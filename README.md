r# aliabdulrazek319.github.io[homecoming_invite_website_single_file.html](https://github.com/user-attachments/files/22940568/homecoming_invite_website_single_file.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>🌟 Homecoming? 🌟</title>
  <style>
    :root{
      --bg1:#ff9a9e; --bg2:#fad0c4; --bg3:#fbc2eb; --bg4:#a18cd1;
      --btn:#ffffff; --btnText:#333; --yes:#24d17e; --no:#ff5d73;
    } 
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0; font-family: system-ui, -apple-system, Segoe UI, Roboto, Ubuntu, Cantarell, Noto Sans, Arial, "Apple Color Emoji", "Segoe UI Emoji";
      color:#fff; overflow-x:hidden;
      background: linear-gradient(135deg,var(--bg1),var(--bg2),var(--bg3),var(--bg4));
      background-size: 300% 300%;
      animation: shift 15s ease-in-out infinite;
    }
    @keyframes shift{0%{background-position:0% 50%}50%{background-position:100% 50%}100%{background-position:0% 50%}}

    /* Flashy title */
    .title{ 
      text-align:center; margin:28px 12px 8px; font-size: clamp(2.2rem, 6vw, 5rem); font-weight:900; 
      text-shadow: 0 2px 0 rgba(0,0,0,.25), 0 0 18px rgba(255,255,255,.7);
      letter-spacing:1px;
      animation: pop 1.2s ease-out both;
    }
    @keyframes pop{0%{transform:scale(.9);opacity:0}80%{transform:scale(1.05);opacity:1}100%{transform:scale(1)}}
    .subtitle{ text-align:center; font-size:clamp(1rem,2.3vw,1.35rem); opacity:.9; margin-bottom:20px }

    /* Content container */
    .wrap{max-width: 980px; margin: 0 auto 60px; padding: 0 18px; position:relative}

    /* Video */
    .video-frame{ position:relative; padding-top:56.25%; border-radius:24px; overflow:hidden; box-shadow:0 12px 40px rgba(0,0,0,.25);}
    .video-frame iframe, .video-frame video{ position:absolute; inset:0; width:100%; height:100%; border:0 }

    /* Description */
    .desc{ background: rgba(255,255,255,.15); backdrop-filter: blur(6px); border-radius:18px; padding:18px 16px; margin-top:18px; box-shadow:0 6px 24px rgba(0,0,0,.15)}
    .desc h2{ margin:6px 0 10px; font-size:clamp(1.2rem,2.7vw,1.8rem)}
    .desc p{ margin:0 0 8px; line-height:1.6 }

    /* Start button */
    .cta{ display:flex; justify-content:center; margin:22px 0 8px }
    .cta button{ 
      appearance:none; border:0; padding:16px 26px; border-radius:999px; font-weight:800; font-size:clamp(1rem,2.5vw,1.2rem);
      background: #fff; color:#222; cursor:pointer; box-shadow:0 10px 30px rgba(0,0,0,.25); transition: transform .12s ease, box-shadow .12s ease;
    }
    .cta button:hover{ transform: translateY(-2px); box-shadow:0 14px 36px rgba(0,0,0,.3) }

    /* Monkey stickers */
    .monkeys{ position:fixed; inset:0; pointer-events:none; z-index:0 }
    .monkeys span{ position:absolute; font-size: clamp(22px, 4.2vw, 44px); opacity:.25; filter: drop-shadow(0 2px 2px rgba(0,0,0,.2)); animation: float 8s ease-in-out infinite }
    @keyframes float{ 0%,100%{ transform:translateY(0)} 50%{ transform:translateY(-18px) }}

    /* Modal */
    .modal{ position:fixed; inset:0; display:none; align-items:center; justify-content:center; z-index:5; }
    .modal.show{ display:flex }
    .modal::before{ content:""; position:absolute; inset:0; background:rgba(0,0,0,.35); backdrop-filter: blur(2px)}
    .card{ position:relative; z-index:1; width:min(92vw, 560px); background:#fff; color:#111; border-radius:22px; box-shadow:0 20px 60px rgba(0,0,0,.35); overflow:hidden }
    .card .head{ padding:18px 18px 8px; background:linear-gradient(135deg,#fff 0%, #ffe3f1 100%)}
    .card h3{ margin:0; font-size: clamp(1.25rem,2.6vw,1.8rem) }
    .card .body{ padding: 16px 18px 8px; font-size: 1rem; }
    .q{ font-weight:700; font-size: clamp(1.1rem,2.5vw,1.4rem); margin:0 0 16px }
    .btns{ display:flex; gap:12px; flex-wrap:wrap; }
    .btn{ flex:1 1 120px; padding:14px 16px; border:0; border-radius:12px; font-weight:800; cursor:pointer; font-size:1rem }
    .yes{ background:var(--yes); color:white }
    .no{ background:var(--no); color:white; position:relative }

    /* Confetti */
    .confetti{ position:fixed; inset:0; pointer-events:none; z-index:10; overflow:hidden }
    .piece{ position:absolute; width:10px; height:16px; background: white; opacity:.9; animation: fall 2.4s linear forwards }
    @keyframes fall { 
      0%{ transform: translateY(-110vh) rotate(0deg)}
      100%{ transform: translateY(110vh) rotate(720deg)}
    }

    footer{ text-align:center; font-size:.9rem; opacity:.85; margin: 22px 0 36px }
    footer a{ color:#fff; font-weight:700 }
  </style>
</head>
<body>
  <!-- Monkey Sticker Field -->
  <div class="monkeys" id="monkeys" aria-hidden="true"></div>

  <h1 class="title">✨ Hey <span id="herName">You</span>… Homecoming? ✨</h1>
  <p class="subtitle">I made this just for you 💖</p>

  <div class="wrap">
    <div class="video-frame" aria-label="Video">
      <!-- ➜ Replace the src below with your own YouTube embed URL or drop in a <video> tag. -->
      <iframe 
        id="video"
        src="https://www.youtube.com/embed/dQw4w9WgXcQ?rel=0&modestbranding=1"
        title="A special video"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen>
      </iframe>
    </div>

    <div class="cta">
      <button id="start">Tap to Answer a Few Cute Questions 💌</button>
    </div>

    <section class="desc">
      <h2>Why this page exists</h2>
      <p id="message">Because you light up every room, and I wanted to make something fun and a little extra to ask you properly. If you say yes, I promise the best night, the best photos, and unlimited snacks. If you say no… my browser might accidentally crash 😅.</p>
    </section>
  </div>

  <!-- Modal -->
  <div class="modal" id="modal" role="dialog" aria-modal="true" aria-labelledby="qText">
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

  <div class="confetti" id="confetti" aria-hidden="true"></div>

  <footer>
    <span>Made with 🐵💖 by <span id="Monkey Smiggie">Someone who thinks you're amazing</span></span>
  </footer>

  <script>
    /* ======== Easy Customization ========
      Change the placeholders below to personalize:
    */
    const SETTINGS = {
      herName: "[Her Name]",            // shows in title
      yourName: "[Your Name]",          // footer credit
      // YouTube embed URL (replace in the iframe above, or set here & we inject):
      videoEmbedUrl: "https://www.youtube.com/embed/dQw4w9WgXcQ?rel=0&modestbranding=1",
      introMessage: "Because you light up every room, and I wanted to make something fun and a little extra to ask you properly. If you say yes, I promise the best night, the best photos, and unlimited snacks. If you say no… my browser might accidentally crash 😅.",
      monkeyEmojis: ["🐵","🙈","🙉","🙊"],
      monkeyCount: 36
    };

    // Apply quick personalization
    document.getElementById('herName').textContent = SETTINGS.herName;
    document.getElementById('yourName').textContent = SETTINGS.yourName;
    document.getElementById('message').textContent = SETTINGS.introMessage;
    if(SETTINGS.videoEmbedUrl){
      document.getElementById('video').src = SETTINGS.videoEmbedUrl;
    }

    // Add floating monkey stickers
    const field = document.getElementById('monkeys');
    const rand = (min,max)=> Math.random()*(max-min)+min;
    for(let i=0;i<SETTINGS.monkeyCount;i++){
      const s = document.createElement('span');
      s.textContent = SETTINGS.monkeyEmojis[i % SETTINGS.monkeyEmojis.length];
      s.style.left = rand(-5,95) + 'vw';
      s.style.top = rand(0,85) + 'vh';
      s.style.animationDelay = rand(0,6)+'s';
      field.appendChild(s);
    }

    // Questions flow
    const questions = [
      { text: "Do you like me?", loopOnNo: false },
      { text: "Are you the prettiest girl in the world?", loopUntilYes: true },
      { text: "Will you go to homecoming with me?", runawayNo: true }
    ];
    let qIndex = 0;

    const modal = document.getElementById('modal');
    const qText = document.getElementById('qText');
    const yesBtn = document.getElementById('yesBtn');
    const noBtn  = document.getElementById('noBtn');

    const start = document.getElementById('start');
    start.addEventListener('click', ()=>{
      qIndex = 0; showQuestion(); modal.classList.add('show');
    });

    function showQuestion(){
      const q = questions[qIndex];
      qText.textContent = q.text;
      resetNoButton();
    }

    function resetNoButton(){
      noBtn.style.position = 'relative';
      noBtn.style.left = '0px';
      noBtn.style.top = '0px';
    }

    yesBtn.addEventListener('click', ()=>{
      const q = questions[qIndex];
      if(qIndex < questions.length - 1){
        qIndex++;
        showQuestion();
      }else{
        // final YES!
        modal.classList.remove('show');
        celebrate();
        niceFinale();
      }
    });

    noBtn.addEventListener('click', (e)=>{
      const q = questions[qIndex];
      if(q.loopUntilYes){
        // simply re-ask the same question until yes is pressed
        qText.textContent = "Oops, try again 😜 — " + q.text;
        playfulJiggle(noBtn);
        return;
      }
      if(q.runawayNo){
        // move the No button to make it hard to click
        const parent = noBtn.parentElement.getBoundingClientRect();
        const newLeft = Math.random()*(parent.width - noBtn.offsetWidth) - (parent.width/2 - noBtn.offsetWidth/2);
        const newTop  = Math.random()*60 - 30; // up/down within row
        noBtn.style.position = 'relative';
        noBtn.style.left = newLeft + 'px';
        noBtn.style.top  = newTop  + 'px';
        qText.textContent = "Are you suuure? 🥺 ";
        return;
      }
      // For other "No" answers: proceed but leave a cheeky note
      qIndex++;
      if(qIndex >= questions.length){
        modal.classList.remove('show');
        celebrate();
        niceFinale();
      } else {
        qText.textContent = "Noted 😅… but next question!";
        setTimeout(showQuestion, 750);
      }
    });

    function playfulJiggle(el){
      el.animate([
        { transform:'translateX(0)' },
        { transform:'translateX(-6px)' },
        { transform:'translateX(6px)' },
        { transform:'translateX(0)' }
      ], { duration:300, easing:'ease-in-out' });
    }

    function niceFinale(){
      const h = document.querySelector('.title');
      h.innerHTML = `🎉 Yay! See you at Homecoming, <strong>${SETTINGS.herName || 'You'}</strong>! 🎉`;
      document.querySelector('.subtitle').textContent = 'You just made my week. Get ready for the best night.';
    }

    // Tiny confetti generator
    function celebrate(){
      const layer = document.getElementById('confetti');
      const colors = ['#ffd166','#06d6a0','#118ab2','#ef476f','#8338ec','#ff6b6b','#4d96ff','#ffd6e0'];
      for(let i=0;i<180;i++){
        const p = document.createElement('div');
        p.className = 'piece';
        p.style.left = (Math.random()*100)+'vw';
        p.style.background = colors[i % colors.length];
        p.style.animationDelay = (Math.random()*0.8)+'s';
        p.style.transform = `translateY(-105vh) rotate(${Math.random()*360}deg)`;
        layer.appendChild(p);
        setTimeout(()=> p.remove(), 3000);
      }
    }

    // Auto-open questions after a short delay for extra flair
    setTimeout(()=>{ start.focus(); }, 800);
  </script>
</body>
</html>
