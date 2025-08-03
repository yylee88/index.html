<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
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
    <p>Your main dish has met its match</p>
  </header>

  <div class="container">
    <div class="input-area">
      <label for="mainDish">What are you making?</label><br>
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
      const input = document.getElementById("mainDish").value.trim().toLowerCase();
      const container = document.getElementById("menu");
      container.innerHTML = "";

      if (!input) return;

      // Curate menu details based on keywords in the dish
      let theme = "";
      let wine = "";
      let cocktail = "";
      let playlist = "";
      let song = "";
      let wildcard = "";
      let appetizers = [];
      let sides = [];
      let dessert = {};

      if (input.includes("tofu") || input.includes("noodle")) {
        theme = "K-town nostalgia with Brooklyn playlists";
        wine = "Orange pét-nat";
        cocktail = "Yuzu spritz with Korean pear";
        playlist = "Leftfield Korean disco + weird TikTok beats";
        song = "Bubble Pop! – HyunA";
        appetizers = [
          { name: "Kimchi deviled eggs", url: "https://www.bonappetit.com/recipe/kimchi-deviled-eggs" },
          { name: "Crispy rice with spicy tuna", url: "https://www.delish.com/cooking/recipe-ideas/a35874134/spicy-tuna-crispy-rice-recipe/" }
        ];
        sides = [
          { name: "Scallion pancakes with soy drizzle", url: "https://thewoksoflife.com/chinese-scallion-pancakes-cong-you-bing/" },
          { name: "Charred shishitos with lemon salt", url: "https://www.loveandlemons.com/shishito-peppers/" }
        ];
        dessert = { name: "Miso caramel brownies", url: "https://www.bonappetit.com/recipe/miso-caramel-brownies" };
        wildcard = "Bonus: everyone gets a mini tube of spicy gochujang lip gloss as a party favor.";
      } else if (input.includes("duck") || input.includes("pork")) {
        theme = "A smoky dinner in your best outfit (even if barefoot)";
        wine = "Funky chilled Beaujolais";
        cocktail = "Smoked mezcal + fig bitters";
        playlist = "Vinyl-only dinner with obscure ‘70s post-funk";
        song = "Les Fleur – Minnie Riperton";
        appetizers = [
          { name: "Pickled fennel and fig toast", url: "https://www.thekitchn.com/recipe-fig-and-fennel-crostini-173963" },
          { name: "Duck liver mousse on rye crisps", url: "https://www.seriouseats.com/duck-liver-mousse-crostini-recipe" }
        ];
        sides = [
          { name: "Roasted beet salad with hazelnut", url: "https://www.bonappetit.com/recipe/beets-with-pistachios-and-orange" },
          { name: "Spiced roasted squash", url: "https://www.loveandlemons.com/roasted-squash/" }
        ];
        dessert = { name: "Dark chocolate tart with sea salt", url: "https://www.bonappetit.com/recipe/salted-dark-chocolate-tart" };
        wildcard = "Someone at the table must perform a dramatic reading of a Yelp review from 2011.";
      } else {
        theme = "Accidental supper club in a living room with too many plants";
        wine = "Chenin blanc, slightly off-dry";
        cocktail = "Grapefruit rosemary gin fizz";
        playlist = "Soft synths, jazz breaks, and random Sade remixes";
        song = "Smooth Operator – Sade";
        appetizers = [
          { name: "Marinated white beans with lemon zest", url: "https://www.loveandlemons.com/marinated-white-beans/" },
          { name: "Crackers with whipped feta & aleppo pepper", url: "https://www.bonappetit.com/recipe/whipped-feta-with-sesame-and-sumac" }
        ];
        sides = [
          { name: "Crispy smashed potatoes with labneh", url: "https://www.bonappetit.com/recipe/smashed-potatoes-with-labneh-and-crunchy-garlic" },
          { name: "Blistered green beans with anchovy butter", url: "https://www.seriouseats.com/charred-green-beans-with-anchovy-dressing" }
        ];
        dessert = { name: "Cardamom olive oil cake", url: "https://www.themediterraneandish.com/olive-oil-cake/" };
        wildcard = "Include one dish that must be eaten with your hands — no explanation allowed.";
      }

      const mainLink = `https://www.google.com/search?q=${encodeURIComponent(input + " recipe")}`;
      const section = document.createElement("div");
      section.className = "menu-output";

      section.innerHTML = `
        <h2><a href="${mainLink}" target="_blank">${input}</a></h2>
        <p><strong>Theme:</strong> ${theme}</p>
        <p><strong>Appetizers:</strong></p>
        <ul>
          ${appetizers.map(item => `<li><a href="${item.url}" target="_blank">${item.name}</a></li>`).join('')}
        </ul>
        <p><strong>Sides:</strong></p>
        <ul>
          ${sides.map(item => `<li><a href="${item.url}" target="_blank">${item.name}</a></li>`).join('')}
        </ul>
        <p><strong>Wine:</strong> ${wine}</p>
        <p><strong>Cocktail:</strong> ${cocktail}</p>
        <p><strong>Dessert:</strong> <a href="${dessert.url}" target="_blank">${dessert.name}</a></p>
        <p><strong>Song Pairing:</strong> <a href="https://open.spotify.com/search/${encodeURIComponent(song)}" target="_blank">${song}</a></p>
        <p><strong>Icebreaker:</strong> ${"What’s your most chaotic food habit or ritual?"}</p>
        <p><strong>Wildcard:</strong> ${wildcard}</p>
        <div class="pdf-link">
          <a href="#" onclick="window.print()">📄 Print Menu</a>
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
