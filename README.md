# index.html
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
    .menu-image {
      width: 100%;
      height: auto;
      margin: 1rem 0;
      border-radius: 8px;
    }
    .try-again {
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
      <input type="text" id="mainDish" placeholder="e.g. Lasagna, Eggplant, Date Night" />
      <br>
      <button onclick="generateMenus()">Generate My Menus</button>
    </div>

    <div id="menus"></div>
  </div>

  <footer>
    &copy; 2025 Gourmeet. All rights reserved.
  </footer>

  <script>
    const themes = ["Golden Hour Cozy", "Crunch + Chaos", "Late Night Picnic"];
    const menusData = [
      {
        sides: [
          { name: "Lemony Green Beans", url: "https://www.seriouseats.com/lemony-green-beans-recipe" },
          { name: "Garlic Roasted Potatoes", url: "https://www.bonappetit.com/recipe/extra-crispy-roast-potatoes" }
        ],
        drink: "Chilled Beaujolais",
        vibe: "Candlelight and jazz",
        extra: "Serve on mismatched plates",
        image: "https://source.unsplash.com/800x400/?dinner-party"
      },
      {
        sides: [
          { name: "Kimchi Slaw", url: "https://www.thekitchn.com/kimchi-slaw-recipe-22946284" },
          { name: "Scallion Pancakes", url: "https://www.seriouseats.com/scallion-pancakes-recipe" }
        ],
        drink: "Soju Spritzer",
        vibe: "K-pop and fairy lights",
        extra: "Play a toast game",
        image: "https://source.unsplash.com/800x400/?korean-food"
      },
      {
        sides: [
          { name: "Tomato Salad with Feta", url: "https://www.bbcgoodfood.com/recipes/tomato-salad-feta" },
          { name: "Grilled Corn on the Cob", url: "https://www.nytimes.com/recipe/1023252/grilled-corn-on-the-cob" }
        ],
        drink: "Sparkling Apple Cider",
        vibe: "Outdoor with string lights",
        extra: "Napkins folded like animals",
        image: "https://source.unsplash.com/800x400/?picnic-food"
      }
    ];

    function generateMenus() {
      const dish = document.getElementById('mainDish').value.trim() || "Mystery Dish";
      const container = document.getElementById('menus');
      container.innerHTML = '';

      menusData.forEach((menu, index) => {
        const section = document.createElement('div');
        section.className = 'menu-output';

        section.innerHTML = `
          <h2>🍽️ Menu Option ${index + 1}</h2>
          <img src="${menu.image}" alt="Menu image" class="menu-image" />
          <p><strong>Main Dish:</strong> ${dish}</p>
          <p><strong>Theme:</strong> ${themes[index]}</p>
          <p><strong>Sides:</strong></p>
          <ul>
            ${menu.sides.map(side => `<li><a href="${side.url}" target="_blank">${side.name}</a></li>`).join('')}
          </ul>
          <p><strong>Drink:</strong> ${menu.drink}</p>
          <p><strong>Vibe:</strong> ${menu.vibe}</p>
          <p><strong>Extra Touch:</strong> ${menu.extra}</p>
          <div class="try-again">
            <button onclick="generateMenus()">Try Again</button>
          </div>
        `;

        container.appendChild(section);
      });
    }
  </script>
</body>
</html>
