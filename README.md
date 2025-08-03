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
      <input type="text" id="mainDish" placeholder="e.g. Lasagna, Chicken Parmesan, Tofu Stir Fry" />
      <br>
      <button onclick="generateMenus()">Generate My Menus</button>
    </div>

    <div id="menus"></div>
  </div>

  <footer>
    &copy; 2025 Gourmeet. All rights reserved.
  </footer>

  <script>
    const menuSuggestions = {
      "lasagna": [
        { name: "Garlic Bread", url: "https://www.allrecipes.com/recipe/21060/toasted-garlic-bread/" },
        { name: "Caesar Salad", url: "https://www.allrecipes.com/recipe/229063/classic-restaurant-caesar-salad/" }
      ],
      "chicken parmesan": [
        { name: "Spaghetti Aglio e Olio", url: "https://www.allrecipes.com/recipe/222000/spaghetti-aglio-e-olio/" },
        { name: "Italian Roasted Vegetables", url: "https://www.allrecipes.com/recipe/214931/roasted-vegetables/" }
      ],
      "tofu stir fry": [
        { name: "Steamed Jasmine Rice", url: "https://www.allrecipes.com/recipe/262856/jasmine-rice/" },
        { name: "Asian Cucumber Salad", url: "https://www.allrecipes.com/recipe/222106/asian-cucumber-salad/" }
      ],
      "default": [
        { name: "Simple Green Salad", url: "https://www.allrecipes.com/recipe/14469/jamies-cranberry-spinach-salad/" },
        { name: "Roasted Potatoes", url: "https://www.allrecipes.com/recipe/220520/roasted-red-potatoes/" }
      ]
    };

    function generateMenus() {
      const input = document.getElementById("mainDish").value.trim().toLowerCase();
      const container = document.getElementById("menus");
      container.innerHTML = "";

      let suggestions = menuSuggestions[input] || menuSuggestions["default"];

      for (let i = 0; i < 3; i++) {
        const section = document.createElement("div");
        section.className = "menu-output";

        section.innerHTML = `
          <h2>🍽️ Menu Option ${i + 1}</h2>
          <p><strong>Main Dish:</strong> ${input || "Mystery Dish"}</p>
          <p><strong>Suggested Sides:</strong></p>
          <ul>
            ${suggestions.map(side => `<li><a href="${side.url}" target="_blank">${side.name}</a></li>`).join("")}
          </ul>
          <div class="try-again">
            <button onclick="generateMenus()">Try Again</button>
          </div>
        `;

        container.appendChild(section);
      }
    }
  </script>
</body>
</html>
