<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>EBO Medikal - Servis Formu</title>
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
position: relative;
}

.logo {
width: 140px;
height: auto;
margin-bottom: 15px;
filter: drop-shadow(0 2px 4px rgba(0,0,0,0.3));
}

.header h1 {
color: #ffd700;
font-size: 1.4em;
font-weight: 700;
margin-bottom: 5px;
}

.header p {
color: #a0a0a0;
font-size: 0.85em;
}

.form-container {
padding: 20px;
}

.section {
margin-bottom: 25px;
padding: 20px;
background: #fafbfc;
border-radius: 12px;
border-left: 4px solid #ffd700;
}

.section-title {
font-size: 1em;
color: #1a1a2e;
font-weight: 600;
margin-bottom: 15px;
display: flex;
align-items: center;
gap: 8px;
}

.section-title::before {
content: '';
width: 6px;
height: 6px;
background: #ffd700;
border-radius: 50%;
}

.form-row {
display: flex;
flex-direction: column;
gap: 12px;
}

.form-group {
display: flex;
flex-direction: column;
}

label {
font-weight: 500;
color: #444;
margin-bottom: 6px;
font-size: 0.85em;
}

input, select, textarea {
padding: 12px 14px;
border: 1.5px solid #e1e4e8;
border-radius: 10px;
font-size: 16px; /* iOS zoom önleme */
transition: all 0.2s;
background: white;
width: 100%;
}

input:focus, select:focus, textarea:focus {
outline: none;
border-color: #ffd700;
box-shadow: 0 0 0 3px rgba(255, 215, 0, 0.1);
}

textarea {
resize: vertical;
min-height: 80px;
}

.checkbox-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 8px;
}

.checkbox-item {
display: flex;
align-items: center;
gap: 8px;
padding: 10px;
background: white;
border-radius: 8px;
border: 1.5px solid #e1e4e8;
font-size: 0.85em;
cursor: pointer;
}

.checkbox-item:active {
transform: scale(0.98);
}

input[type="checkbox"] {
width: 18px;
height: 18px;
accent-color: #ffd700;
}

.priority-selector {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 10px;
}

.priority-btn {
padding: 12px;
border: 2px solid #e1e4e8;
background: white;
border-radius: 10px;
cursor: pointer;
transition: all 0.2s;
font-weight: 500;
font-size: 0.9em;
}

.priority-btn.low { color: #28a745; }
.priority-btn.medium { color: #ff9800; }
.priority-btn.high { color: #dc3545; }

.priority-btn.active {
transform: scale(1.05);
font-weight: 600;
}

.priority-btn.low.active { background: #d4edda; border-color: #28a745; }
.priority-btn.medium.active { background: #fff3cd; border-color: #ff9800; }
.priority-btn.high.active { background: #f8d7da; border-color: #dc3545; }

.parts-card {
background: white;
border-radius: 10px;
border: 1.5px solid #e1e4e8;
padding: 15px;
margin-bottom: 10px;
}

.parts-row {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 10px;
margin-bottom: 10px;
}

.parts-row input {
padding: 10px;
font-size: 0.9em;
}

.parts-actions {
display: flex;
gap: 8px;
margin-top: 10px;
}

.btn-icon {
flex: 1;
padding: 10px;
border: none;
border-radius: 8px;
cursor: pointer;
font-size: 0.85em;
font-weight: 500;
transition: all 0.2s;
}

.btn-add {
background: #ffd700;
color: #1a1a2e;
}

.btn-remove {
background: #fee;
color: #dc3545;
}

.btn-icon:active {
transform: scale(0.95);
}

.actions {
display: flex;
flex-direction: column;
gap: 10px;
margin-top: 30px;
padding-top: 20px;
border-top: 2px solid #e1e4e8;
}

.btn {
padding: 16px;
border-radius: 12px;
font-size: 1em;
font-weight: 600;
cursor: pointer;
border: none;
transition: all 0.2s;
width: 100%;
}

.btn:active {
transform: scale(0.98);
}

.btn-secondary {
background: #e9ecef;
color: #495057;
}

.btn-primary {
background: linear-gradient(135deg, #ffd700 0%, #ffed4e 100%);
color: #1a1a2e;
box-shadow: 0 4px 15px rgba(255, 215, 0, 0.3);
}

/* Tablet ve Desktop */
@media (min-width: 768px) {
body {
padding: 20px;
}

.header {
padding: 30px;
}

.logo {
width: 180px;
}

.header h1 {
font-size: 1.8em;
}

.form-container {
padding: 30px;
}

.form-row {
display: grid;
grid-template-columns: repeat(3, 1fr);
}

.form-row.two-col {
grid-template-columns: repeat(2, 1fr);
}

.checkbox-grid {
grid-template-columns: repeat(3, 1fr);
}

.actions {
flex-direction: row;
justify-content: flex-end;
}

.btn {
width: auto;
padding: 16px 40px;
}
}

@media print {
body { background: white; padding: 0; }
.container { box-shadow: none; border-radius: 0; }
.actions { display: none; }
.btn-remove, .btn-add { display: none; }
}
</style>
</head>
<body>
<div class="container">
<div class="header">
<!-- Logo PNG olarak eklenecek -->
<img src="logo.png" alt="EBO Medikal" class="logo" onerror="this.style.display='none'">
<h1>SERVİS FORMU</h1>
<p>Teknik Servis Yönetim Sistemi</p>
</div>

<div class="form-container">
<!-- Müşteri Bilgileri -->
<div class="section">
<h2 class="section-title">Müşteri Bilgileri</h2>
<div class="form-row two-col">
<div class="form-group">
<label>Firma / Kişi Adı</label>
<input type="text" id="musteriAdi" placeholder="">
</div>
<div class="form-group">
<label>Yetkili Kişi</label>
<input type="text" id="yetkili" placeholder="">
</div>
</div>
<div class="form-row">
<div class="form-group">
<label>Telefon</label>
<input type="tel" id="telefon" placeholder="">
</div>
<div class="form-group">
<label>E-posta</label>
<input type="email" id="email" placeholder="">
</div>
<div class="form-group">
<label>Adres</label>
<input type="text" id="adres" placeholder="">
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
<input type="text" id="markaModel" placeholder="">
</div>
<div class="form-group">
<label>Seri No</label>
<input type="text" scale(0.98);
}

input[type="checkbox"] {
width: 18px;
height: 18px;
accent-color: #ffd700;
}

.priority-selector {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 10px;
}

.priority-btn {
padding: 12px;
border: 2px solid #e1e4e8;
background: white;
border-radius: 10px;
cursor: pointer;
transition: all 0.2s;
font-weight: 500;
font-size: 0.9em;
}

.priority-btn.low { color: #28a745; }
.priority-btn.medium { color: #ff9800; }
.priority-btn.high { color: #dc3545; }

.priority-btn.active {
transform: scale(1.05);
font-weight: 600;
}

.priority-btn.low.active { background: #d4edda; border-color: #28a745; }
.priority-btn.medium.active { background: #fff3cd; border-color: #ff9800; }
.priority-btn.high.active { background: #f8d7da; border-color: #dc3545; }

.parts-card {
background: white;
border-radius: 10px;
border: 1.5px solid #e1e4e8;
padding: 15px;
margin-bottom: 10px;
}

.parts-row {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 10px;
margin-bottom: 10px;
}

.parts-row input {
padding: 10px;
font-size: 0.9em;
}

.parts-actions {
display: flex;
gap: 8px;
margin-top: 10px;
}

.btn-icon {
flex: 1;
padding: 10px;
border: none;
border-radius: 8px;
cursor: pointer;
font-size: 0.85em;
font-weight: 500;
transition: all 0.2s;
}

.btn-add {
background: #ffd700;
color: #1a1a2e;
}

.btn-remove {
background: #fee;
color: #dc3545;
}

.btn-icon:active {
transform: scale(0.95);
}

.actions {
display: flex;
flex-direction: column;
gap: 10px;
margin-top: 30px;
padding-top: 20px;
border-top: 2px solid #e1e4e8;
}

.btn {
padding: 16px;
border-radius: 12px;
font-size: 1em;
font-weight: 600;
cursor: pointer;
border: none;
transition: all 0.2s;
width: 100%;
}

.btn:active {
transform: scale(0.98);
}

.btn-secondary {
background: #e9ecef;
color: #495057;
}

.btn-primary {
background: linear-gradient(135deg, #ffd700 0%, #ffed4e 100%);
color: #1a1a2e;
box-shadow: 0 4px 15px rgba(255, 215, 0, 0.3);
}

/* Tablet ve Desktop */
@media (min-width: 768px) {
body {
padding: 20px;
}

.header {
padding: 30px;
}

.logo {
width: 180px;
}

.header h1 {
font-size: 1.8em;
}

.form-container {
padding: 30px;
}

.form-row {
display: grid;
grid-template-columns: repeat(3, 1fr);
}

.form-row.two-col {
grid-template-columns: repeat(2, 1fr);
}

.checkbox-grid {
grid-template-columns: repeat(3, 1fr);
}

.actions {
flex-direction: row;
justify-content: flex-end;
}

.btn {
width: auto;
padding: 16px 40px;
}
}

@media print {
body { background: white; padding: 0; }
.container { box-shadow: none; border-radius: 0; }
.actions { display: none; }
.btn-remove, .btn-add { display: none; }
}
</style>
</head>
<body>
<div class="container">
<div class="header">
<!-- Logo PNG olarak eklenecek -->
<img src="logo.png" alt="EBO Medikal" class="logo" onerror="this.style.display='none'">
<h1>SERVİS FORMU</h1>
<p>Teknik Servis Yönetim Sistemi</p>
</div>

<div class="form-container">
<!-- Müşteri Bilgileri -->
<div class="section">
<h2 class="section-title">Müşteri Bilgileri</h2>
<div class="form-row two-col">
<div class="form-group">
<label>Firma / Kişi Adı</label>
<input type="text" id="musteriAdi" placeholder="">
</div>
<div class="form-group">
<label>Yetkili Kişi</label>
<input type="text" id="yetkili" placeholder="">
</div>
</div>
<div class="form-row">
<div class="form-group">
<label>Telefon</label>
<input type="tel" id="telefon" placeholder="">
</div>
<div class="form-group">
<label>E-posta</label>
<input type="email" id="email" placeholder="">
</div>
<div class="form-group">
<label>Adres</label>
<input type="text" id="adres" placeholder="">
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
<input type="text" id="markaModel" placeholder="">
</div>
<div class="form-group">
<label>Seri No</label>
<input type="text" id="seriNo" placeholder="">
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
<label>Başlangıç</label>
<input type="date" id="baslangicTarihi">
</div>
<div class="form-group">
<label>Tahmini Bitiş</label>
<input type="date" id="bitisTarihi">
</div>
</div>

<div class="form-group" style="margin-top: 15px;">
<label>Öncelik</label>
<div class="priority-selector">
<button type="button" class="priority-btn low" onclick="setPriority(this, 'low')">Düşük</button>
<button type="button" class="priority-btn medium active" onclick="setPriority(this, 'medium')">Orta</button>
<button type="button" class="priority-btn high" onclick="setPriority(this, 'high')">Yüksek</button>
</div>
</div>

<div class="form-group" style="margin-top: 15px;">
<label>Bildirilen Arıza</label>
<textarea id="sikayet" placeholder=""></textarea>
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

<div class="form-group" style="margin-top: 15px;">
<label>Tespit Edilen Arıza</label>
<textarea id="tespit" placeholder=""></textarea>
</div>

<div class="form-group" style="margin-top: 10px;">
<label>Uygulanan Çözüm</label>
<textarea id="cozum" placeholder=""></textarea>
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
<button class="btn-icon btn-add" onclick="yeniParca()">+ Parça Ekle</button>
</div>

<!-- Servis Sonucu -->
<div class="section">
<h2 class="section-title">Servis Sonucu</h2>
<div class="form-row">
<div class="form-group">
<label>Durum</label>
<select id="durum">
<option value="">Seçiniz...</option>
<option>Beklemede</option>
<option>Devam Ediyor</option>
<option>Parça Bekleniyor</option>
<option>Tamamlandı</option>
</select>
</div>
<div class="form-group">
<label>Süre (Saat)</label>
<input type="number" step="0.5" id="sure" placeholder="">
</div>
<div class="form-group">
<label>Garanti</label>
<select id="garantiKapsam">
<option value="">Seçiniz...</option>
<option>Evet</option>
<option>Hayır</option>
</select>
</div>
</div>

<div class="form-group" style="margin-top: 15px;">
<label>Notlar</label>
<textarea id="notlar" placeholder=""></textarea>
</div>
</div>

<!-- Onay -->
<div class="section">
<h2 class="section-title">Onay</h2>
<div class="form-row">
<div class="form-group">
<label>Teknisyen</label>
<input type="text" id="teknisyen" placeholder="">
</div>
<div class="form-group">
<label>Onaylayan</label>
<input type="text" id="onaylayan" placeholder="">
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
function setPriority(btn, level) {
document.querySelectorAll('.priority-btn').forEach(b => b.classList.remove('active'));
btn.classList.add('active');
}

function yeniParca() {
const container = document.getElementById('parcaListesi');
const card = document.createElement('div');
card.className = 'parts-card';
card.innerHTML = `
<div class="parts-row">
<input type="text" placeholder="Parça Kodu">
<input type="text" placeholder="Parça Adı">
</div>
<div class="parts-row">
<input type="number" placeholder="Miktar">
<input type="text" placeholder="Birim Fiyat">
</div>
<button class="btn-icon btn-remove" onclick="this.parentElement.remove()">Sil</button>
`;
container.appendChild(card);
}

function formTemizle() {
if(confirm('Tüm alanlar temizlenecek?')) {
document.querySelectorAll('input, textarea').forEach(el => el.value = '');
document.querySelectorAll('select').forEach(el => el.selectedIndex = 0);
document.querySelectorAll('input[type="checkbox"]').forEach(el => el.checked = false);
}
}

function formYazdir() {
window.print();
}

// Bugünün tarihi
document.getElementById('bildirimTarihi').valueAsDate = new Date();
</script>
</body>
</html>
