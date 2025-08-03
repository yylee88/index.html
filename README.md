<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Gourmeet | Menu Pairing Made Beautiful</title>
  <style>
    body {
      font-family: 'Helvetica Neue', sans-serif;
      margin: 0;
      padding: 0;
      background: #f4f4f4;
      color: #222;
    }
    header {
      background: #fff;
      padding: 2rem;
      text-align: center;
      box-shadow: 0 2px 8px rgba(0,0,0,0.05);
    }
    header h1 {
      font-size: 2.8rem;
      margin-bottom: 0.3rem;
      color: #1a1a1a;
    }
    header p {
      font-size: 1rem;
      color: #666;
    }
    .container {
      max-width: 700px;
      margin: 2rem auto;
      padding: 1rem;
      background: #fff;
      border-radius: 8px;
      box-shadow: 0 2px 12px rgba(0,0,0,0.05);
    }
    .input-area {
      margin-bottom: 2rem;
      text-align: center;
    }
    input[type="text"] {
      width: 80%;
      padding: 0.8rem;
      font-size: 1rem;
      border: 1px solid #ccc;
      border-radius: 6px;
      margin-top: 0.5rem;
    }
    button {
      margin-top: 1rem;
      padding: 0.8rem 1.5rem;
      font-size: 1rem;
      background-color: #111;
      color: #fff;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      transition: background 0.3s ease;
    }
    button:hover {
      background-color: #444;
    }
    .menu-output h2 {
      font-size: 2rem;
      font-weight: 500;
      margin-bottom: 0.5rem;
    }
    .menu-output ul {
      list-style: none;
      padding-left: 1rem;
    }
    .menu-output ul li {
      margin-bottom: 0.5rem;
    }
    .pdf-link, .try-again {
      text-align: center;
      margin-top: 1.5rem;
    }
    .pdf-link a {
      background: #000;
      color: #fff;
      padding: 0.6rem 1.2rem;
      border-radius: 5px;
      text-decoration: none;
    }
    footer {
      text-align: center;
      padding: 2rem;
      font-size: 0.9rem;
      color: #aaa;
    }
  </style>
</head>
<body>
  <header>
    <h1>Gourmeet</h1>
    <p>Modern menus, curated by taste</p>
  </header>

  <div class="container">
    <div class="input-area">
      <label for="mainDish">What's your anchor dish or craving?</label><br>
      <input type="text" id="mainDish" placeholder="e.g. crispy tofu, roasted duck, spicy noodles" />
      <br>
      <button onclick="generateMenu()">Curate My Menu</button>
    </div>

    <div id="menu"></div>
  </div>

  <footer>
    &copy; 2025 Gourmeet. All menus born of appetite, culture & chaos.
  </footer>

  <script>
    function generateMenu() {
      const input = document.getElementById("mainDish").value.trim();
      const container = document.getElementById("menu");
      container.innerHTML = "";

      if (!input) return;

      const menu = {
        main: input,
        mainLink: "https://www.google.com/search?q=" + encodeURIComponent(input + " recipe"),
        appetizers: [
          { name: "Pickled turnips with mustard seed", url: "https://www.seriouseats.com/pickled-turnips-recipe" },
          { name: "Crispy shallots on labneh", url: "https://www.bonappetit.com/recipe/labneh-with-quick-pickles-and-crispy-shallots" }
        ],
        sides: [
          { name: "Spiced lentils with preserved lemon", url: "https://www.nytimes.com/recipe/1021980/spiced-lentils" },
          { name: "Charred broccolini with anchovy oil", url: "https://www.epicurious.com/recipes/food/views/charred-broccolini-with-anchovy-dressing" }
        ],
        wine: "A chilled Gamay with high acid",
        cocktail: "Basil-cilantro mezcal margarita",
        dessert: { name: "Olive oil cake with fennel pollen", url: "https://www.loveandlemons.com/olive-oil-cake/" },
        theme: "Studio dinner in a converted print shop",
        song: "Fade to Grey – Visage",
        songLink: "https://open.spotify.com/track/4tkgz64N2fddIsCgd5Z0us",
        icebreaker: "What food trend would you bring back or cancel forever?",
        pdf: "https://example.com/menu-curated.pdf"
      };

      const section = document.createElement("div");
      section.className = "menu-output";

      section.innerHTML = `
        <h2><a href="${menu.mainLink}" target="_blank">${menu.main}</a></h2>
        <p><strong>Theme:</strong> ${menu.theme}</p>
        <p><strong>Appetizers:</strong></p>
        <ul>
          ${menu.appetizers.map(item => `<li><a href="${item.url}" target="_blank">${item.name}</a></li>`).join('')}
        </ul>
        <p><strong>Sides:</strong></p>
        <ul>
          ${menu.sides.map(item => `<li><a href="${item.url}" target="_blank">${item.name}</a></li>`).join('')}
        </ul>
        <p><strong>Wine:</strong> ${menu.wine}</p>
        <p><strong>Cocktail:</strong> ${menu.cocktail}</p>
        <p><strong>Dessert:</strong> <a href="${menu.dessert.url}" target="_blank">${menu.dessert.name}</a></p>
        <p><strong>Song Pairing:</strong> <a href="${menu.songLink}" target="_blank">${menu.song}</a></p>
        <p><strong>Icebreaker:</strong> ${menu.icebreaker}</p>
        <div class="pdf-link">
          <a href="${menu.pdf}" target="_blank">📄 Download Printable Menu</a>
        </div>
        <div class="try-again">
          <button onclick="generateMenu()">Try Again</button>
        </div>
      `;

      container.appendChild(section);
    }
  </script>
</body>
</html>
