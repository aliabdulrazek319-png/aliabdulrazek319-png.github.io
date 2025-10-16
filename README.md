<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>🌸 Homecoming? 🌸</title>
  <style>
    :root{
      --bg1:#ffb6c1; --bg2:#ffc3a0; --bg3:#fbc2eb; --bg4:#a18cd1;
      --yes:#24d17e; --no:#ff5d73;
    }
    *{box-sizing:border-box;margin:0;padding:0}
    body{
      font-family:"Poppins",system-ui,Arial; color:#fff; overflow-x:hidden;
      background:linear-gradient(135deg,var(--bg1),var(--bg2),var(--bg3),var(--bg4));
      background-size:300% 300%;
      animation:shift 15s ease-in-out infinite;
      min-height:100vh;
    }
    @keyframes shift{
      0%{background-position:0% 50%}
      50%{background-position:100% 50%}
      100%{background-position:0% 50%}
    }

    /* Bubble title */
    .title{
      text-align:center;
      margin:40px 12px 10px;
      font-size:clamp(2.5rem,7vw,5rem);
      font-weight:900;
      background:linear-gradient(90deg,#fff,#ffe0f5,#fff);
      -webkit-background-clip:text;
      -webkit-text-fill-color:transparent;
      text-shadow:0 4px 12px rgba(255,255,255,.7),0 0 25px rgba(255,255,255,.6);
      letter-spacing:1.5px;
      animation:pop 1.4s ease-out both;
    }
    @keyframes pop{0%{transform:scale(.8);opacity:0}70%{transform:scale(1.08);opacity:1}100%{transform:scale(1)}}
    .subtitle{text-align:center;font-size:1.3rem;opacity:.9;margin-bottom:25px}

    .wrap{max-width:900px;margin:0 auto 60px;padding:0 18px}
    .video-frame{position:relative;padding-top:56.25%;border-radius:25px;overflow:hidden;box-shadow:0 10px 35px rgba(0,0,0,.25)}
    .video-frame iframe{position:absolute;inset:0;width:100%;height:100%;border:0}

    .desc{background:rgba(255,255,255,.15);backdrop-filter:blur(6px);border-radius:18px;padding:20px;margin-top:20px;box-shadow:0 6px 24px rgba(0,0,0,.15)}
    .desc h2{margin:6px 0 10px;font-size:1.7rem}
    .desc p{line-height:1.6;margin:0 0 8px}

    .cta{display:flex;justify-content:center;margin:25px 0}
    .cta button{
      border:0;border-radius:999px;padding:16px 30px;font-weight:800;
      background:#fff;color:#333;font-size:1.1rem;cursor:pointer;
      box-shadow:0 8px 28px rgba(0,0,0,.25);transition:transform .12s ease;
    }
    .cta button:hover{transform:scale(1.05)}

    .monkeys{position:fixed;inset:0;pointer-events:none;z-index:0}
    .monkeys span{position:absolute;font-size:clamp(24px,4.5vw,46px);opacity:.25;animation:float 8s ease-in-out infinite}
    @keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-18px)}}

    .modal{position:fixed;inset:0;display:none;align-items:center;justify-content:center;z-index:5}
    .modal.show{display:flex}
    .modal::before{content:\"\";position:absolute;inset:0;background:rgba(0,0,0,.35);backdrop-filter:blur(2px)}
    .card{position:relative;z-index:1;width:min(92vw,560px);background:#fff;color:#111;border-radius:22px;box-shadow:0 20px 60px rgba(0,0,0,.35)}
    .card .head{padding:18px;background:linear-gradient(135deg,#fff,#ffe3f1)}
    .card h3{margin:0;font-size:1.8rem}
    .card .body{padding:18px}
    .q{font-weight:700;font-size:1.4rem;margin-bottom:16px}
    .btns{display:flex;gap:12px;flex-wrap:wrap}
    .btn{flex:1 1 120px;padding:14px;border:0;border-radius:12px;font-weight:800;font-size:1rem;cursor:pointer}
    .yes{background:var(--yes);color:#fff}
    .no{background:var(--no);color:#fff}

    .confetti{position:fixed;inset:0;pointer-events:none;z-index:10}
    .piece{position:absolute;width:10px;height:16px;background:white;opacity:.9;animation:fall 2.4s linear forwards}
    @keyframes fall{0%{transform:translateY(-110vh) rotate(0)}100%{transform:translateY(110vh) rotate(720deg)}}

    footer{text-align:center;font-size:.9rem;opacity:.85;margin:25px 0 40px}
  </style>
</head>
<body>
  <div class="monkeys" id="monkeys" aria-hidden="true"></div>

  <h1 class="title">✨ Hey <span id="herName">Monkey Smiggie</span>… Homecoming? ✨</h1>
  <p class="subtitle">I made this just for you 💖</p>

  <div class="wrap">
    <div class="video-frame">
      <iframe id="video" src="https://www.youtube.com/embed/dQw4w9WgXcQ?rel=0&modestbranding=1"
        title="A special video" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen></iframe>
    </div>

    <div class="cta">
      <button id="start">Tap to Answer a Few Cute Questions 💌</button>
    </div>

    <section class="desc">
      <h2>Why this page exists</h2>
      <p id="message">Because you light up every room, and I wanted to make something fun and a little extra to ask you properly. If you say yes, I promise the best night, the best photos, and unlimited snacks. If you say no… my browser might accidentally crash 😅.</p>
    </section>
  </div>

  <div class="modal" id="modal">
    <div class="card">
      <div class="head"><h3>Quick Questions 🥰</h3></div>
      <div class="body">
        <p class="q" id="qText">Question goes here</p>
        <div class="btns">
          <button class="btn yes" id="yesBtn">Yes</button>
          <button class="btn no" id="noBtn">No</button>
        </div>
      </div>
    </div>
  </div>

  <div class="confetti" id="confetti"></div>

  <footer>
    <span>Made with 🐵💖 by <span id="yourName">Hadi</span></span>
  </footer>

  <script>
    const SETTINGS = {
      herName: "Monkey Smiggie",
      yourName: "Hadi",
      videoEmbedUrl: "https://www.youtube.com/embed/dQw4w9WgXcQ?rel=0&modestbranding=1",
      introMessage: "Because you light up every room, and I wanted to make something fun and a little extra to ask you properly. If you say yes, I promise the best night, the best photos, and unlimited snacks. If you say no… my browser might accidentally crash 😅.",
      monkeyEmojis: ["🐵","🙈","🙉","🙊"],
      monkeyCount: 36
    };

    document.getElementById('herName').textContent = SETTINGS.herName;
    document.getElementById('yourName').textContent = SETTINGS.yourName;
    document.getElementById('message').textContent = SETTINGS.introMessage;
    document.getElementById('video').src = SETTINGS.videoEmbedUrl;

    const field=document.getElementById('monkeys');
    const rand=(min,max)=>Math.random()*(max-min)+min;
    for(let i=0;i<SETTINGS.monkeyCount;i++){
      const s=document.createElement('span');
      s.textContent=SETTINGS.monkeyEmojis[i%SETTINGS.monkeyEmojis.length];
      s.style.left=rand(-5,95)+'vw';
      s.style.top=rand(0,85)+'vh';
      s.style.animationDelay=rand(0,6)+'s';
      field.appendChild(s);
    }

    const questions=[
      {text:"Do you like me?",loopOnNo:false},
      {text:"Are you the prettiest girl in the world?",loopUntilYes:true},
      {text:"Will you go to homecoming with me?",runawayNo:true}
    ];
    let qIndex=0;
    const modal=document.getElementById('modal');
    const qText=document.getElementById('qText');
    const yesBtn=document.getElementById('yesBtn');
    const noBtn=document.getElementById('noBtn');
    const start=document.getElementById('start');

    start.addEventListener('click',()=>{qIndex=0;showQuestion();modal.classList.add('show');});
    function showQuestion(){const q=questions[qIndex];qText.textContent=q.text;noBtn.style.left='0';noBtn.style.top='0';}
    yesBtn.addEventListener('click',()=>{if(qIndex<questions.length-1){qIndex++;showQuestion();}else{modal.classList.remove('show');celebrate();niceFinale();}});
    noBtn.addEventListener('click',()=>{const q=questions[qIndex];
      if(q.loopUntilYes){qText.textContent=\"Oops, try again 😜 — \"+q.text;return;}
      if(q.runawayNo){const parent=noBtn.parentElement.getBoundingClientRect();
        noBtn.style.left=Math.random()*(parent.width-noBtn.offsetWidth)-(parent.width/2-noBtn.offsetWidth/2)+'px';
        noBtn.style.top=Math.random()*60-30+'px';qText.textContent=\"Are you suuure? 🥺 \";return;}
      qIndex++;if(qIndex>=questions.length){modal.classList.remove('show');celebrate();niceFinale();}else{qText.textContent=\"Noted 😅… but next question!\";setTimeout(showQuestion,750);}});
    function niceFinale(){const h=document.querySelector('.title');h.innerHTML=`🎉 Yay! See you at Homecoming, <strong>${SETTINGS.herName}</strong>! 🎉`;document.querySelector('.subtitle').textContent='You just made my week. Get ready for the best night.';}
    function celebrate(){const layer=document.getElementById('confetti');const colors=['#ffd166','#06d6a0','#118ab2','#ef476f','#8338ec','#ff6b6b','#4d96ff','#ffd6e0'];for(let i=0;i<180;i++){const p=document.createElement('div');p.className='piece';p.style.left=(Math.random()*100)+'vw';p.style.background=colors[i%colors.length];p.style.animationDelay=(Math.random()*0.8)+'s';p.style.transform=`translateY(-105vh) rotate(${Math.random()*360}deg)`;layer.appendChild(p);setTimeout(()=>p.remove(),3000);}}
  </script>
</body>
</html>
