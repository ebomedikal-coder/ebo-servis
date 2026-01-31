<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>EBO Servis - Admin Giriş</title>
<script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-auth-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-database-compat.js"></script>
<style>
* { margin: 0; padding: 0; box-sizing: border-box; }
body {
font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
min-height: 100vh;
display: flex;
align-items: center;
justify-content: center;
}
.login-container {
background: white;
padding: 40px;
border-radius: 10px;
box-shadow: 0 10px 25px rgba(0,0,0,0.2);
width: 90%;
max-width: 400px;
}
h1 {
text-align: center;
color: #333;
margin-bottom: 10px;
font-size: 24px;
}
.subtitle {
text-align: center;
color: #666;
margin-bottom: 30px;
font-size: 14px;
}
.form-group {
margin-bottom: 20px;
}
label {
display: block;
margin-bottom: 5px;
color: #555;
font-weight: 600;
}
input {
width: 100%;
padding: 12px;
border: 2px solid #ddd;
border-radius: 5px;
font-size: 14px;
}
input:focus {
outline: none;
border-color: #667eea;
}
button {
width: 100%;
padding: 12px;
background: #667eea;
color: white;
border: none;
border-radius: 5px;
font-size: 16px;
font-weight: 600;
cursor: pointer;
}
button:hover { background: #5568d3; }
.error {
color: #e74c3c;
text-align: center;
margin-top: 10px;
display: none;
}
.loading {
display: none;
text-align: center;
margin-top: 10px;
color: #667eea;
}
</style>
</head>
<body>
<div class="login-container">
<h1>🔧 EBO Servis</h1>
<p class="subtitle">Endüstriyel Bakım Onarım Sistemi</p>

<form id="loginForm">
<div class="form-group">
<label for="email">E-posta</label>
<input type="email" id="email" required placeholder="admin@eboservis.com">
</div>

<div class="form-group">
<label for="password">Şifre</label>
<input type="password" id="password" required placeholder="••••••••">
</div>

<button type="submit">Giriş Yap</button>
<div class="error" id="error"></div>
<div class="loading" id="loading">Giriş yapılıyor...</div>
</form>
</div>

<script src="js/firebase-config.js"></script>
<script>
auth.onAuthStateChanged(user => {
if (user) window.location.href = 'admin.html';
});

document.getElementById('loginForm').addEventListener('submit', (e) => {
e.preventDefault();
const email = document.getElementById('email').value;
const password = document.getElementById('password').value;
const errorDiv = document.getElementById('error');
const loadingDiv = document.getElementById('loading');

errorDiv.style.display = 'none';
loadingDiv.style.display = 'block';

auth.signInWithEmailAndPassword(email, password)
.then(() => window.location.href = 'admin.html')
.catch(error => {
loadingDiv.style.display = 'none';
errorDiv.style.display = 'block';
errorDiv.textContent = 'Giriş başarısız: ' + error.message;
});
});
</script>
</body>
</html>
