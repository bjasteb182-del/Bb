<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>KHI STORE</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:'Poppins',sans-serif;}
body{background:#0d0818;color:white;}
.container{max-width:700px;margin:auto;padding:20px;}
.banner{width:100%;height:220px;background:linear-gradient(135deg,#6d28d9,#9333ea);border-radius:20px;display:flex;justify-content:center;align-items:center;font-size:40px;font-weight:bold;margin-bottom:20px;}
.card{background:#1a1230;padding:18px;border-radius:18px;margin-bottom:18px;box-shadow:0 0 15px rgba(128,0,255,.2);}
h2{margin-bottom:15px;font-size:20px;}
input{width:100%;padding:15px;border:none;border-radius:12px;outline:none;background:#271b47;color:white;font-size:16px;}
.nominal{display:grid;grid-template-columns:repeat(2,1fr);gap:15px;}
.item{background:#24173d;border:2px solid transparent;border-radius:15px;padding:15px;cursor:pointer;transition:.3s;}
.item:hover{border-color:#9d4edd;transform:translateY(-3px);}
.item.active{border-color:#b517ff;background:#35185c;}
.item p{margin-top:8px;color:#9effa5;font-weight:bold;}
.summary div{display:flex;justify-content:space-between;margin:12px 0;}
.total{font-size:20px;font-weight:bold;color:#00ff88;}
button{width:100%;padding:16px;border:none;border-radius:15px;background:#25D366;color:white;font-size:18px;font-weight:bold;cursor:pointer;}
</style>
</head>
<body>
<div class="container">
<div class="banner">KHI STORE</div>
<div class="card"><h2>Masukkan Email</h2><input type="email" id="email" placeholder="Masukkan Email"></div>
<div class="card"><h2>Pilih Nominal</h2><div class="nominal">
<div class="item" data-item="50 Result" data-price="5.000"><h3>100 Result</h3><p>Rp10.000</p></div>
<div class="item" data-item="100 Result" data-price="10.000"><h3>200 Result</h3><p>Rp20.000</p></div>
<div class="item" data-item="200 Result" data-price="20.000"><h3>300 Result</h3><p>Rp30.000</p></div>
<div class="item" data-item="300 Result" data-price="30.000"><h3>500 Result</h3><p>Rp50.000</p></div>
<div class="item" data-item="400 Result" data-price="40.000"><h3>1000 Result</h3><p>Rp100.000</p></div>
<div class="item" data-item="500 Result" data-price="50.000"><h3>2000 Result</h3><p>Rp200.000</p></div>
</div></div>
<div class="card"><h2>Ringkasan Order</h2><div class="summary">
<div><span>Email</span><span id="sEmail">-</span></div>
<div><span>Nominal</span><span id="sItem">-</span></div>
<div><span>Harga</span><span id="sHarga">Rp0</span></div>
<hr><div class="total"><span>Total</span><span id="sTotal">Rp0</span></div>
</div></div>
<button id="order">Order via WhatsApp</button>

<script>
let selectedItem="",selectedPrice=0;
const email=document.getElementById("email");
const sEmail=document.getElementById("sEmail");
const sItem=document.getElementById("sItem");
const sHarga=document.getElementById("sHarga");
const sTotal=document.getElementById("sTotal");
email.addEventListener("input",()=>sEmail.textContent=email.value||"-");
document.querySelectorAll(".item").forEach(el=>{
 el.onclick=()=>{
  document.querySelectorAll(".item").forEach(i=>i.classList.remove("active"));
  el.classList.add("active");
  selectedItem=el.dataset.item;
  selectedPrice=Number(el.dataset.price);
  sItem.textContent=selectedItem;
  sHarga.textContent="Rp"+selectedPrice.toLocaleString("id-ID");
  sTotal.textContent="Rp"+selectedPrice.toLocaleString("id-ID");
 };
});
document.getElementById("order").onclick=()=>{
 if(!email.value.trim()){alert("Masukkan email!");return;}
 if(!selectedItem){alert("Pilih nominal!");return;}
 const pesan=`Halo, saya mau order Jasteb Email!

📧 Email  : ${email.value}
📦 Item   : ${selectedItem}
💰 Harga  : Rp${selectedPrice.toLocaleString("id-ID")}

Mohon konfirmasi, terima kasih 🙏`;
 window.open("https://wa.me/6283130816847?text="+encodeURIComponent(pesan),"_blank");
};
</script>

</div></body></html>
