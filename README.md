<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Birthday, Shayna!</title>
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #fcb1ff, #ffd6ff, #ffecf9);
      margin: 0;
      padding: 0;
      height: 100vh;
      overflow: hidden;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
    }

    /* confetti + flowers container */
    canvas, .flower {
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      pointer-events: none;
      z-index: 1;
    }

    .container {
      z-index: 2;
      background: rgba(255, 255, 255, 0.9);
      padding: 25px;
      border-radius: 20px;
      box-shadow: 0 0 30px rgba(0,0,0,0.1);
      max-width: 800px;
      width: 90%;
      text-align: center;
      animation: fadeIn 1.5s ease-in;
    }

    h1 {
      color: #ff66b3;
      font-size: 2em;
      animation: bounce 2s infinite;
    }

    p {
      font-size: 1.2em;
      color: #444;
      line-height: 1.6;
      animation: fadeText 1s ease-in;
    }

    button {
      background: #ff66b3;
      color: white;
      border: none;
      padding: 12px 25px;
      font-size: 1em;
      border-radius: 8px;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    button:hover {
      background: #ff4081;
      transform: scale(1.05);
    }

    .letter-container {
      z-index: 2;
      background: rgba(255,255,255,0.95);
      padding: 40px;
      border-radius: 15px;
      font-family: 'Brush Script MT', cursive;
      font-size: 1.5em;
      color: #333;
      text-align: left;
      white-space: pre-line;
      display: none;
      animation: fadeIn 1s ease-in;
      max-width: 800px;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.9); }
      to { opacity: 1; transform: scale(1); }
    }

    @keyframes fadeText {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @keyframes bounce {
      0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
      40% { transform: translateY(-10px); }
      60% { transform: translateY(-5px); }
    }

    /* flower petals */
    .flower {
      position: absolute;
      top: -10%;
      animation: fall linear infinite;
      opacity: 0.8;
    }

    @keyframes fall {
      0% { transform: translateY(0) rotate(0deg); opacity: 1; }
      100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
    }
  </style>
</head>
<body>
  <canvas id="confetti"></canvas>
  
  <div class="container" id="main-container">
    <h1 id="slide-title">Haiii Selamat Datang orang imut dan special !,,
💖💕💗</h1>
    <p id="slide-content">Klik tombol di bawah ini yaaa, cantikk 💕 💕 💕</p>
    <button onclick="nextSlide()" id="next-btn">Next</button>
  </div>

  <div class="letter-container" id="letter">
    To my dearest Shayna,  
    aku beruntung banget,  
    aku adalah cowok terberuntung,  
    seeeee alam semesta,  
    kek, gila sih, omayygoatt gituuu,  
    aaaa lucuu bangett dehh  
    intinya, kita lucu, unik, gitu gituu dahh 💖  
    intinya, aku sayang cayna sih intinya,  
    , hehehe cuma bisa ngasih segini
🫡
    — your boyfriend 💞
  </div>

  <script>
    let currentSlide = 0;
    const slides = [
      { title: "Haiii Selamat Datang!", content: "Selamat datang, Shayna! Klik disinii ya! 🌟" },
      { title: "US", content: "liatt siapa inii?! cuma kitaa, dua manusia paling unikk,manusia paling bahagia Cuzz loving each other,yaga yaga,bohong yaa kalau aku bilang gak sayangg Ama kamuu" },
      { title: "Selamat Ulang Tahun!", content: "Happy Birthday, sayangkuhh, my moonshine 🌙, selamat ulangtahun yaaa semoga keinginannya cepat cepat tercapai dan masih terus bareng aku,xixixi" },
      { title: "Sweetheart", content: "Kamu lucu, gaa boong, kamu tuhh ya bener benerr cantikk,kalau dibilang cantik tuhhh percayaa makanyaaa,! ❤️❤️❤️" },
      { title: "Wishhh", content: "Semoga kitaa bisaa terus terusan bareng yahh, semuanya bareng, pokoknya harus tetep bareng teruss gamauu picah🙂‍↔️ dari caynaa iloveyou💖❤️ iloveyou💗💗 caynaa🎉" },
      { title: "Pesan Kecil", content: "Kamu tuhh gausah gimana gimana ya cantik,kamu ga harus jadi sempurna atau gimana just the way you are,dan aku minta maaf sebelumnya jika ada salahhh yaa sayangkuh💖💖💖" },
      { title: "Surat Khusus", content: "Ada surat buat kamu! Klik 'Buka Surat' di bawah.", isLetter: true }
    ];

    function nextSlide() {
      currentSlide = (currentSlide + 1) % slides.length;
      const slide = slides[currentSlide];
      const container = document.getElementById('main-container');
      if (slide.isLetter) {
        container.innerHTML = `
          <div>
            <h1>${slide.title}</h1>
            <p>${slide.content}</p>
            <button onclick="openLetter()">Buka Surat 💌</button>
          </div>
        `;
      } else {
        container.innerHTML = `
          <h1>${slide.title}</h1>
          <p>${slide.content}</p>
          <button onclick="nextSlide()">Next</button>
        `;
      }
    }

    function openLetter() {
      document.getElementById('main-container').style.display = 'none';
      document.getElementById('letter').style.display = 'block';
    }

    // confetti effect
    const canvas = document.getElementById("confetti");
    const ctx = canvas.getContext("2d");
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const confettis = Array.from({ length: 100 }).map(() => ({
      x: Math.random() * canvas.width,
      y: Math.random() * canvas.height,
      r: Math.random() * 6 + 2,
      d: Math.random() * 2 + 1,
      color: `hsl(${Math.random() * 360}, 100%, 70%)`
    }));

    function drawConfetti() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      confettis.forEach(c => {
        ctx.beginPath();
        ctx.arc(c.x, c.y, c.r, 0, Math.PI * 2, false);
        ctx.fillStyle = c.color;
        ctx.fill();
      });
      updateConfetti();
      requestAnimationFrame(drawConfetti);
    }

    function updateConfetti() {
      confettis.forEach(c => {
        c.y += c.d;
        if (c.y > canvas.height) {
          c.y = -10;
          c.x = Math.random() * canvas.width;
        }
      });
    }

    drawConfetti();

    // flower petals fall
    const flowerColors = ['#ffb6c1', '#ffc0cb', '#ff69b4', '#ff1493', '#db7093'];
    for (let i = 0; i < 15; i++) {
      const flower = document.createElement('div');
      flower.classList.add('flower');
      flower.textContent = '🌸';
      flower.style.left = Math.random() * 100 + 'vw';
      flower.style.animationDuration = (5 + Math.random() * 5) + 's';
      flower.style.fontSize = (16 + Math.random() * 16) + 'px';
      document.body.appendChild(flower);
    }
  </script>
</body>
</html>
