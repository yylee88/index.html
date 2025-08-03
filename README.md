# index.html
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
      background: #f9f5f0;
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
      max-width: 700px;
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
      <button onclick="generateMenu()">Generate My Menu</button>
    </div>

    <div class="menu-output" id="output" style="display: none">
      <h2>🍽️ Your Gourmeet Menu</h2>
      <p><strong>Main Dish:</strong> <span id="dishName"></span></p>
      <p><strong>Theme:</strong> <span id="theme"></span></p>
      <p><strong>Sides:</strong></p>
      <ul id="sides"></ul>
      <p><strong>Drink:</strong> <span id="drink"></span></p>
      <p><strong>Vibe:</strong> <span id="vibe"></span></p>
      <p><strong>Extra Touch:</strong> <span id="extra"></span></p>
    </div>
  </div>

  <footer>
    &copy; 2025 Gourmeet. All rights reserved.
  </footer>

  <script>
    function generateMenu() {
      const dish = document.getElementById('mainDish').value.trim();
      const output = document.getElementById('output');
      const themes = ["Golden Hour Cozy", "Crunch + Chaos", "Quiet Luxury", "Late Night Picnic", "Global Grandma"];
      const sidesSets = [
        ["Lemony green beans", "Garlic roasted potatoes"],
        ["Kimchi slaw", "Scallion pancakes"],
        ["Pear & arugula salad", "Baguette with whipped butter"],
        ["Pickled cucumbers", "Sesame soba noodles"],
        ["Roasted squash", "Butter-glazed carrots"]
      ];
      const drinks = ["Chilled Beaujolais", "Soju spritzer", "Lemon spritz", "Spiced red wine sangria", "Sparkling apple cider"];
      const vibes = ["Candlelight and jazz", "K-pop and fairy lights", "Dinner on the floor", "Old records and warm lighting", "Outdoor with string lights"];
      const extras = ["Serve on mismatched plates", "Napkins folded like animals", "Tiny handwritten menus", "Play a toast game", "Dessert served in mugs"];

      const randomIndex = Math.floor(Math.random() * themes.length);

      document.getElementById('dishName').innerText = dish || "Mystery Dish";
      document.getElementById('theme').innerText = themes[randomIndex];

      const sides = document.getElementById('sides');
      sides.innerHTML = '';
      sidesSets[randomIndex].forEach(side => {
        const li = document.createElement('li');
        li.innerText = side;
        sides.appendChild(li);
      });

      document.getElementById('drink').innerText = drinks[randomIndex];
      document.getElementById('vibe').innerText = vibes[randomIndex];
      document.getElementById('extra').innerText = extras[randomIndex];

      output.style.display = 'block';
    }
  </script>
</body>
</html>
