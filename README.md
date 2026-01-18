# 3 year 
<!Mnkhgrl ees html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<title>❤️ Чамд зориулав</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:'Segoe UI',sans-serif}
body{
  height:100vh;
  background:radial-gradient(circle at bottom,#0b1d3a,#000);
  overflow:hidden;
  color:white;
}

/* Stars */
body::before{
  content:"";
  position:absolute;
  width:200%;
  height:200%;
  background:url("https://i.imgur.com/9aKQK0L.png");
  animation:stars 120s linear infinite;
  opacity:.6;
}
@keyframes stars{
  from{transform:translate(0,0)}
  to{transform:translate(-500px,-500px)}
}

/* Center */
.center{
  position:absolute;
  top:50%;
  left:50%;
  transform:translate(-50%,-50%);
  text-align:center;
}

/* Gift box */
#gift{
  font-size:100px;
  cursor:pointer;
  transition:.4s;
  display:none;
}
#gift.open{
  transform:scale(1.2) rotate(10deg);
}

/* Input */
input{
  padding:10px 15px;
  border-radius:8px;
  border:none;
  outline:none;
  font-size:16px;
}

/* Button */
button{
  padding:10px 18px;
  border:none;
  border-radius:8px;
  background:#ff4d6d;
  color:white;
  font-size:16px;
  cursor:pointer;
}

/* Proposal text */
#proposal{
  font-size:48px;
  margin-top:30px;
  display:none;
  animation:fadeUp 2s ease forwards;
}
@keyframes fadeUp{
  from{opacity:0;transform:translateY(40px)}
  to{opacity:1;transform:translateY(0)}
}

/* Fireworks */
.firework{
  position:absolute;
  width:6px;
  height:6px;
  background:white;
  border-radius:50%;
  animation:explode 2s ease-out forwards;
}
@keyframes explode{
  from{transform:scale(0)}
  to{transform:scale(40);opacity:0}
}

/* Love texts */
.love{
  position:absolute;
  bottom:-40px;
  font-size:20px;
  animation:rise 10s linear forwards;
  opacity:.9;
}
@keyframes rise{
  to{transform:translateY(-110vh);opacity:0}
}
</style>
</head>

<body>

<div class="center">
  <div id="codeBox">
    <p style="margin-bottom:10px;">🔐 Код оруулна уу</p>
    <input id="code" placeholder="Code...">
    <br><br>
    <button onclick="checkCode()">Нээх</button>
  </div>

  <div id="gift" onclick="openGift()">🎁</div>

  <div id="proposal">💍 Надтай үерхээч ❤️</div>
</div>

<script>
let opened=false;

function checkCode(){
  const code=document.getElementById("code").value;
  if(code==="Tiim"){
    document.getElementById("codeBox").style.display="none";
    document.getElementById("gift").style.display="block";
  }else{
    alert("❌ Код буруу байна");
  }
}

function openGift(){
  if(opened) return;
  opened=true;

  const gift=document.getElementById("gift");
  gift.classList.add("open");

  fireworks();
  setTimeout(()=>{
    document.getElementById("proposal").style.display="block";
    startLove();
  },2000);
}

/* Fireworks */
function fireworks(){
  for(let i=0;i<8;i++){
    const f=document.createElement("div");
    f.className="firework";
    f.style.left=Math.random()*100+"%";
    f.style.top=Math.random()*60+"%";
    document.body.appendChild(f);
    setTimeout(()=>f.remove(),2000);
  }
}

/* 30 languages love */
const loves=[
"I love you","Te amo","Je t'aime","Ich liebe dich","Ti amo",
"Я тебя люблю","愛してる","사랑해","我爱你","Ik hou van jou",
"Seni seviyorum","Te iubesc","Σ'αγαπώ","Jeg elsker dig",
"Minä rakastan sinua","Mahal kita","Aku cinta kamu",
"Eu te amo","Ana behibek","Volim te","Kocham cię",
"Jag älskar dig","Te quiero","Es mīlu tevi",
"Ngiyakuthanda","Ndagukunda","Ek het jou lief",
"Ti voglio bene"
];

function startLove(){
  loves.forEach((t,i)=>{
    setTimeout(()=>{
      const d=document.createElement("div");
      d.className="love";
      d.innerText=t;
      d.style.left=Math.random()*90+"%";
      document.body.appendChild(d);
      setTimeout(()=>d.remove(),10000);
    },i*300);
  });
}
</script>

</body>
</html>
