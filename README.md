<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Nosso Amor</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: linear-gradient(to bottom right, #3575b1, #ff9eb6);
      color: white;
      font-family: Arial, sans-serif;
      overflow-x: hidden;
    }

    section {
      width: 100%;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      padding: 20px;
    }

    #boas-vindas {
      background: linear-gradient(to right, #6890bb, #ce6179);
      color: white;
    }

    .glow-button {
      background-color: transparent;
      border: 2px solid #00f7ff;
      color: white;
      padding: 12px 24px;
      border-radius: 12px;
      font-size: 18px;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 8px;
      box-shadow: 0 0 10px #00f7ff, 0 0 20px #00f7ff;
      transition: transform 0.2s, box-shadow 0.3s;
    }

    .glow-button:hover {
      transform: scale(1.05);
      box-shadow: 0 0 15px #22989c, 0 0 30px #398588;
    }

    .glow-button i {
      color: #ebebeb;
    }

    .music-player {
      background: #c9499e;
      padding: 16px;
      border-radius: 16px;
      display: flex;
      align-items: center;
      gap: 16px;
      margin-bottom: 20px;
      width: 90%;
      max-width: 350px;
      box-shadow: 0 0 10px rgba(0,0,0,0.2);
    }

    .music-player img {
      width: 60px;
      height: 60px;
      border-radius: 8px;
      object-fit: cover;
    }

    .music-player .info {
      flex: 1;
      display: flex;
      flex-direction: column;
      gap: 6px;
    }

    .music-player audio {
      width: 100%;
    }

    .carousel {
      position: relative;
      width: 250px;
      height: 400px;
      overflow: hidden;
      border-radius: 16px;
      border: 3px solid white;
      margin: 20px 0;
    }

    .carousel-track {
      display: flex;
      transition: transform 0.5s ease-in-out;
    }

    .carousel-track img {
      width: 250px;
      height: 400px;
      object-fit: cover;
      flex-shrink: 0;
    }

    .carousel-button {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      background-color: rgba(255, 255, 255, 0.3);
      color: white;
      border: none;
      font-size: 14px;
      cursor: pointer;
      padding: 3px 6px;
      border-radius: 50%;
      z-index: 1;
    }

    .carousel-button.left {
      left: 10px;
    }

    .carousel-button.right {
      right: 10px;
    }

    .dots {
      position: absolute;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      gap: 4px;
      z-index: 2;
    }

    .dots span {
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background-color: rgba(255, 255, 255, 0.4);
      transition: background-color 0.3s;
    }

    .dots span.active {
      background-color: white;
    }

    .contador {
      margin-top: 20px;
      text-align: center;
      max-width: 600px;
    }

    .contador i {
      color: red;
    }

    .hearts {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      overflow: hidden;
      z-index: 0;
    }

    .heart {
      position: absolute;
      color: #ff69b4;
      font-size: 20px;
      animation: float 6s linear infinite;
    }

    @keyframes float {
      0% {
        bottom: -10px;
        opacity: 0;
        transform: translateX(0);
      }
      50% {
        opacity: 1;
      }
      100% {
        bottom: 100%;
        transform: translateX(50px);
        opacity: 0;
      }
    }

  </style>
</head>
<body>

  <!-- Tela de Boas-vindas -->
  <section id="boas-vindas">
    <h1>Bem-vinda meu amor ❤️</h1>
    <button class="glow-button" onclick="irParaPrincipal()">
      <i class="fas fa-heart"></i> Entrar
    </button>
  </section>

  <!-- Tela Principal -->
  <section id="principal" style="display:none;">
    <div class="music-player">
      <img src="capa.jpg" alt="Capa da música" />
      <div class="info">
        <strong>Congratulations</strong>
        <span>Bilal</span>
        <small id="statusMusica">⏸️ Pausado</small>
        <audio id="player" controls>
          <source src="congratulations.mp3" type="audio/mp3">
          Seu navegador não suporta áudio HTML5.
        </audio>
      </div>
    </div>

    <div class="carousel">
      <button class="carousel-button left" onclick="mudarFoto(-1)">❮</button>
      <button class="carousel-button right" onclick="mudarFoto(1)">❯</button>
      <div class="carousel-track" id="carouselTrack">
        <img src="fotos/foto1.jpg" />
        <img src="fotos/foto2.jpg" />
        <img src="fotos/foto3.jpg" />
        <img src="fotos/foto4.jpg" />
        <img src="fotos/foto5.jpg" />
        <img src="fotos/foto6.jpg" />
        <img src="fotos/foto7.jpg" />
        <img src="fotos/foto8.jpg" />
        <img src="fotos/foto9.jpg" />
        <img src="fotos/foto10.jpg" />
      </div>
      <div class="dots" id="dots"></div>
    </div>
    
    <div class="contador">
      <p><i class="fas fa-heart"></i> Eu te amo há:</p>
      <p id="tempo"></p>

  
      <!-- MENSAGEM ROMÂNTICA -->
      <div class="mensagem" style="margin-top: 20px; font-size: 18px; max-width: 400px; text-align: center; line-height: 1.6;">
        <p>
          Parabéns, meu amor! 💖<br><br>
          Hoje é mais um daqueles dias em que meu coração se enche de gratidão por ter você ao meu lado. Sua presença ilumina minha vida, e cada momento contigo se torna inesquecível. Obrigado por ser minha inspiração, minha paz e meu abrigo. <br><br>
          Sua companhia é o que dá sentido a cada um dos meus dias. Você é minha melhor escolha, meu maior orgulho e o amor que sempre sonhei. Que essa data se repita por muitos e muitos anos, sempre com sorrisos, cumplicidade e muito amor. <br><br>
          Te amo mais do que palavras podem expressar. 💘<br><br>
          <strong>Eu te amo! ❤️</strong>
        </p>
  
        <p style="margin-top: 20px; font-size: 16px; font-style: italic;">
          "O amor é paciente, o amor é bondoso. Não inveja, não se vangloria, não se orgulha. Tudo sofre, tudo crê, tudo espera, tudo suporta." <br>
          – <strong>1 Coríntios 13:4,7</strong>
        </p>
      </div>
  
      <div class="hearts" id="hearts"></div>
  

      <p style="margin-top: 20px; font-size: 16px; font-style: italic;">
        "O amor é paciente, o amor é bondoso... – <strong>1 Coríntios 13:4,7</strong>"
      </p>
    </div>

    <div class="hearts" id="hearts"></div>
  </section>

  <script>
    function irParaPrincipal() {
      document.getElementById("boas-vindas").style.display = "none";
      document.getElementById("principal").style.display = "flex";

      const audio = document.getElementById("player");
      const statusMusica = document.getElementById("statusMusica");

      audio.play().catch(e => console.log("Autoplay bloqueado:", e));
      audio.addEventListener("play", () => statusMusica.textContent = "🎵 Reproduzindo");
      audio.addEventListener("pause", () => statusMusica.textContent = "⏸️ Pausado");
    }

    const inicio = new Date("2024-11-25T00:00:00");
    function atualizarTempo() {
      const agora = new Date();
      const diff = agora - inicio;
      const dias = Math.floor(diff / (1000 * 60 * 60 * 24));
      const horas = agora.getHours();
      const minutos = agora.getMinutes();
      const segundos = agora.getSeconds();
      document.getElementById("tempo").textContent = `${dias} dias, ${horas} horas, ${minutos} minutos e ${segundos} segundos`;
    }
    setInterval(atualizarTempo, 1000);
    atualizarTempo();

    function criarCoração() {
      const heart = document.createElement("div");
      heart.classList.add("heart");
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.fontSize = Math.random() * 10 + 15 + "px";
      heart.textContent = "💗";
      document.getElementById("hearts").appendChild(heart);
      setTimeout(() => heart.remove(), 6000);
    }
    setInterval(criarCoração, 500);

    // Carrossel
    let fotoAtual = 0;
    const track = document.getElementById("carouselTrack");
    const fotos = track.querySelectorAll("img");
    const dotsContainer = document.getElementById("dots");

    fotos.forEach((_, i) => {
      const dot = document.createElement("span");
      if (i === 0) dot.classList.add("active");
      dotsContainer.appendChild(dot);
    });

    const dots = dotsContainer.querySelectorAll("span");

    function mudarFoto(direcao = 1) {
      dots[fotoAtual].classList.remove("active");
      fotoAtual = (fotoAtual + direcao + fotos.length) % fotos.length;
      dots[fotoAtual].classList.add("active");
      track.style.transform = `translateX(-${fotoAtual * 250}px)`;
    }

    let trocasAutomáticas = 0;
    const maxTrocas = fotos.length;
    const intervalo = setInterval(() => {
      mudarFoto(1);
      trocasAutomáticas++;
      if (trocasAutomáticas >= maxTrocas) {
        clearInterval(intervalo);
      }
    }, 4000);
  </script>
</body>
</html>
