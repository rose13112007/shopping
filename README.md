<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ShopEasy Premium</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }

    body {
      background: linear-gradient(135deg, #4facfe, #00f2fe);
      min-height: 100vh;
    }

    header {
      background: rgba(13, 71, 161, 0.95);
      color: white;
      padding: 20px;
      text-align: center;
      font-size: 30px;
      font-weight: bold;
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
      position: sticky;
      top: 0;
      z-index: 1000;
    }

    .top-bar {
      display: flex;
      justify-content: center;
      gap: 15px;
      flex-wrap: wrap;
      padding: 20px;
    }

    .top-bar input, .top-bar select {
      padding: 12px;
      border: none;
      border-radius: 10px;
      width: 250px;
      font-size: 16px;
      outline: none;
    }

    .container {
      display: flex;
      gap: 20px;
      padding: 20px;
    }

    .products-section {
      flex: 3;
    }

    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 20px;
    }

    .card {
      background: white;
      border-radius: 15px;
      overflow: hidden;
      box-shadow: 0 6px 15px rgba(0,0,0,0.2);
      transition: 0.3s;
    }

    .card:hover {
      transform: translateY(-8px);
    }

    .card img {
      width: 100%;
      height: 220px;
      object-fit: cover;
    }

    .card-content {
      padding: 15px;
      text-align: center;
    }

    .card h3 {
      color: #0d47a1;
      margin-bottom: 8px;
    }

    .card p {
      margin: 5px 0;
      color: #333;
    }

    .price {
      font-size: 20px;
      font-weight: bold;
      color: #1565c0;
    }

    .card button {
      margin-top: 10px;
      padding: 10px 15px;
      border: none;
      background: #0d47a1;
      color: white;
      border-radius: 8px;
      cursor: pointer;
      transition: 0.3s;
    }

    .card button:hover {
      background: #1565c0;
    }

    .cart {
      flex: 1;
      background: white;
      border-radius: 15px;
      padding: 20px;
      height: fit-content;
      box-shadow: 0 6px 15px rgba(0,0,0,0.25);
      position: sticky;
      top: 100px;
    }

    .cart h2 {
      text-align: center;
      color: #0d47a1;
      margin-bottom: 15px;
    }

    .cart-item {
      border-bottom: 1px solid #ddd;
      padding: 10px 0;
    }

    .cart-item button {
      margin-top: 5px;
      padding: 6px 10px;
      border: none;
      background: crimson;
      color: white;
      border-radius: 6px;
      cursor: pointer;
    }

    .total {
      margin-top: 15px;
      font-size: 20px;
      font-weight: bold;
      text-align: center;
      color: #0d47a1;
    }

    .checkout-btn {
      width: 100%;
      margin-top: 15px;
      padding: 12px;
      border: none;
      background: green;
      color: white;
      font-size: 16px;
      border-radius: 8px;
      cursor: pointer;
    }

    .checkout-btn:hover {
      background: darkgreen;
    }

    @media (max-width: 900px) {
      .container {
        flex-direction: column;
      }

      .cart {
        position: static;
      }
    }
  </style>
</head>
<body>
  <header>🛒 ShopEasy Premium Shopping Website</header>

  <div class="top-bar">
    <input type="text" id="searchInput" placeholder="Search products..." onkeyup="filterProducts()" />
    <select id="categoryFilter" onchange="filterProducts()">
      <option value="All">All Categories</option>
      <option value="Fashion">Fashion</option>
      <option value="Accessories">Accessories</option>
      <option value="Electronics">Electronics</option>
    </select>
  </div>

  <div class="container">
    <div class="products-section">
      <div class="products" id="productList"></div>
    </div>

    <div class="cart">
      <h2>Cart</h2>
      <div id="cartItems"></div>
      <div class="total">Total: ₹<span id="total">0</span></div>
      <button class="checkout-btn" onclick="checkout()">Checkout</button>
    </div>
  </div>

  <script>
    const products = [
      {
        name: "Running Shoes",
        price: 1200,
        category: "Fashion",
        img: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?auto=format&fit=crop&w=500&q=80"
      },
      {
        name: "Luxury Watch",
        price: 1800,
        category: "Accessories",
        img: "https://images.unsplash.com/photo-1523170335258-f5ed11844a49?auto=format&fit=crop&w=500&q=80"
      },
      {
        name
