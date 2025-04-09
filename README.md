<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Saveurs Dauphinoises</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500&family=Open+Sans&display=swap" rel="stylesheet">
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: 'Open Sans', sans-serif;
      background: #fff;
      color: #333;
      line-height: 1.6;
    }
    header {
      background: url('https://source.unsplash.com/1600x600/?catering,food') center/cover no-repeat;
      height: 60vh;
      color: white;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-shadow: 2px 2px 4px rgba(0,0,0,0.6);
    }
    header h1 {
      font-family: 'Playfair Display', serif;
      font-size: 3rem;
    }
    header p {
      font-size: 1.2rem;
    }
    nav {
      display: flex;
      justify-content: center;
      gap: 2rem;
      background: #f5f5f5;
      padding: 1rem;
    }
    nav a {
      text-decoration: none;
      color: #333;
      font-weight: bold;
    }
    .container {
      max-width: 1000px;
      margin: auto;
      padding: 2rem;
    }
    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 2rem;
    }
    .product {
      border: 1px solid #eee;
      border-radius: 10px;
      padding: 1rem;
      text-align: center;
    }
    .product img {
      width: 100%;
      height: 180px;
      object-fit: cover;
      border-radius: 10px;
    }
    .btn {
      background: #d4af37;
      color: white;
      border: none;
      padding: 0.5rem 1rem;
      margin-top: 0.5rem;
      cursor: pointer;
      border-radius: 5px;
    }
    .cart {
      margin-top: 2rem;
      background: #fafafa;
      padding: 1rem;
      border-radius: 10px;
    }
    footer {
      text-align: center;
      padding: 2rem;
      background: #f8f8f8;
      margin-top: 4rem;
    }
  </style>
</head>
<body>
  <header>
    <h1>Saveurs Dauphinoises</h1>
    <p>Traiteur raffiné à Bourgoin-Jallieu</p>
  </header>

  <nav>
    <a href="#produits">Menu</a>
    <a href="#panier">Panier</a>
    <a href="#contact">Contact</a>
  </nav>

  <div class="container">
    <h2 id="produits">Nos spécialités</h2>
    <div class="products">
      <div class="product">
        <img src="https://source.unsplash.com/300x200/?foie-gras" alt="Foie gras maison">
        <h3>Foie gras maison</h3>
        <p>Préparé avec soin, 200g</p>
        <button class="btn" onclick="addToCart('Foie gras maison')">Ajouter</button>
      </div>
      <div class="product">
        <img src="https://source.unsplash.com/300x200/?buffet,catering" alt="Buffet froid">
        <h3>Buffet froid</h3>
        <p>Idéal pour événements</p>
        <button class="btn" onclick="addToCart('Buffet froid')">Ajouter</button>
      </div>
      <div class="product">
        <img src="https://source.unsplash.com/300x200/?pastry,dessert" alt="Plateau desserts">
        <h3>Plateau desserts</h3>
        <p>Assortiment sucré maison</p>
        <button class="btn" onclick="addToCart('Plateau desserts')">Ajouter</button>
      </div>
    </div>

    <div class="cart" id="panier">
      <h2>Votre panier</h2>
      <ul id="cart-items"></ul>
    </div>
  </div>

  <footer id="contact">
    <p><strong>Saveurs Dauphinoises</strong></p>
    <p>12 rue des Gourmets, 38300 Bourgoin-Jallieu</p>
    <p>Tél : 04 74 00 00 00</p>
    <p>Email : contact@saveursdauphinoises.fr</p>
  </footer>

  <script>
    const cart = [];
    function addToCart(item) {
      cart.push(item);
      renderCart();
    }
    function renderCart() {
      const list = document.getElementById('cart-items');
      list.innerHTML = '';
      const counts = {};
      cart.forEach(i => counts[i] = (counts[i] || 0) + 1);
      for (let item in counts) {
        const li = document.createElement('li');
        li.textContent = `${item} x${counts[item]}`;
        list.appendChild(li);
      }
    }
  </script>
</body>
</html>
