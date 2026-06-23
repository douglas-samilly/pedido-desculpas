# pedido-desculpas
<!DOCTYPE html>

<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>Missão Reconquistar Seu Perdão ❤️</title>

<style>

:root{
--rosa:#ff4f8b;
--rosa2:#ff7eb3;
--glass:rgba(255,255,255,.15);
--branco:#fff;
}

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
}

body{
background:linear-gradient(135deg,#ff6b9f,#ff8ec5);
min-height:100vh;
overflow-x:hidden;
color:white;
padding-bottom:50px;
}

body::before{
content:'';
position:fixed;
inset:0;
backdrop-filter:blur(40px);
z-index:-1;
}

.hero{
padding:50px 20px 20px;
text-align:center;
}

.foto{
width:220px;
height:220px;
border-radius:50%;
object-fit:cover;
border:6px solid white;
box-shadow:0 15px 50px rgba(255,255,255,.4);
}

h1{
font-size:2.2rem;
margin-top:20px;
}

.subtitle{
margin-top:10px;
opacity:.95;
line-height:1.6;
}

.card{
width:92%;
max-width:850px;
margin:20px auto;
padding:25px;
border-radius:25px;
background:rgba(255,255,255,.18);
backdrop-filter:blur(20px);
border:1px solid rgba(255,255,255,.2);
}

.card h2{
margin-bottom:15px;
}

#carta{
line-height:1.8;
min-height:160px;
}

.contador{
margin-top:20px;
font-weight:bold;
font-size:1.1rem;
}

.gifts{
display:grid;
grid-template-columns:1fr;
gap:15px;
}

.gift{
background:white;
color:#333;
padding:20px;
border-radius:20px;
text-align:center;
cursor:pointer;
transition:.3s;
}

.gift:active{
transform:scale(.96);
}

.btn{
background:white;
color:var(--rosa);
border:none;
padding:14px 25px;
border-radius:999px;
font-size:1rem;
font-weight:bold;
cursor:pointer;
}

.btn2{
background:var(--rosa);
color:white;
border:none;
padding:14px 25px;
border-radius:999px;
font-size:1rem;
margin-top:10px;
}

.barra{
height:25px;
background:rgba(255,255,255,.2);
border-radius:30px;
overflow:hidden;
margin-top:15px;
}

#progresso{
width:10%;
height:100%;
background:white;
transition:.5s;
}

.frase{
text-align:center;
font-size:1.1rem;
padding:10px;
font-weight:600;
}

.final{
text-align:center;
}

#nao{
position:relative;
}

.modal{
display:none;
position:fixed;
inset:0;
background:rgba(0,0,0,.8);
justify-content:center;
align-items:center;
padding:20px;
z-index:1000;
}

.modal-box{
background:white;
color:#333;
padding:25px;
border-radius:25px;
max-width:400px;
width:100%;
text-align:center;
}

.modal-box h2{
color:#ff4f8b;
margin-bottom:15px;
}

#fim{
display:none;
position:fixed;
inset:0;
background:#111;
justify-content:center;
align-items:center;
flex-direction:column;
text-align:center;
z-index:9999;
}

#fim h1{
font-size:2rem;
}

.heart{
position:fixed;
pointer-events:none;
animation:subir 8s linear forwards;
}

@keyframes subir{
from{
transform:translateY(100vh);
opacity:1;
}
to{
transform:translateY(-150px);
opacity:0;
}
}

@media(min-width:700px){

.gifts{
grid-template-columns:repeat(2,1fr);
}

}

</style>

</head>

<body>

<audio id="musica" loop>
<source src="musica.mp3" type="audio/mpeg">
</audio>

<section class="hero">

<img src="foto.jpg" class="foto">

<h1>🥺 Pedido Oficial de Desculpas</h1>

<p class="subtitle">
Depois de uma análise extremamente detalhada,
foi concluído que eu realmente estava errado(a).
</p>

<div class="contador" id="contador"></div>

<br>

<button class="btn" onclick="tocarMusica()">
🎵 Iniciar Música
</button>

</section>

<div class="card">

<h2>💌 Carta Aberta</h2>

<p id="carta"></p>

</div>

<div class="card">

<h2>🏆 Nível de Reconquista</h2>

<div class="barra">
<div id="progresso"></div>
</div>

</div>

<div class="card">

<h2>🎁 Escolha Seu Presente</h2>

<div class="gifts">

<div class="gift" onclick="abrir('chocolate')">
🍫 Chocolate Supremo
</div>

<div class="gift" onclick="abrir('pizza')">
🍕 Vale Pizza
</div>

<div class="gift" onclick="abrir('rainha')">
👑 Dia da Rainha
</div>

<div class="gift" onclick="abrir('vale')">
🛍️ Vale Presente
</div>

<div class="gift" onclick="abrir('premium')">
💎 Perdão Premium Deluxe
</div>

</div>

</div>

<div class="card">
<div class="frase" id="frase"></div>
</div>

<div class="card final">

<h2>❤️ Pergunta Final</h2>

<br>

<button class="btn"
onclick="aceitou()">
Sim, eu te perdoo ❤️ </button>

<br><br>

<button class="btn2" id="nao">
Não 😡
</button>

</div>

<div class="modal" id="modal">

<div class="modal-box">

<h2 id="titulo"></h2>

<p id="descricao"></p>

<br>

<button class="btn2"
onclick="confirmar()">
Quero esse ❤️ </button>

</div>

</div>

<div id="fim">

<h1>🎉 MISSÃO CONCLUÍDA 🎉</h1>

<h2>
Ela me perdoou ❤️
</h2>

<br>

<p>
Obrigado por me dar mais uma chance.
</p>

</div>

<script>

const texto = `
Eu sei que desculpas sozinhas não resolvem tudo.

Mas quero que você saiba que reconheço meu erro.

Você é uma pessoa extremamente importante para mim.

E este pequeno site é apenas uma forma de mostrar
que estou tentando reparar minha burrada.

❤️
`;

let i=0;

function escrever(){

if(i<texto.length){

document.getElementById("carta")
.innerHTML += texto.charAt(i);

i++;

setTimeout(escrever,35);

}

}

escrever();

const dataErro =
new Date("2025-01-01");

const hoje = new Date();

const dias =
Math.floor(
(hoje-dataErro)/
(1000*60*60*24)
);

contador.innerHTML =
"🤦 Dias desde a burrada: "
+ dias;

const frases=[

"Você é minha pessoa favorita ❤️",

"Obrigado por estar aqui 🥺",

"Prometo tentar errar menos 😅",

"Você merece o melhor ✨",

"Estou me esforçando de verdade ❤️"

];

let indice=0;

setInterval(()=>{

frase.innerHTML =
frases[indice];

indice++;

if(indice>=frases.length)
indice=0;

},3000);

function tocarMusica(){

document.getElementById("musica")
.play();

}

const presentes={

chocolate:{
titulo:"🍫 Chocolate Supremo",
descricao:"Inclui chocolate premium, abraço de desculpas e direito oficial de reclamar."
},

pizza:{
titulo:"🍕 Vale Pizza",
descricao:"Pizza completa e escutar todas as reclamações sem contestar."
},

rainha:{
titulo:"👑 Dia da Rainha",
descricao:"Você manda. Eu obedeço."
},

vale:{
titulo:"🛍️ Vale Presente",
descricao:"Você escolhe o presente."
},

premium:{
titulo:"💎 Perdão Premium Deluxe",
descricao:"Todos os benefícios anteriores combinados."
}

};

let progresso=10;

function abrir(tipo){

modal.style.display="flex";

titulo.innerHTML=
presentes[tipo].titulo;

descricao.innerHTML=
presentes[tipo].descricao;

}

function confirmar(){

modal.style.display="none";

progresso+=18;

if(progresso>100)
progresso=100;

document
.getElementById("progresso")
.style.width=
progresso+"%";

}

window.onclick=e=>{

if(e.target===modal){

modal.style.display="none";

}

}

nao.addEventListener(
"touchstart",
fugir
);

nao.addEventListener(
"mouseover",
fugir
);

function fugir(){

const x=
(Math.random()*200)-100;

const y=
(Math.random()*120)-60;

nao.style.transform=
`translate(${x}px,${y}px)`;

}

setInterval(()=>{

let h=document.createElement("div");

h.className="heart";

h.innerHTML="❤️";

h.style.left=
Math.random()*100+"vw";

h.style.fontSize=
(20+Math.random()*25)+"px";

document.body.appendChild(h);

setTimeout(()=>{
h.remove();
},8000);

},500);

function aceitou(){

fim.style.display="flex";

for(let i=0;i<150;i++){

let h=
document.createElement("div");

h.className="heart";

h.innerHTML="🎉";

h.style.left=
Math.random()*100+"vw";

h.style.fontSize="35px";

document.body.appendChild(h);

}

}

</script>

</body>
</html>
