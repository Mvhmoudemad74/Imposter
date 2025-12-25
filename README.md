
<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>الإمبوستر</title>
<style>
body {
  background:#111;
  color:white;
  font-family:Arial;
  text-align:center;
}
button {
  padding:12px 20px;
  font-size:18px;
  margin:10px;
}
.hidden {display:none;}
</style>
</head>

<body>

<h1>🕵️ لعبة الإمبوستر</h1>

<div id="setup">
  <p>عدد اللاعبين</p>
  <input id="players" type="number" value="6" min="3"><br>

  <p>عدد الإمبوستر</p>
  <input id="imposters" type="number" value="1" min="1"><br>

  <button onclick="start()">ابدأ</button>
</div>

<div id="game" class="hidden">
  <h2 id="player"></h2>
  <button onclick="show()">اظهر الدور</button>
  <h3 id="role"></h3>
  <button onclick="next()">التالي</button>
</div>

<script>
let words=["قهوة","بحر","مدرسة","كورة","موبايل","مطعم"];
let roles=[],index=0;

function start(){
  let p=players.value;
  let i=imposters.value;
  let word=words[Math.floor(Math.random()*words.length)];

  roles=[];
  for(let x=0;x<i;x++) roles.push("❌ إمبوستر");
  for(let x=0;x<p-i;x++) roles.push("✅ الكلمة: "+word);
  roles.sort(()=>Math.random()-0.5);

  setup.classList.add("hidden");
  game.classList.remove("hidden");
  update();
}

function update(){
  role.innerText="";
  player.innerText="لاعب رقم "+(index+1);
}

function show(){
  role.innerText=roles[index];
}

function next(){
  index++;
  if(index>=roles.length){
    alert("ابدأوا اللعب 🎉");
    location.reload();
  } else update();
}
</script>

</body>
</html>
