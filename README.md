<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>EBO Medikal - Servis Formu</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
<style>
* {
margin: 0;
padding: 0;
box-sizing: border-box;
-webkit-tap-highlight-color: transparent;
}

body {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
background: #f5f7fa;
min-height: 100vh;
padding: 10px;
}

.container {
max-width: 800px;
margin: 0 auto;
background: white;
border-radius: 16px;
box-shadow: 0 4px 20px rgba(0,0,0,0.08);
overflow: hidden;
}

.header {
background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
padding: 20px;
text-align: center;
}

.logo {
max-width: 180px;
height: auto;
margin-bottom: 10px;
}

.header h1 {
color: #ffd700;
font-size: 1.3em;
font-weight: 700;
}

.qr-section {
background: white;
padding: 15px;
text-align: center;
border-bottom: 2px solid #e1e4e8;
}

.qr-container {
display: inline-block;
padding: 10px;
background: white;
border-radius: 10px;
border: 2px solid #ffd700;
}

.qr-id {
margin-top: 8px;
font-family: monospace;
font-size: 0.9em;
color: #666;
font-weight: 600;
}

.form-container {
padding: 20px;
}

.section {
margin-bottom: 20px;
padding: 15px;
background: #fafbfc;
border-radius: 12px;
border-left: 4px solid #ffd700;
}

.section-title {
font-size: 0.95em;
color: #1a1a2e;
font-weight: 600;
margin-bottom: 12px;
display: flex;
align-items: center;
gap: 8px;
}

.form-row {
display: flex;
flex-direction: column;
gap: 10px;
}

.form-group {
display: flex;
flex-direction: column;
}

label {
font-weight: 500;
color: #444;
margin-bottom: 5px;
font-size: 0.85em;
}

input, select, textarea {
padding: 10px 12px;
border: 1.5px solid #e1e4e8;
border-radius: 8px;
font-size: 16px;
width: 100%;
}

input:focus, select:focus, textarea:focus {
outline: none;
border-color: #ffd700;
}

textarea {
resize: vertical;
min-height: 60px;
}

.checkbox-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 8px;
}

.checkbox-item {
display: flex;
align-items: center;
gap: 6px;
padding: 8px;
background: white;
border-radius: 6px;
border: 1px solid #e1e4e8;
font-size: 0.85em;
}

.priority-selector {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 8px;
}

.priority-btn {
padding: 10px;
border: 2px solid #e1e4e8;
background: white;
border-radius: 8px;
cursor: pointer;
font-weight: 500;
font-size: 0.85em;
}

.priority-btn.active {
background: #ffd700;
border-color: #ffd700;
color: #1a1a2e;
}

.parts-card {
background: white;
border-radius: 8px;
border: 1.5px solid #e1e4e8;
padding: 12px;
margin-bottom: 8px;
}

.parts-row {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 8px;
margin-bottom: 8px;
}

.btn-icon {
padding: 8px;
border: none;
border-radius: 6px;
cursor: pointer;
font-size: 0.8em;
font-weight: 500;
width: 100%;
}

.btn-add {
background: #ffd700;
color: #1a1a2e;
}

.btn-remove {
background: #fee;
color: #dc3545;
border: 1px solid #fcc;
margin-top: 5px;
}

.actions {
display: flex;
flex-direction: column;
gap: 10px;
margin-top: 20px;
padding-top: 15px;
border-top: 2px solid #e1e4e8;
}

.btn {
padding: 14px;
border-radius: 10px;
font-size: 1em;
font-weight: 600;
cursor: pointer;
border: none;
width: 100%;
}

.btn-secondary {
background: #e9ecef;
color: #495057;
}

.btn-primary {
background: linear-gradient(135deg, #ffd700 0%, #ffed4e 100%);
color: #1a1a2e;
}

.btn-success {
background: #28a745;
color: white;
}

.data-display {
background: #f8f9fa;
border: 1px solid #dee2e6;
border-radius: 8px;
padding: 15px;
margin-top: 10px;
display: none;
}

.data-display.active {
display: block;
}

@media (min-width: 768px) {
body { padding: 20px; }
.form-row { display: grid; grid-template-columns: repeat(3, 1fr); }
.form-row.two-col { grid-template-columns: repeat(2, 1fr); }
.checkbox-grid { grid-template-columns: repeat(3, 1fr); }
.actions { flex-direction: row; }
.btn { width: auto; padding: 14px 30px; }
}
</style>
</head>
<body>
<div class="container">
<div class="header">
<h1>EBO MEDİKAL SERVİS FORMU</h1>
</div>

<!-- QR Kod Bölümü -->
<div class="qr-section">
<div class="qr-container">
<div id="qrcode"></div>
<div class="qr-id" id="musteriId">ID: Yükleniyor...</div>
</div>
<p style="font-size: 0.8em; color: #666; margin-top: 8px;">
Bu QR kodu tarayarak müşteri bilgilerine ulaşın
</p>
</div>

<div class="form-container">
<!-- Müşteri Bilgileri -->
<div class="section">
<h2 class="section-title">Müşteri Bilgileri</h2>
<div class="form-row two-col">
<div class="form-group">
<label>Firma / Kişi Adı *</label>
<input type="text" id="musteriAdi" onchange="generateQR()">
</div>
<div class="form-group">
<label>Yetkili Kişi</label>
<input type="text" id="yetkili">
</div>
</div>
<div class="form-row">
<div class="form-group">
<label>Telefon *</label>
<input type="tel" id="telefon" onchange="generateQR()">
</div>
<div class="form-group">
<label>E-posta</label>
<input type="email" id="email">
</div>
<div class="form-group">
<label>Adres</label>
<input type="text" id="adres">
</div>
</div>
</div>

<!-- Cihaz Bilgileri -->
<div class="section">
<h2 class="section-title">Cihaz Bilgileri</h2>
<div class="form-row">
<div class="form-group">
<label>Cihaz Türü</label>
<select id="cihazTuru">
<option value="">Seçiniz...</option>
<option>MR Cihazı</option>
<option>CT Tomografi</option>
<option>Ultrason</option>
<option>Röntgen</option>
<option>Mamografi</option>
<option>Angiografi</option>
<option>Laboratuvar Cihazı</option>
<option>Diğer</option>
</select>
</div>
<div class="form-group">
<label>Marka / Model</label>
<input type="text" id="markaModel">
</div>
<div class="form-group">
<label>Seri No</label>
<input type="text" id="seriNo">
</div>
</div>
</div>

<!-- Servis Talebi -->
<div class="section">
<h2 class="section-title">Servis Talebi</h2>
<div class="form-row">
<div class="form-group">
<label>Bildirim Tarihi</label>
<input type="date" id="bildirimTarihi">
</div>
<div class="form-group">
<label>Öncelik</label>
<div class="priority-selector">
<button type="button" class="priority-btn" onclick="setPriority(this)">Düşük</button>
<button type="button" class="priority-btn active" onclick="setPriority(this)">Orta</button>
<button type="button" class="priority-btn" onclick="setPriority(this)">Yüksek</button>
</div>
</div>
<div class="form-group">
<label>Durum</label>
<select id="durum">
<option>Beklemede</option>
<option>Devam Ediyor</option>
<option>Tamamlandı</option>
</select>
</div>
</div>

<div class="form-group" style="margin-top: 10px;">
<label>Arıza / Şikayet</label>
<textarea id="sikayet"></textarea>
</div>
</div>

<!-- Teknik İnceleme -->
<div class="section">
<h2 class="section-title">Teknik İnceleme</h2>
<div class="checkbox-grid">
<label class="checkbox-item"><input type="checkbox"> Kalibrasyon</label>
<label class="checkbox-item"><input type="checkbox"> Yazılım</label>
<label class="checkbox-item"><input type="checkbox"> Parça Değişimi</label>
<label class="checkbox-item"><input type="checkbox"> Bakım</label>
<label class="checkbox-item"><input type="checkbox"> Arıza Tespiti</label>
<label class="checkbox-item"><input type="checkbox"> Test</label>
</div>

<div class="form-group" style="margin-top: 10px;">
<label>Tespit Edilen Arıza</label>
<textarea id="tespit"></textarea>
</div>

<div class="form-group" style="margin-top: 10px;">
<label>Uygulanan Çözüm</label>
<textarea id="cozum"></textarea>
</div>
</div>

<!-- Parçalar -->
<div class="section">
<h2 class="section-title">Kullanılan Parçalar</h2>
<div id="parcaListesi">
<div class="parts-card">
<div class="parts-row">
<input type="text" placeholder="Parça Kodu">
<input type="text" placeholder="Parça Adı">
</div>
<div class="parts-row">
<input type="number" placeholder="Miktar">
<input type="text" placeholder="Birim Fiyat">
</div>
</div>
</div>
<button type="button" class="btn-icon btn-add" onclick="yeniParca()">+ Parça Ekle</button>
</div>

<!-- Onay -->
<div class="section">
<h2 class="section-title">Onay</h2>
<div class="form-row">
<div class="form-group">
<label>Teknisyen</label>
<input type="text" id="teknisyen">
</div>
<div class="form-group">
<label>Onaylayan</label>
<input type="text" id="onaylayan">
</div>
<div class="form-group">
<label>Tarih</label>
<input type="date" id="onayTarihi">
</div>
</div>
</div>

<div class="actions">
<button type="button" class="btn btn-secondary" onclick="formTemizle()">Yeni Form</button>
<button type="button" class="btn btn-success" onclick="kaydetVeIndir()">Kaydet & İndir</button>
<button type="button" class="btn btn-primary" onclick="formYazdir()">Yazdır</button>
</div>

<!-- Veri Görüntüleme Alanı (QR tarama sonrası) -->
<div id="dataDisplay" class="data-display">
<h3>Müşteri Bilgileri</h3>
<div id="displayContent"></div>
</div>
</div>
</div>

<script>
// Sayfa yüklendiğinde
window.onload = function() {
document.getElementById('bildirimTarihi').valueAsDate = new Date();
generateQR();
};

// Benzersiz ID oluştur
function generateId() {
const musteri = document.getElementById('musteriAdi').value || 'MUSTERI';
const tel = document.getElementById('telefon').value || '0000';
const tarih = new Date().toISOString().slice(0,10).replace(/-/g,'');
const random = Math.floor(Math.random() * 1000).toString().padStart(3, '0');
return `EBO-${musteri.substring(0,3).toUpperCase()}-${tel.slice(-4)}-${tarih}-${random}`;
}

// QR Kod oluştur
function generateQR() {
const id = generateId();
document.getElementById('musteriId').textContent = `ID: ${id}`;

// QR kodu temizle ve yeniden oluştur
const qrContainer = document.getElementById('qrcode');
qrContainer.innerHTML = '';

// Form verilerini JSON olarak hazırla
const formData = {
id: id,
musteri: document.getElementById('musteriAdi').value,
telefon: document.getElementById('telefon').value,
email: document.getElementById('email').value,
adres: document.getElementById('adres').value,
cihaz: document.getElementById('cihazTuru').value,
marka: document.getElementById('markaModel').value,
seriNo: document.getElementById('seriNo').value,
tarih: document.getElementById('bildirimTarihi').value,
sikayet: document.getElementById('sikayet').value,
tespit: document.getElementById('tespit').value,
cozum: document.getElementById('cozum').value,
durum: document.getElementById('durum').value
};

// QR kodu oluştur (base64 veri)
const qrData = btoa(JSON.stringify(formData));

new QRCode(qrContainer, {
text: qrData,
width: 128,
height: 128,
colorDark : "#1a1a2e",
colorLight : "#ffffff",
correctLevel : QRCode.CorrectLevel.M
});
}

function setPriority(btn) {
document.querySelectorAll('.priority-btn').forEach(b => b.classList.remove('active'));
btn.classList.add('active');
}

function yeniParca() {
const container = document.getElementById('parcaListesi');
const card = document.createElement('div');
card.className = 'parts-card';
card.innerHTML =
'<div class="parts-row">' +
'<input type="text" placeholder="Parça Kodu">' +
'<input type="text" placeholder="Parça Adı">' +
'</div>' +
'<div class="parts-row">' +
'<input type="number" placeholder="Miktar">' +
'<input type="text" placeholder="Birim Fiyat">' +
'</div>' +
'<button type="button" class="btn-icon btn-remove" onclick="this.parentElement.remove()">Sil</button>';
container.appendChild(card);
}

function formTemizle() {
if(confirm('Yeni form başlatılacak. Emin misiniz?')) {
document.querySelectorAll('input, textarea').forEach(el => el.value = '');
document.querySelectorAll('select').forEach(el => el.selectedIndex = 0);
document.querySelectorAll('input[type="checkbox"]').forEach(el => el.checked = false);
document.getElementById('bildirimTarihi').valueAsDate = new Date();
generateQR();
}
}

function kaydetVeIndir() {
generateQR();
const formData = {
id: document.getElementById('musteriId').textContent,
musteri: document.getElementById('musteriAdi').value,
tarih: new Date().toLocaleString('tr-TR')
};

// LocalStorage'a kaydet
let kayitlar = JSON.parse(localStorage.getItem('eboServis') || '[]');
kayitlar.push(formData);
localStorage.setItem('eboServis', JSON.stringify(kayitlar));

alert('Form kaydedildi! ID: ' + formData.id);
}

function formYazdir() {
window.print();
}

// QR kod okuma simülasyonu (gerçek uygulamada kamera ile okunur)
function readQR(qrData) {
try {
const data = JSON.parse(atob(qrData));
const display = document.getElementById('dataDisplay');
const content = document.getElementById('displayContent');

content.innerHTML = `
<p><strong>ID:</strong> ${data.id}</p>
<p><strong>Müşteri:</strong> ${data.musteri}</p>
<p><strong>Telefon:</strong> ${data.telefon}</p>
<p><strong>Cihaz:</strong> ${data.cihaz} - ${data.marka}</p>
<p><strong>Seri No:</strong> ${data.seriNo}</p>
<p><strong>Durum:</strong> ${data.durum}</p>
`;
display.classList.add('active');
} catch(e) {
alert('Geçersiz QR kod!');
}
}
</script>
</body>
</html>
