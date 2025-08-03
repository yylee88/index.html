<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Gourmeet | Menu Pairing Made Simple</title>
  <style>
    body {
      font-family: 'Helvetica', sans-serif;
      margin: 0;
      padding: 0;
      background: #fefefe;
      color: #333;
    }
    header {
      background: #fff;
      padding: 2rem;
      text-align: center;
      box-shadow: 0 2px 8px rgba(0,0,0,0.05);
    }
    header h1 {
      font-size: 2.5rem;
      margin-bottom: 0.5rem;
    }
    header p {
      font-size: 1.2rem;
      color: #666;
    }
    .container {
      max-width: 900px;
      margin: 2rem auto;
      padding: 1rem;
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
    }
    button {
      margin-top: 1rem;
      padding: 0.8rem 1.5rem;
      font-size: 1rem;
      background-color: #d2691e;
      color: #fff;
      border: none;
      border-radius: 6px;
      cursor: pointer;
    }
    .menu-output {
      background: #fff;
      border-radius: 8px;
      padding: 1.5rem;
      box-shadow: 0 2px 12px rgba(0,0,0,0.08);
      margin-bottom: 2rem;
    }
    .menu-output h2 {
      margin-top: 0;
    }
    footer {
      text-align: center;
      padding: 2rem;
      font-size: 0.9rem;
      color: #aaa;
    }
    .try-again {
      text-align: center;
      margin-top: 1rem;
    }
    .pdf-link {
      text-align: center;
      margin-top: 1rem;
    }
  </style>
</head>
<body>
  <header>
    <h1>Gourmeet</h1>
    <p>Your main dish just met its match.</p>
  </header>

  <div class="container">
    <div class="input-area">
      <label for="mainDish">What are you making (or craving)?</label><br>
      <input type="text" id="mainDish" placeholder="e.g. Lasagna, Chicken Parmesan, Tofu Stir Fry, Grilled Salmon, Biryani" />
      <br>
      <button onclick="generateMenu()">Generate My Menu</button>
    </div>

    <div id="menu"></div>
  </div>

  <footer>
    &copy; 2025 Gourmeet. All rights reserved.
  </footer>

  <script>
    const dishDatabase = {
      "lasagna": {
        appetizers: [
          { name: "Bruschetta", url: "https://www.simplyrecipes.com/recipes/bruschetta_with_tomato_and_basil/" },
          { name: "Stuffed Mushrooms", url: "https://www.delish.com/cooking/recipe-ideas/a19665918/easy-stuffed-mushrooms-recipe/" }
        ],
        sides: [
          { name: "Caesar Salad", url: "https://www.allrecipes.com/recipe/229063/classic-restaurant-caesar-salad/" },
          { name: "Garlic Bread", url: "https://www.allrecipes.com/recipe/21060/toasted-garlic-bread/" }
        ],
        wine: "Chianti",
        cocktail: "Negroni",
        dessert: { name: "Tiramisu", url: "https://www.allrecipes.com/recipe/21412/tiramisu-ii/" },
        theme: "Rustic Italian Night",
        playlist: { name: "La Dolce Vita", song: "Volare – Dean Martin" },
        icebreaker: "What’s the most unforgettable meal you’ve ever had?",
        pdf: "https://example.com/menus/lasagna.pdf"
      },
      "default": {
        appetizers: [
          { name: "Deviled Eggs", url: "https://www.simplyrecipes.com/recipes/deviled_eggs/" },
          { name: "Caprese Skewers", url: "https://www.loveandlemons.com/caprese-skewers/" }
        ],
        sides: [
          { name: "Roasted Veggies", url: "https://www.loveandlemons.com/roasted-vegetables/" },
          { name: "Wild Rice Pilaf", url: "https://www.allrecipes.com/recipe/222006/wild-rice-pilaf/" }
        ],
        wine: "Pinot Noir",
        cocktail: "Moscow Mule",
        dessert: { name: "Chocolate Lava Cake", url: "https://sallysbakingaddiction.com/molten-chocolate-lava-cakes/" },
        theme: "Cozy Night In",
        playlist: { name: "Mellow Dinner Vibes", song: "Banana Pancakes – Jack Johnson" },
        icebreaker: "If you could share a meal with any historical figure, who would it be?",
        pdf: "https://example.com/menus/default.pdf"
      }
    };

    function generateMenu() {
      const input = document.getElementById("mainDish").value.trim().toLowerCase();
      const container = document.getElementById("menu");
      container.innerHTML = "";

      let data = dishDatabase[input] || dishDatabase["default"];

      const section = document.createElement("div");
      section.className = "menu-output";

      section.innerHTML = `
        <h2>🍽️ Your Gourmeet Menu</h2>
        <p><strong>Main Dish:</strong> ${input || "Mystery Dish"}</p>
        <p><strong>Theme:</strong> ${data.theme}</p>
        <p><strong>Appetizers:</strong></p>
        <ul>
          ${data.appetizers.map(item => `<li><a href="${item.url}" target="_blank">${item.name}</a></li>`).join('')}
        </ul>
        <p><strong>Sides:</strong></p>
        <ul>
          ${data.sides.map(item => `<li><a href="${item.url}" target="_blank">${item.name}</a></li>`).join('')}
        </ul>
        <p><strong>Wine Pairing:</strong> ${data.wine}</p>
        <p><strong>Cocktail Pairing:</strong> ${data.cocktail}</p>
        <p><strong>Dessert:</strong> <a href="${data.dessert.url}" target="_blank">${data.dessert.name}</a></p>
        <p><strong>Playlist Vibe:</strong> ${data.playlist.name} — song suggestion: "${data.playlist.song}"</p>
        <p><strong>Icebreaker Question:</strong> ${data.icebreaker}</p>
        <div class="pdf-link">
          <a href="${data.pdf}" target="_blank">📄 Download Printable Menu (Instagram-ready)</a>
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
