<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Happy Birthday 🎉</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family: 'Segoe UI', sans-serif;
}

body{
  background: radial-gradient(circle at top, #ff0080, #000);
  color:white;
  height:100vh;
  overflow:hidden;
}

/* Pages */
.page{
  position:absolute;
  inset:0;
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  transition:1s ease;
}

.hidden{
  opacity:0;
  transform:scale(1.3);
  pointer-events:none;
}

/* Page 1 */
h1{
  font-size:2.8rem;
  animation: glow 2s infinite alternate;
}

@keyframes glow{
  from{text-shadow:0 0 10px #fff;}
  to{text-shadow:0 0 25px #ff0;}
}

button{
  margin-top:30px;
  padding:15px 40px;
  font-size:1.1rem;
  border:none;
  border-radius:30px;
  cursor:pointer;
  background:linear-gradient(45deg,#ff0,#ff0080);
  color:black;
  box-shadow:0 0 20px #ff0;
  transition:.3s;
}

button:hover{
  transform:scale(1.1);
}

/* Page 2 */
.balloons span{
  font-size:3rem;
  animation: float 3s infinite ease-in-out;
  display:inline-block;
}

.balloons span:nth-child(2){animation-delay:.5s}
.balloons span:nth-child(3){animation-delay:1s}

@keyframes float{
  0%{transform:translateY(0)}
  50%{transform:translateY(-25px)}
  100%{transform:translateY(0)}
}

/* Page 3 */
.name{
  font-size:3.2rem;
  color:#ff0;
}

.message{
  margin-top:15px;
  font-size:1.2rem;
  max-width:300px;
  text-align:center;
}

/* Confetti */
.confetti{
  position:absolute;
  width:10px;
  height:10px;
  background:red;
  animation: fall 3s linear infinite;
}

@keyframes fall{
  from{top:-10px; transform:rotate(0deg)}
  to{top:110vh; transform:rotate(360deg)}
}
</style>
</head>

<body>

<!-- PAGE 1 -->
<div class="page" id="p1">
  <h1>🎂 Something Special For You 🎂</h1>
  <button onclick="next(1)">Tap to Continue 💖</button>
</div>

<!-- PAGE 2 -->
<div class="page hidden" id="p2">
  <div class="balloons">
    <span>🎈</span>
    <span>🎉</span>
    <span>🎂</span>
  </div>
  <h1 style="margin-top:20px">Guess What? 😍</h1>
  <button onclick="next(2)">Next Surprise ✨</button>
</div>

<!-- PAGE 3 -->
<div class="page hidden" id="p3">
  <div class="name">Happy Birthday Bestie 💖</div>
  <div class="message">
    May your life be full of smiles, success & endless happiness 🌸  
    You deserve the BEST 💫
  </div>
  <button onclick="confetti()">Celebrate 🎊</button>
</div>

<script>
function next(n){
  document.getElementById("p"+n).classList.add("hidden");
  document.getElementById("p"+(n+1)).classList.remove("hidden");
}

/* Confetti Effect */
function confetti(){
  for(let i=0;i<50;i++){
    let c=document.createElement("div");
    c.className="confetti";
    c.style.left=Math.random()*100+"vw";
    c.style.background=`hsl(${Math.random()*360},100%,50%)`;
    c.style.animationDuration=2+Math.random()*3+"s";
    document.body.appendChild(c);
    setTimeout(()=>c.remove(),5000);
  }
}
</script>

</body>
</html>
