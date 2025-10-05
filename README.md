# Happy-birthday-diya-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Happy Birthday Diya, My Love! - A Proposal</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/tone/14.8.49/Tone.min.js"></script>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700&family=Pacifico&family=Space+Mono&display=swap');
    body {
      font-family: 'Inter', sans-serif;
      background: linear-gradient(145deg, #1f001f 0%, #4a001f 100%);
      min-height: 100vh;
      margin: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      padding: 1rem;
    }
    #main-content {
      display: flex;
      flex-direction: column;
      align-items: center;
      width: 100%;
      max-width: 400px;
      margin-top: 1rem;
      margin-bottom: 3rem;
    }
    #scratch-container {
      position: relative;
      cursor: pointer;
      width: 90vw;
      max-width: 400px;
      height: 90vw;
      max-height: 400px;
      border-radius: 2rem;
      box-shadow: 0 10px 40px rgba(255, 105, 180, 0.7);
      z-index: 10;
    }
    #hidden-message {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 1rem;
      background: radial-gradient(circle at center, #FFECB3 0%, #FFB6C1 150%);
      color: #444;
      border-radius: 2rem;
      z-index: 5;
      opacity: 0;
      transition: opacity 0.7s;
    }
    #scratch-surface {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-image: linear-gradient(135deg, #FF66B2 0%, #FFD1DC 100%);
      border: 5px solid #FFC0CB;
      box-shadow: 0 0 25px rgba(255, 192, 203, 0.8);
      border-radius: 2rem;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      color: #fff;
      font-size: 1.2rem;
      font-weight: 700;
      z-index: 10;
      transition: opacity 0.5s ease-out;
      font-family: 'Pacifico', cursive;
    }
    #scratch-surface p:first-child {
      font-size: 3rem;
      text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
    }
    .typing-text {
      font-family: 'Space Mono', monospace;
      overflow: hidden;
      border-right: .15em solid #FF69B4;
      white-space: nowrap;
      margin: 0 auto;
      letter-spacing: .08em;
      animation: blink-caret .75s step-end infinite;
    }
    @keyframes blink-caret { from, to { border-color: transparent } 50% { border-color: #FF69B4; } }
    #confetti-canvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 20;
      opacity: 0;
      transition: opacity 0.5s;
    }
    /* 2-Layer 3D Cake Styles */
    #birthday-cake {
      position: relative;
      width: 320px;
      max-width: 95vw;
      min-height: 320px;
      margin: 2rem auto 0 auto;
      filter: drop-shadow(0 12px 24px rgba(0,0,0,0.5));
      z-index: 15;
      text-align: center;
      opacity: 0; /* Starts hidden, shown via JS */
      transition: opacity 0.6s;
    }
    .cake-stand {
      width: 240px;
      height: 30px;
      background: radial-gradient(ellipse at center, #d1a15f 0%, #b88942 100%);
      border-radius: 0 0 40px 40px/0 0 60px 60px;
      box-shadow: 0 10px 40px #b88942;
      margin: 0 auto;
      position: relative;
      top: 180px;
      z-index: 1;
    }
    .cake-layer-bottom {
      position: absolute;
      left: 30px;
      top: 140px;
      width: 260px;
      height: 80px;
      background: linear-gradient(180deg, #fceabb 0%, #f8bbd0 50%, #e57373 100%);
      border-radius: 0 0 100px 100px / 0 0 80px 80px;
      box-shadow: 0 18px 30px -8px #b71c1c;
      z-index: 2;
      border: 3px solid #fff8e1;
    }
    .cake-bottom-cream {
      position: absolute;
      left: 30px;
      top: 122px;
      width: 260px;
      height: 40px;
      z-index: 3;
    }
    .cake-layer-top {
      position: absolute;
      left: 75px;
      top: 60px;
      width: 170px;
      height: 70px;
      background: linear-gradient(180deg, #fff0e5 0%, #ffd1dc 70%, #f48fb1 100%);
      border-radius: 0 0 60px 60px / 0 0 60px 60px;
      box-shadow: 0 12px 24px -6px #c2185b;
      z-index: 4;
      border: 3px solid #fff8e1;
    }
    .cake-top-cream {
      position: absolute;
      left: 75px;
      top: 40px;
      width: 170px;
      height: 40px;
      z-index: 5;
    }
    .cake-candle {
      position: absolute;
      left: 154px;
      top: 2px;
      width: 14px;
      height: 50px;
      background: linear-gradient(90deg, #ffe066 70%, #fff59d 100%);
      border-radius: 7px;
      box-shadow: 2px 0 8px #ffecb3;
      z-index: 6;
      transition: opacity 0.3s;
    }
    .cake-flame {
      position: absolute;
      left: 158px;
      top: -14px;
      width: 10px;
      height: 22px;
      background: radial-gradient(ellipse at center, #fffde7 0%, #ffd54f 70%, #ff9800 100%);
      border-radius: 60% 60% 60% 60%;
      box-shadow: 0 0 18px 8px #ffd54f;
      animation: flicker .3s infinite alternate;
      z-index: 7;
      transition: opacity 0.3s;
    }
    @keyframes flicker {
      0% { transform: scaleY(1); background: #ffd54f; }
      100% { transform: scaleY(1.18); background: #ff9800; }
    }
    .cake-message {
      color: #fff8e1;
      font-family: 'Pacifico', cursive;
      font-size: 1.3rem;
      text-shadow: 1px 1px 8px #c2185b;
      margin-top: 2.5rem;
      margin-bottom: 0;
      text-align: center;
    }

    /* Proposal & Result Styles */
    #proposal-section, #result-section {
      display: none; /* Initially hidden */
      width: 95vw;
      max-width: 400px;
      margin: 2rem auto 0 auto;
      padding: 2rem;
      background-color: rgba(255, 255, 255, 0.1);
      border-radius: 1.5rem;
      text-align: center;
      color: #ffe082;
      font-family: 'Pacifico', cursive;
      transition: opacity 0.7s;
      opacity: 0;
    }
    #proposal-section h2 {
      font-size: 1.8rem;
      margin-bottom: 1.5rem;
      color: #fff8e1;
      text-shadow: 1px 1px 8px #4a001f;
    }
    .proposal-buttons button {
      font-family: 'Inter', sans-serif;
      font-weight: 700;
      padding: 0.75rem 2rem;
      margin: 0 1rem;
      border-radius: 9999px;
      transition: transform 0.2s, background-color 0.2s;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.4);
    }
    #yes-button {
      background-color: #34D399; /* Emerald Green */
      color: #10B981;
    }
    #no-button {
      background-color: #F87171; /* Red */
      color: #EF4444;
    }
    #yes-button:hover, #no-button:hover {
      transform: scale(1.05);
    }

    /* Result styles */
    #ring-image {
      max-width: 150px;
      margin: 2rem auto;
      filter: drop-shadow(0 0 20px #FFD700);
      animation: sparkle 1s infinite alternate;
    }
    @keyframes sparkle {
      from { transform: scale(1); opacity: 1; }
      to { transform: scale(1.05); opacity: 0.9; }
    }
    #result-message {
      font-size: 1.6rem;
      font-family: 'Pacifico', cursive;
    }
  </style>
</head>
<body>
  <canvas id="confetti-canvas"></canvas>

  <button id="audio-start-button" class="mt-8 px-8 py-4 bg-yellow-500 text-black font-bold text-lg rounded-full shadow-xl hover:bg-yellow-600 transition-colors z-20 transform hover:scale-105">
    Tap Here to Start the Magic!
  </button>
  <div id="main-content">
    <div id="scratch-container" class="mt-8">
      <div id="hidden-message">
        <span class="text-6xl mb-2 text-yellow-500">✨</span>
        <p class="text-3xl font-extrabold tracking-wider font-pacifico" id="revealed-title"></p>
        <p class="mt-2 text-2xl font-light italic font-inter text-gray-700" id="revealed-message" style="margin-top: 1rem;"></p>
      </div>
      <div id="scratch-surface">
        <p class="font-bold tracking-widest z-20">Scratch to Reveal Love!</p>
        <p class="text-gray-200 text-base mt-2 z-20">(Use your finger)</p>
      </div>
    </div>

    <div id="birthday-cake" style="display:none;">
      <div style="position:relative; width:320px; height:220px; margin:auto;">
        <div class="cake-stand"></div>
        <div class="cake-layer-bottom"></div>
        <svg class="cake-bottom-cream" viewBox="0 0 260 40">
          <path d="M0,25 Q30,0 60,20 Q90,40 130,20 Q170,0 200,20 Q230,35 260,25 L260,40 L0,40 Z" fill="#fffde7" opacity="0.93"/>
        </svg>
        <div class="cake-layer-top"></div>
        <svg class="cake-top-cream" viewBox="0 0 170 40">
          <path d="M0,25 Q20,0 40,20 Q70,40 85,20 Q110,0 140,20 Q160,35 170,25 L170,40 L0,40 Z" fill="#fffde7" opacity="0.96"/>
        </svg>
        <div class="cake-candle" id="cake-candle"></div>
        <div class="cake-flame" id="cake-flame"></div>
      </div>
      <p class="cake-message">
        Happy Birthday Diya my love!<br>
        Touch the cake to blow the candle, then touch again for your next surprise...
      </p>
    </div>

    <div id="proposal-section">
      <h2>Will you be my life partner?</h2>
      <div class="proposal-buttons flex justify-center">
        <button id="yes-button" onclick="handleProposal('yes')">YES! ❤️</button>
        <button id="no-button" onclick="handleProposal('no')">NO 😢</button>
      </div>
    </div>

    <div id="result-section">
      <img id="ring-image" style="display:none;" src="https://i.imgur.com/kS5YvPj.png" alt="Diamond Ring">
      <p id="result-message"></p>
    </div>
  </div>
  <script>
    // Scratch logic and other elements
    const scratchContainer = document.getElementById('scratch-container');
    const scratchSurface = document.getElementById('scratch-surface');
    const hiddenMessage = document.getElementById('hidden-message');
    const startButton = document.getElementById('audio-start-button');
    const confettiCanvas = document.getElementById('confetti-canvas');
    const revealedTitleEl = document.getElementById('revealed-title');
    const revealedMessageEl = document.getElementById('revealed-message');
    const birthdayCake = document.getElementById('birthday-cake');
    const cakeCandle = document.getElementById('cake-candle');
    const cakeFlame = document.getElementById('cake-flame');
    
    // Proposal elements
    const proposalSection = document.getElementById('proposal-section');
    const resultSection = document.getElementById('result-section');
    const ringImage = document.getElementById('ring-image');
    const resultMessage = document.getElementById('result-message');

    let isScratching = false, scratchCount = 0, soundInitialized = false;
    const revealThreshold = 40;
    let cakeTouchCount = 0;

    // Tone.js Setup
    const synth = new Tone.PolySynth(Tone.Synth, {
      oscillator: { type: "triangle" },
      envelope: { attack: 0.1, decay: 0.2, sustain: 0.8, release: 1.0 },
      volume: -8
    }).toDestination();
    const noise = new Tone.NoiseSynth({
      noise: { type: 'white' },
      envelope: { attack: 0.001, decay: 0.2, sustain: 0, release: 0 }
    }).toDestination();
    const jingle = [
      { note: "C5", time: 0, duration: "4n" },
      { note: "E5", time: "4n", duration: "4n" },
      { note: "G5", time: "2n", duration: "4n" },
      { note: "C6", time: "2n + 4n", duration: "2n" }
    ];
    function playJingle() {
      jingle.forEach(part => {
        synth.triggerAttackRelease(part.note, part.duration, Tone.now() + part.time);
      });
    }
    function initializeAudio() {
      if (!soundInitialized) {
        Tone.start();
        startButton.style.display = 'none';
        soundInitialized = true;
      }
    }
    startButton.addEventListener('click', initializeAudio);
    startButton.addEventListener('touchstart', initializeAudio);

    // Typing Effect Logic
    function typeWriter(element, text, speed) {
      return new Promise(resolve => {
        let i = 0;
        function type() {
          if (i < text.length) {
            element.textContent += text.charAt(i);
            i++;
            setTimeout(type, speed);
          } else {
            element.classList.remove('typing-text');
            resolve();
          }
        }
        element.textContent = '';
        element.classList.add('typing-text');
        type();
      });
    }
    // Confetti Logic
    const colors = ['#FFD700', '#FFFFFF', '#FFCC00', '#FF69B4', '#E91E63'];
    const numConfetti = 50;
    let confetti = [];
    const ctxConfetti = confettiCanvas.getContext('2d');
    function Confetti(x, y, color) {
      this.x = x;
      this.y = y;
      this.size = Math.random() * 6 + 4;
      this.color = color;
      this.rotation = Math.random() * 360;
      this.velocity = { x: Math.random() * 3 - 1.5, y: Math.random() * 3 - 4 };
      this.gravity = 0.1;
      this.draw = function() {
        ctxConfetti.save();
        ctxConfetti.translate(this.x, this.y);
        ctxConfetti.rotate(this.rotation * Math.PI / 180);
        ctxConfetti.fillStyle = this.color;
        ctxConfetti.fillRect(-this.size / 2, -this.size / 2, this.size, this.size);
        ctxConfetti.restore();
      };
      this.update = function() {
        this.velocity.y += this.gravity;
        this.x += this.velocity.x;
        this.y += this.velocity.y;
        this.rotation += this.velocity.x * 2;
        if (this.y > confettiCanvas.height) {
          this.x = Math.random() * confettiCanvas.width;
          this.y = -10;
          this.velocity.y = Math.random() * 3 - 4;
        }
      };
    }
    function createConfetti() {
      confettiCanvas.style.opacity = '1';
      for (let i = 0; i < numConfetti; i++) {
        const color = colors[Math.floor(Math.random() * colors.length)];
        confetti.push(new Confetti(confettiCanvas.width / 2 + (Math.random() * 100 - 50), -50, color));
      }
    }
    function drawConfettiLoop() {
      if (confettiCanvas.style.opacity !== '1') return;
      ctxConfetti.clearRect(0, 0, confettiCanvas.width, confettiCanvas.height);
      for (let i = 0; i < confetti.length; i++) {
        confetti[i].update();
        confetti[i].draw();
      }
      requestAnimationFrame(drawConfettiLoop);
    }

    // Scratch-Off Card Logic
    function startScratch(e) {
      if (!soundInitialized) return;
      e.preventDefault();
      isScratching = true;
      scratch(e);
    }
    function stopScratch() {
      if (!soundInitialized) return;
      isScratching = false;
      if (scratchCount >= revealThreshold) {
        revealGift();
      }
    }
    function scratch(e) {
      if (!isScratching) return;
      let clientX, clientY;
      if (e.type.startsWith('touch')) {
        e.preventDefault();
        clientX = e.touches[0].clientX;
        clientY = e.touches[0].clientY;
      } else {
        clientX = e.clientX;
        clientY = e.clientY;
      }
      scratchCount++;
      const newOpacity = Math.max(0, 1 - (scratchCount / revealThreshold));
      scratchSurface.style.opacity = newOpacity.toString();
    }
    async function revealGift() {
      scratchSurface.style.opacity = '0';
      setTimeout(async () => {
        scratchSurface.style.display = 'none';
        hiddenMessage.style.opacity = '1';
        playJingle();
        createConfetti();
        drawConfettiLoop();
        // 1. Type Title
        const titleText = `Happy Birthday Diya, my love!`;
        revealedTitleEl.style.fontFamily = "'Pacifico', cursive";
        await typeWriter(revealedTitleEl, titleText, 100);
        // 2. Type Message
        const messageText = `Wishing you a magical birthday, Diya! You are the light of my life. May your day be filled with endless joy, love, and happiness. I love you so much! ❤️`;
        revealedMessageEl.style.fontFamily = "'Inter', sans-serif";
        await typeWriter(revealedMessageEl, messageText, 50);
        // Show Cake
        setTimeout(() => {
          scratchContainer.style.display = 'none';
          // Set display to block before setting opacity for smooth fade-in
          birthdayCake.style.display = 'block'; 
          setTimeout(() => { birthdayCake.style.opacity = '1'; }, 10);
        }, 1300);
      }, 500);
    }

    // --- Utility Functions for Fading ---
    function fadeOut(el) {
      el.style.opacity = 0;
      el.style.transition = 'opacity 0.7s';
      // Set display to none AFTER the transition finishes (700ms)
      setTimeout(()=>{ el.style.display = "none"; }, 700);
    }
    function fadeIn(el) {
      el.style.opacity = 0;
      el.style.display = "flex"; /* Changed to flex for centering content */
      el.style.transition = 'opacity 0.7s';
      // Start transition immediately
      setTimeout(()=>{ el.style.opacity = 1; }, 10);
    }

    // --- Cake Touch Logic (2-step: candle → then proposal) ---
    birthdayCake.addEventListener('click', handleCakeTouch);
    birthdayCake.addEventListener('touchstart', handleCakeTouch);

    function handleCakeTouch(e) {
      e.preventDefault();
      cakeTouchCount++;
      if (cakeTouchCount === 1) {
        // 1st Click: Blow out candle
        cakeCandle.style.opacity = "0";
        cakeFlame.style.opacity = "0";
        noise.triggerAttackRelease("8n"); // Blow sound
      } else if (cakeTouchCount === 2) {
        // 2nd Click: Show Proposal
        
        // 1. Fade out Cake
        fadeOut(birthdayCake);
        
        // 2. Show Proposal Section after cake fades
        // Using 750ms to ensure the cake is fully gone (700ms) before the next one appears
        setTimeout(()=>{
          fadeIn(proposalSection);
        }, 750);
      }
    }

    // --- PROPOSAL HANDLER ---
    function handleProposal(answer) {
      fadeOut(proposalSection);
      setTimeout(() => {
        if (answer === 'yes') {
          // YES logic: Show Ring and Success Message
          ringImage.style.display = 'block';
          resultMessage.textContent = "You said YES! ❤️ My life is complete! I love you so much, my future wife! 🎉💍";
          
          // Play a triumphant chord
          synth.triggerAttackRelease(["C6", "E6", "G6"], "2n", Tone.now());
          
          // Restart confetti or make it blast again
          confetti = []; 
          createConfetti(); 
          drawConfettiLoop();
          
        } else {
          // NO logic: Show Farewell Message
          ringImage.style.display = 'none';
          resultMessage.textContent = "Aww... That's a huge pain. Wishing you all the best and a happy life ahead. Bye Bye! 😔";
          
          // Play a sad tone
          synth.triggerAttackRelease(["C3", "E2", "G2"], "2n", Tone.now());
          
          // Stop confetti
          confettiCanvas.style.opacity = '0';
        }

        // Show Result Section
        fadeIn(resultSection);
        
      }, 750); // Wait for proposal section to fade out
    }
    
    // Make handleProposal globally accessible
    window.handleProposal = handleProposal;


    // Confetti/responsive on load
    window.onload = function() {
      confettiCanvas.width = window.innerWidth;
      confettiCanvas.height = window.innerHeight;
      window.addEventListener('resize', () => {
        confettiCanvas.width = window.innerWidth;
        confettiCanvas.height = window.innerHeight;
      });
      // Set initial display to none for sections that are hidden
      proposalSection.style.display = 'none';
      resultSection.style.display = 'none';
    };

    // Scratch events
    if (scratchContainer) {
      scratchContainer.addEventListener('mousedown', startScratch);
      document.addEventListener('mouseup', stopScratch);
      scratchContainer.addEventListener('mousemove', scratch);
      scratchContainer.addEventListener('touchstart', startScratch);
      document.addEventListener('touchend', st
