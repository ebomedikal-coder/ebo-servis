<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>EBO Medikal - Servis Formu</title>
<style>
* {
margin: 0;
padding: 0;
box-sizing: border-box;
}

body {
font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
min-height: 100vh;
padding: 20px;
}

.container {
max-width: 1000px;
margin: 0 auto;
background: white;
border-radius: 20px;
box-shadow: 0 20px 60px rgba(0,0,0,0.3);
overflow: hidden;
}

.header {
background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
padding: 30px;
text-align: center;
color: white;
}

.header h1 {
color: #ffd700;
font-size: 2em;
margin-bottom: 10px;
}

.form-container {
padding: 30px;
}

.section {
margin-bottom: 30px;
padding: 20px;
background: #f8f9fa;
border-radius: 10px;
border-left: 4px solid #ffd700;
}

.section-title {
font-size: 1.2em;
color: #1a1a2e;
font-weight: 600;
margin-bottom: 15px;
}

.form-row {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
gap: 15px;
margin-bottom: 15px;
}

.form-group {
display: flex;
flex-direction: column;
}

.form-group.full-width {
grid-column: 1 / -1;
}

label {
font-weight: 500;
color: #333;
margin-bottom: 5px;
font-size: 0.9em;
}

input, select, textarea {
padding: 12px;
border: 2px solid #e0e0e0;
border-radius: 8px;
font-size: 1em;
transition: border-color 0.3s;
}

input:focus, select:focus, textarea:focus {
outline: none;
border-color: #667eea;
}

textarea {
resize: vertical;
min-height: 80px;
}

.checkbox-group {
display: flex;
flex-wrap: wrap;
gap: 10px;
}

.checkbox-item {
display: flex;
align-items: center;
gap: 5px;
padding: 8px 12px;
background: white;
border-radius: 6px;
border: 1px solid #ddd;
}

.priority-selector {
display: flex;
gap: 10px;
}

.priority-btn {
flex: 1;
padding: 10px;
border: 2px solid #e0e0e0;
background: white;
border-radius: 8px;
cursor: pointer;
transition: all 0.3s;
}

.priority-btn.active {
background: #ffd700;
border-color: #ffd700;
color: #1a1a2e;
}

.parts-table {
width: 100%;
border-collapse: collapse;
background: white;
border-radius: 8px;
overflow: hidden;
}

.parts-table th, .parts-table td {
padding: 12px;
text-align: left;
border-bottom: 1px solid #e0e0e0;
}

.parts-table th {
background: #1a1a2e;
color: #ffd700;
}

.add-btn {
background: #667eea;
color: white;
border: none;
padding: 10px 20px;
border-radius: 6px;
cursor: pointer;
margin-top: 10px;
}

.actions {
display: flex;
gap: 10px;
justify-content: flex-end;
margin-top: 30px;
padding-top: 20px;
border-top: 2px solid #e0e0e0;
}

.btn {
padding: 12px 30px;
border-radius: 8px;
font-size: 1em;
font-weight: 600;
cursor: pointer;
border: none;
transition: transform 0.2s;
}

.btn:hover {
transform: translateY(-2px);
}

.btn-secondary {
background: #e0e0e0;
color: #333;
}

.btn-primary {
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
color: white;
}

@media print {
body { background: white; }
.container { box-shadow: none; }
.actions { display: none; }
}
</style>
</head>
<body>
<div class="container">
<div class="header">
<h1>🔧 EBO MEDİKAL SERVİS FORMU</h1>
<p>Teknik Servis Yönetim Sistemi</p>
</div>

<div class="form-container">
<!-- Müşteri Bilgileri -->
<div class="section">
<h2 class="section-title">👤 Müşteri Bilgileri</h2>
<div class="form-row">
<div class="form-group">
<label>Firma / Kişi Adı</label>
<input type="text" id="musteriAdi">
</div>
<div class="form-group">
<label>Yetkili Kişi</label>
<input type="text" id="yetkili">
</div>
<div class="form-group">
<label>Telefon</label>
<input type="tel" id="telefon">
</div>
</div>
<div class="form-row">
<div class="form-group">
<label>E-posta</label>
<input type="email" id="email">
</div>
<div class="form-group full-width">
<label>Adres</label>
<input type="text" id="adres">
</div>
</div>
</div>

<!-- Cihaz Bilgileri -->
<div class="section">
<h2 class="section-title">🏥 Cihaz Bilgileri</h2>
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
<div class="form-row">
<div class="form-group">
<label>Kurulum Tarihi</label>
<input type="date" id="kurulumTarihi">
</div>
<div class="form-group">
<label>Son Bakım Tarihi</label>
<input type="date" id="sonBakim">
</div>
<div class="form-group">
<label>Garanti Durumu</label>
<select id="garanti">
<option value="">Seçiniz...</option>
<option>Garantili</option>
<option>Garanti Dışı</option>
<option>Ek Garanti</option>
</select>
</div>
</div>
</div>

<!-- Servis Talebi -->
<div class="section">
<h2 class="section-title">📋 Servis Talebi Detayları</h2>
<div class="form-row">
<div class="form-group">
<label>Arıza Bildirim Tarihi</label>
<input type="date" id="bildirimTarihi">
</div>
<div class="form-group">
<label>Servis Başlangıç</label>
<input type="date" id="baslangicTarihi">
</div>
<div class="form-group">
<label>Tahmini Bitiş</label>
<input type="date" id="bitisTarihi">
</div>
</div>

<div class="form-group full-width" style="margin-top: 15px;">
<label>Öncelik Seviyesi</label>
<div class="priority-selector">
<button type="button" class="priority-btn" onclick="setPriority('low')">Düşük</button>
<button type="button" class="priority-btn active" onclick="setPriority('medium')">Orta</button>
<button type="button" class="priority-btn" onclick="setPriority('high')">Yüksek</button>
</div>
</div>

<div class="form-group full-width" style="margin-top: 15px;">
<label>Bildirilen Arıza / Şikayet</label>
<textarea id="sikayet"></textarea>
</div>
</div>

<!-- Teknik İnceleme -->
<div class="section">
<h2 class="section-title">🔍 Teknik İnceleme</h2>
<div class="form-group full-width">
<label>Yapılan İşlemler</label>
<div class="checkbox-group">
<label class="checkbox-item"><input type="checkbox"> Kalibrasyon</label>
<label class="checkbox-item"><input type="checkbox"> Yazılım Güncellemesi</label>
<label class="checkbox-item"><input type="checkbox"> Parça Değişimi</label>
<label class="checkbox-item"><input type="checkbox"> Temizlik / Bakım</label>
<label class="checkbox-item"><input type="checkbox"> Arıza Tespiti</label>
<label class="checkbox-item"><input type="checkbox"> Test ve Kontrol</label>
</div>
</div>

<div class="form-group full-width" style="margin-top: 15px;">
<label>Tespit Edilen Arıza</label>
<textarea id="tespit"></textarea>
</div>

<div class="form-group full-width" style="margin-top: 15px;">
<label>Uygulanan Çözüm</label>
<textarea id="cozum"></textarea>
</div>
</div>

<!-- Parçalar -->
<div class="section">
<h2 class="section-title">🔩 Kullanılan Parçalar</h2>
<table class="parts-table">
<thead>
<tr>
<th>Parça Kodu</th>
<th>Parça Adı</th>
<th>Miktar</th>
<th>Birim Fiyat</th>
<th>İşlem</th>
</tr>
</thead>
<tbody id="parcaListesi">
<tr>
<td><input type="text" style="width: 100%; border: none;"></td>
<td><input type="text" style="width: 100%; border: none;"></td>
<td><input type="number" style="width: 60px; border: none;"></td>
<td><input type="text" style="width: 100%; border: none;"></td>
<td><button onclick="silSatir(this)" style="background: #dc3545; color: white; border: none; padding: 5px 10px; border-radius: 4px; cursor: pointer;">Sil</button></td>
</tr>
</tbody>
</table>
<button class="add-btn" onclick="yeniSatir()">+ Yeni Parça Ekle</button>
</div>

<!-- Servis Sonucu -->
<div class="section">
<h2 class="section-title">✅ Servis Sonucu</h2>
<div class="form-row">
<div class="form-group">
<label>Servis Durumu</label>
<select id="durum">
<option value="">Seçiniz...</option>
<option>Beklemede</option>
<option>Devam Ediyor</option>
<option>Parça Bekleniyor</option>
<option>Tamamlandı</option>
</select>
</div>
<div class="form-group">
<label>Çalışma Süresi (Saat)</label>
<input type="number" step="0.5" id="sure">
</div>
<div class="form-group">
<label>Garanti Kapsamı</label>
<select id="garantiKapsam">
<option value="">Seçiniz...</option>
<option>Evet</option>
<option>Hayır</option>
<option>Kısmi</option>
</select>
</div>
</div>

<div class="form-group full-width" style="margin-top: 15px;">
<label>Notlar ve Öneriler</label>
<textarea id="notlar"></textarea>
</div>
</div>

<!-- Onay -->
<div class="section">
<h2 class="section-title">📝 Onay</h2>
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
<button class="btn btn-secondary" onclick="formTemizle()">Temizle</button>
<button class="btn btn-primary" onclick="formYazdir()">Yazdır / Kaydet</button>
</div>
</div>
</div>

<script>
function setPriority(level) {
document.querySelectorAll('.priority-btn').forEach(btn => btn.classList.remove('active'));
event.target.classList.add('active');
}

function yeniSatir() {
const tbody = document.getElementById('parcaListesi');
const row = document.createElement('tr');
row.innerHTML = `
<td><input type="text" style="width: 100%; border: none;"></td>
<td><input type="text" style="width: 100%; border: none;"></td>
<td><input type="number" style="width: 60px; border: none;"></td>
<td><input type="text" style="width: 100%; border: none;"></td>
<td><button onclick="silSatir(this)" style="background: #dc3545; color: white; border: none; padding: 5px 10px; border-radius: 4px; cursor: pointer;">Sil</button></td>
`;
tbody.appendChild(row);
}

function silSatir(btn) {
btn.closest('tr').remove();
}

function formTemizle() {
if(confirm('Formdaki tüm bilgiler silinecek. Emin misiniz?')) {
document.querySelectorAll('input, textarea').forEach(el => el.value = '');
document.querySelectorAll('select').forEach(el => el.selectedIndex = 0);
document.querySelectorAll('input[type="checkbox"]').forEach(el => el.checked = false);
}
}

function formYazdir() {
window.print();
}

// Bugünün tarihini varsayılan olarak ayarla
document.getElementById('bildirimTarihi').valueAsDate = new Date();
</script>
</body>
</html>
