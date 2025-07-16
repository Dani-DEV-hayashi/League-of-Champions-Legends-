<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Wild Rift - Portal Gamer</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', sans-serif;
    }

    body {
      background-color: #000;
      color: #fff;
    }

    header {
      background-color: #111;
      padding: 20px;
      text-align: center;
      border-bottom: 2px solid #00ffc3;
    }

    header h1 {
      font-size: 2.5rem;
      color: #00ffc3;
    }

    .akali-highlight {
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      padding: 40px 20px;
      background: linear-gradient(to bottom, #1a1a1a, #000);
    }

    .akali-highlight img {
      width: 100%;
      max-width: 800px;
      border-radius: 20px;
      box-shadow: 0 0 30px #00ffc3;
    }

    .akali-highlight h2 {
      margin-top: 20px;
      font-size: 2rem;
      color: #00ffc3;
    }

    .champion-grid {
      padding: 40px 20px;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 30px;
      background-color: #0a0a0a;
    }

    .champion-card {
      background-color: #111;
      border-radius: 12px;
      overflow: hidden;
      box-shadow: 0 0 15px rgba(0, 255, 195, 0.15);
      transition: transform 0.3s;
    }

    .champion-card:hover {
      transform: scale(1.03);
      box-shadow: 0 0 25px #00ffc3;
    }

    .champion-card img {
      width: 100%;
      height: auto;
      display: block;
    }

    .champion-info {
      padding: 10px 15px;
      text-align: center;
    }

    .champion-info h3 {
      margin-bottom: 5px;
      font-size: 1.2rem;
      color: #00ffc3;
    }

    .champion-info p {
      font-size: 0.95rem;
      color: #ccc;
    }

    footer {
      text-align: center;
      padding: 20px;
      background-color: #111;
      border-top: 2px solid #00ffc3;
      color: #999;
    }
  </style>
</head>
<body>

  <header>
    <h1>Portal Gamer - Wild Rift</h1>
  </header>

  <section class="akali-highlight">
    <img src="https://ddragon.leagueoflegends.com/cdn/img/champion/splash/Akali_0.jpg" alt="Akali destaque">
    <h2>Akali - A Assassina Silenciosa</h2>
  </section>

  <section class="champion-grid" id="champion-grid">
    <!-- Campeões serão carregados aqui via JavaScript -->
  </section>

  <footer>
    &copy; 2025 Portal Gamer | Todos os direitos reservados
  </footer>

  <script>
    async function carregarCampeoes() {
      const resposta = await fetch("https://ddragon.leagueoflegends.com/cdn/13.6.1/data/pt_BR/champion.json");
      const dados = await resposta.json();
      const campeoes = Object.values(dados.data);

      const container = document.getElementById("champion-grid");

      campeoes.forEach((campeao) => {
        const nome = campeao.name;
        const id = campeao.id;
        const descricao = campeao.title;

        const card = document.createElement("div");
        card.className = "champion-card";
        card.innerHTML = `
          <img src="https://ddragon.leagueoflegends.com/cdn/img/champion/splash/${id}_0.jpg" alt="${nome}">
          <div class="champion-info">
            <h3>${nome}</h3>
            <p>${descricao}</p>
          </div>
        `;
        container.appendChild(card);
      });
    }

    carregarCampeoes();
  </script>

</body>
</html>
