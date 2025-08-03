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
    const menus = [
      {
        main: "Whole Cambodian-style fish with lemongrass & lime",
        appetizers: ["Cured radish with chili oil drizzle", "Charred okra skewers with smoked salt"],
        sides: ["Sticky coconut rice", "Pickled papaya & shallot salad"],
        wine: "Skin-contact Riesling from Finger Lakes",
        cocktail: "Makrut gimlet on crushed ice",
        dessert: "Salted palm sugar flan",
        theme: "Back-alley market meets art gallery",
        playlist: "Obscure disco edits from São Paulo + a rogue Addison Rae track",
        song: "Do You Wanna Funk – Sylvester",
        icebreaker: "What’s the weirdest meal you’ve ever loved more than you expected?",
        pdf: "https://example.com/menu-cambodian-fish.pdf"
      },
      {
        main: "Crispy smashed fingerlings with chili crisp & labneh",
        appetizers: ["Marinated Castelvetrano olives with fennel pollen", "Spoonfuls of lemony whipped ricotta"],
        sides: ["Charred cabbage with anchovy vinaigrette", "Crunchy Persian cucumber salad"],
        wine: "Chilled red from Sicily",
        cocktail: "Shiso mezcal sour",
        dessert: "Burnt honey semifreddo",
        theme: "Natural wine & no shoes",
        playlist: "Japanese city pop and minimal techno",
        song: "Plastic Love – Mariya Takeuchi",
        icebreaker: "What’s one food hill you’d die on (like cilantro is trash)?",
        pdf: "https://example.com/menu-smashed-fingerlings.pdf"
      },
      {
        main: "Korean soy-braised short ribs (galbi jjim)",
        appetizers: ["Shredded scallion pancakes", "Soy-pickled quail eggs"],
        sides: ["Jujube & daikon broth", "Charred shishitos with sesame oil"],
        wine: "Light Burgundy or Lambrusco",
        cocktail: "Black sesame old fashioned",
        dessert: "Hojicha panna cotta",
        theme: "Concrete floors, warm light, someone brought incense",
        playlist: "K-indie deep cuts meets '90s house",
        song: "Everybody Be Somebody – Ruffneck",
        icebreaker: "If your soul had a signature dish, what would it be?",
        pdf: "https://example.com/menu-galbi.pdf"
      }
    ];

    function generateMenu() {
      const input = document.getElementById("mainDish").value.trim();
      const container = document.getElementById("menu");
      container.innerHTML = "";

      const menu = menus[Math.floor(Math.random() * menus.length)];

      const section = document.createElement("div");
      section.className = "menu-output";

      section.innerHTML = `
        <h2>${menu.main}</h2>
        <p><strong>Theme:</strong> ${menu.theme}</p>
        <p><strong>Appetizers:</strong></p>
        <ul>${menu.appetizers.map(item => `<li>${item}</li>`).join('')}</ul>
        <p><strong>Sides:</strong></p>
        <ul>${menu.sides.map(item => `<li>${item}</li>`).join('')}</ul>
        <p><strong>Wine:</strong> ${menu.wine}</p>
        <p><strong>Cocktail:</strong> ${menu.cocktail}</p>
        <p><strong>Dessert:</strong> ${menu.dessert}</p>
        <p><strong>Playlist:</strong> ${menu.playlist} <em>– play "${menu.song}"</em></p>
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
