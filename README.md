
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Gourmeet | Menu Pairing Made Simple</title>
  <style>
    body {
      font-family: 'Helvetica Neue', sans-serif;
      margin: 0;
      padding: 0;
      background: #f4f4f4;
      color: #333;
    }
    header {
      background: #fff;
      padding: 2rem;
      text-align: center;
      box-shadow: 0 2px 8px rgba(0,0,0,0.05);
    }
    header h1 {
      font-size: 3rem;
      margin-bottom: 0.5rem;
      color: #2c2c2c;
    }
    header p {
      font-size: 1.2rem;
      color: #777;
    }
    .container {
      max-width: 900px;
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
      background-color: #ff5722;
      color: #fff;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      transition: background 0.3s ease;
    }
    button:hover {
      background-color: #e64a19;
    }
    .menu-output img {
      width: 100%;
      max-height: 200px;
      object-fit: cover;
      border-radius: 6px;
      margin-bottom: 1rem;
    }
    .menu-output h2 {
      margin-top: 0;
    }
    .pdf-link, .try-again {
      text-align: center;
      margin-top: 1.5rem;
    }
    .pdf-link a {
      background: #333;
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
    <p>✨ Your main dish just met its match ✨</p>
  </header>

  <div class="container">
    <div class="input-area">
      <label for="mainDish">What's the main dish?</label><br>
      <input type="text" id="mainDish" placeholder="e.g. Lasagna, Salmon, Biryani, Veggie Tacos" />
      <br>
      <button onclick="generateMenu()">Generate Menu</button>
    </div>

    <div id="menu"></div>
  </div>

  <footer>
    &copy; 2025 Gourmeet. All rights reserved.
  </footer>

  <script>
    const dishDatabase = {
      "lasagna": {
        image: "https://source.unsplash.com/800x400/?lasagna",
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
      "salmon": {
        image: "https://source.unsplash.com/800x400/?grilled-salmon",
        appetizers: [
          { name: "Smoked Salmon Dip", url: "https://www.simplyrecipes.com/recipes/smoked_salmon_dip/" },
          { name: "Cucumber Canapés", url: "https://www.loveandlemons.com/cucumber-appetizers/" }
        ],
        sides: [
          { name: "Roasted Asparagus", url: "https://www.loveandlemons.com/roasted-asparagus/" },
          { name: "Herbed Quinoa", url: "https://www.allrecipes.com/recipe/229156/herbed-quinoa/" }
        ],
        wine: "Sauvignon Blanc",
        cocktail: "French 75",
        dessert: { name: "Lemon Tart", url: "https://www.delish.com/uk/cooking/recipes/a31073634/easy-lemon-tart-recipe/" },
        theme: "Seaside Bistro",
        playlist: { name: "Chill Coastal", song: "Come Away With Me – Norah Jones" },
        icebreaker: "What's your go-to comfort dish when you're sad or sick?",
        pdf: "https://example.com/menus/salmon.pdf"
      },
      "default": {
        image: "https://source.unsplash.com/800x400/?dinner",
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
        <img src="${data.image}" alt="Dish Image" />
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
        <p><strong>Playlist Vibe:</strong> ${data.playlist.name} — Song: "${data.playlist.song}"</p>
        <p><strong>Icebreaker Question:</strong> ${data.icebreaker}</p>
        <div class="pdf-link">
          <a href="${data.pdf}" target="_blank">📄 Download Printable Menu</a>
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
