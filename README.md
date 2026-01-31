<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>EBO Servis - Admin Panel</title>
<script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-auth-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-database-compat.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
<style>
* { margin: 0; padding: 0; box-sizing: border-box; }
body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background: #f5f6fa; }
.header {
background: #2c3e50; color: white; padding: 15px 30px;
display: flex; justify-content: space-between; align-items: center;
box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}
.header h1 { font-size: 20px; }
.user-info { display: flex; align-items: center; gap: 15px; }
.btn {
padding: 8px 16px; border: none; border-radius: 4px;
cursor: pointer; font-size: 14px; transition: all 0.3s;
}
.btn-primary { background: #3498db; color: white; }
.btn-danger { background: #e74c3c; color: white; }
.btn-success { background: #27ae60; color: white; }
.btn:hover { opacity: 0.9; transform: translateY(-1px); }
.container { max-width: 1400px; margin: 30px auto; padding: 0 20px; }
.stats-grid {
display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
gap: 20px; margin-bottom: 30px;
}
.stat-card {
background: white; padding: 20px; border-radius: 8px;
box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}
.stat-card h3 { color: #7f8c8d; font-size: 14px; margin-bottom: 10px; }
.stat-card .number { font-size: 32px; font-weight: bold; color: #2c3e50; }
.filters {
background: white; padding: 20px; border-radius: 8px;
margin-bottom: 20px; box-shadow: 0 2px 5px rgba(0,0,0,0.1);
display: flex; gap: 15px; flex-wrap: wrap; align-items: center;
}
.filters input, .filters select {
padding: 8px 12px; border: 1px solid #ddd; border-radius: 4px; font-size: 14px;
}
.table-container {
background: white; border-radius: 8px;
box-shadow: 0 2px 5px rgba(0,0,0,0.1); overflow: hidden;
}
table { width: 100%; border-collapse: collapse; }
th, td { padding: 12px; text-align: left; border-bottom: 1px solid #ecf0f1; }
th { background: #34495e; color: white; font-weight: 600; font-size: 13px; }
tr:hover { background: #f8f9fa; }
.status {
padding: 4px 8px; border-radius: 12px; font-size: 12px; font-weight: 600;
}
.status-bekliyor { background: #fff3cd; color: #856404; }
.status-işlemde { background: #cce5ff; color: #004085; }
.status-tamamlandı { background: #d4edda; color: #155724; }
.actions { display: flex; gap: 5px; }
.actions button { padding: 5px 10px; font-size: 12px; border: none; border-radius: 3px; cursor: pointer; }
.btn-view { background: #3498db; color: white; }
.btn-edit { background: #f39c12; color: white; }
.btn-qr { background: #9b59b6; color: white; }
.modal {
display: none; position: fixed; top: 0; left: 0;
width: 100%; height: 100%; background: rgba(0,0,0,0.5);
z-index: 1000; align-items: center; justify-content: center;
}
.modal.active { display: flex; }
.modal-content {
background: white; padding: 30px; border-radius: 8px;
max-width: 500px; width: 90%; text-align: center;
}
#qrcode { margin: 20px auto; }
@media (max-width: 768px) {
.header { flex-direction: column; gap: 10px; text-align: center; }
table { font-size: 12px; }
th, td { padding: 8px; }
}
</style>
</head>
<body>
<div class="header">
<h1>🔧 EBO Servis Yönetim Paneli</h1>
<div class="user-info">
<span id="userEmail"></span>
<button class="btn btn-primary" onclick="window.location.href='form.html'">+ Yeni Form</button>
<button class="btn btn-danger" onclick="logout()">Çıkış</button>
</div>
</div>

<div class="container">
<div class="stats-grid">
<div class="stat-card"><h3>Toplam Kayıt</h3><div class="number" id="totalForms">0</div></div>
<div class="stat-card"><h3>Bu Ay</h3><div class="number" id="monthForms">0</div></div>
<div class="stat-card"><h3>Bekleyen</h3><div class="number" id="pendingForms">0</div></div>
<div class="stat-card"><h3>Tamamlanan</h3><div class="number" id="completedForms">0</div></div>
</div>

<div class="filters">
<input type="text" id="searchInput" placeholder="Ara (Müşteri, Cihaz...)" onkeyup="filterForms()">
<input type="date" id="startDate" onchange="filterForms()">
<input type="date" id="endDate" onchange="filterForms()">
<select id="statusFilter" onchange="filterForms()">
<option value="">Tüm Durumlar</option>
<option value="Bekliyor">Bekliyor</option>
<option value="İşlemde">İşlemde</option>
<option value="Tamamlandı">Tamamlandı</option>
</select>
</div>

<div class="table-container">
<table>
<thead>
<tr>
<th>Form No</th><th>Tarih</th><th>Müşteri</th><th>Cihaz</th>
<th>Seri No</th><th>Durum</th><th>Tutar</th><th>İşlemler</th>
</tr>
</thead>
<tbody id="formsTable"></tbody>
</table>
</div>
</div>

<div id="qrModal" class="modal">
<div class="modal-content">
<h3>Form QR Kodu</h3>
<div id="qrcode"></div>
<p id="qrFormNo"></p>
<button class="btn btn-primary" onclick="closeModal()">Kapat</button>
</div>
</div>

<script src="js/firebase-config.js"></script>
<script>
auth.onAuthStateChanged(user => {
if (!user) window.location.href = 'index.html';
else {
document.getElementById('userEmail').textContent = user.email;
loadForms();
}
});

function logout() { auth.signOut().then(() => window.location.href = 'index.html'); }

let allForms = [];

function loadForms() {
database.ref('forms').orderByChild('createdAt').on('value', snapshot => {
allForms = [];
snapshot.forEach(child => allForms.push({id: child.key, ...child.val()}));
allForms.reverse();
displayForms(allForms);
updateStats(allForms);
});
}

function displayForms(forms) {
const tbody = document.getElementById('formsTable');
tbody.innerHTML = '';
forms.forEach(form => {
const date = form.createdAt ? new Date(form.createdAt).toLocaleDateString('tr-TR') : '-';
const statusClass = 'status-' + (form.status || 'Bekliyor').toLowerCase().replace(' ', '');
tbody.innerHTML += `
<tr>
<td>${form.formNo || '-'}</td>
<td>${date}</td>
<td>${form.customer?.name || '-'}</td>
<td>${form.device?.brand || '-'} ${form.device?.model || ''}</td>
<td>${form.device?.serialNo || '-'}</td>
<td><span class="status ${statusClass}">${form.status || 'Bekliyor'}</span></td>
<td>${form.total ? form.total.toLocaleString('tr-TR', {minimumFractionDigits: 2}) + ' TL' : '0,00 TL'}</td>
<td class="actions">
<button class="btn-view" onclick="viewForm('${form.id}')">Gör</button>
<button class="btn-edit" onclick="editForm('${form.id}')">Düzenle</button>
<button class="btn-qr" onclick="showQR('${form.id}', '${form.formNo}')">QR</button>
</td>
</tr>`;
});
}

function updateStats(forms) {
document.getElementById('totalForms').textContent = forms.length;
const monthStart = new Date(new Date().getFullYear(), new Date().getMonth(), 1);
document.getElementById('monthForms').textContent = forms.filter(f => f.createdAt && new Date(f.createdAt) >= monthStart).length;
document.getElementById('pendingForms').textContent = forms.filter(f => !f.status || f.status === 'Bekliyor').length;
document.getElementById('completedForms').textContent = forms.filter(f => f.status === 'Tamamlandı').length;
}

function filterForms() {
const search = document.getElementById('searchInput').value.toLowerCase();
const start = document.getElementById('startDate').value;
const end = document.getElementById('endDate').value;
const status = document.getElementById('statusFilter').value;

let filtered = allForms.filter(form => {
const matchSearch = !search ||
(form.customer?.name || '').toLowerCase().includes(search) ||
(form.device?.serialNo || '').toLowerCase().includes(search) ||
(form.formNo || '').toLowerCase().includes(search);
let matchDate = true;
if (start) matchDate = matchDate && new Date(form.createdAt) >= new Date(start);
if (end) matchDate = matchDate && new Date(form.createdAt) <= new Date(end + 'T23:59:59');
const matchStatus = !status || form.status === status;
return matchSearch && matchDate && matchStatus;
});
displayForms(filtered);
}

function viewForm(id) { window.open(`view-form.html?id=${id}`, '_blank'); }
function editForm(id) { window.location.href = `form.html?id=${id}`; }

function showQR(id, formNo) {
document.getElementById('qrcode').innerHTML = '';
const url = `${window.location.origin}/view-form.html?id=${id}`;
new QRCode(document.getElementById('qrcode'), {text: url, width: 200, height: 200});
document.getElementById('qrFormNo').textContent = `Form No: ${formNo}`;
document.getElementById('qrModal').classList.add('active');
}

function closeModal() { document.getElementById('qrModal').classList.remove('active'); }
window.onclick = e => { if (e.target === document.getElementById('qrModal')) closeModal(); }
</script>
</body>
</html>
