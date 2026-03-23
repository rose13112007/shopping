<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>DressLux - Online Dress Ordering</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      scroll-behavior: smooth;
      font-family: Arial, sans-serif;
    }

    body {
      background: #f8f5f9;
      color: #222;
    }

    header {
      background: linear-gradient(135deg, #8e24aa, #d81b60);
      color: white;
      padding: 18px 40px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: sticky;
      top: 0;
      z-index: 1000;
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
    }

    header h1 {
      font-size: 28px;
      letter-spacing: 1px;
    }

    nav ul {
      display: flex;
      list-style: none;
      gap: 18px;
      flex-wrap: wrap;
    }

    nav ul li a {
      text-decoration: none;
      color: white;
      font-weight: bold;
      transition: 0.3s;
    }

    nav ul li a:hover {
      color: #ffe082;
    }

    .hero {
      min-height: 90vh;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      color: white;
      background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)),
        url('https://images.unsplash.com/photo-1496747611176-843222e1e57c?auto=format&fit=crop&w=1400&q=80') center/cover no-repeat;
      padding: 30px;
    }

    .hero-content {
      max-width: 800px;
      background: rgba(0,0,0,0.35);
      padding: 30px;
      border-radius: 15px;
    }

    .hero h2 {
      font-size: 48px;
      margin-bottom: 15px;
    }

    .hero p {
      font-size: 20px;
      margin-bottom: 20px;
    }

    .hero button {
      background: #ffca28;
      color: #222;
      border: none;
      padding: 14px 28px;
      border-radius: 30px;
      font-size: 18px;
      cursor: pointer;
      font-weight: bold;
      transition: 0.3s;
    }

    .hero button:hover {
      background: #ffd54f;
      transform: scale(1.05);
    }

    .section-title {
      text-align: center;
      padding: 40px 20px 20px;
      font-size: 32px;
      color: #8e24aa;
    }

    .controls {
      width: 90%;
      margin: 20px auto;
      display: flex;
      gap: 15px;
      flex-wrap: wrap;
      justify-content: center;
    }

    .controls input, .controls select {
      padding: 12px;
      border-radius: 8px;
      border: 1px solid #bbb;
      min-width: 220px;
      font-size: 16px;
    }

    .products {
      width: 92%;
      margin: 30px auto;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 25px;
    }

    .card {
      background: white;
      border-radius: 16px;
      overflow: hidden;
      box-shadow: 0 6px 18px rgba(0,0,0,0.12);
      transition: 0.3s;
    }

    .card:hover {
      transform: translateY(-8px);
    }

    .card img {
      width: 100%;
      height: 320px;
      object-fit: cover;
    }

    .card-content {
      padding: 18px;
    }

    .card-content h3 {
      margin-bottom: 10px;
      color: #d81b60;
    }

    .price {
      font-size: 20px;
      color: #2e7d32;
      margin-bottom: 10px;
      font-weight: bold;
    }

    .desc {
      font-size: 14px;
      color: #555;
      margin-bottom: 12px;
      min-height: 45px;
    }

    .card-content select,
    .card-content input {
      width: 100%;
      padding: 10px;
      margin: 7px 0;
      border-radius: 8px;
      border: 1px solid #ccc;
    }

    .card-content button {
      width: 100%;
      padding: 12px;
      background: linear-gradient(135deg, #8e24aa, #d81b60);
      color: white;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      font-size: 16px;
      font-weight: bold;
      transition: 0.3s;
    }

    .card-content button:hover {
      opacity: 0.9;
    }

    .cart-section {
      width: 92%;
      margin: 50px auto;
      background: white;
      border-radius: 18px;
      padding: 25px;
      box-shadow: 0 6px 20px rgba(0,0,0,0.12);
    }

    .cart-section h2 {
      color: #8e24aa;
      margin-bottom: 20px;
      text-align: center;
    }

    .cart-items {
      display: grid;
      gap: 15px;
    }

    .cart-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: #fce4ec;
      padding: 15px;
      border-radius: 12px;
      gap: 15px;
      flex-wrap: wrap;
    }

    .cart-item button {
      background: #c62828;
      color: white;
      border: none;
      padding: 8px 14px;
      border-radius: 8px;
      cursor: pointer;
    }

    .total {
      margin-top: 20px;
      text-align: right;
      font-size: 24px;
      font-weight: bold;
      color: #2e7d32;
    }

    .checkout-btn {
      margin-top: 20px;
      width: 100%;
      padding: 15px;
      font-size: 18px;
      border: none;
      background: #2e7d32;
      color: white;
      border-radius: 12px;
      cursor: pointer;
      font-weight: bold;
    }

    .checkout-btn:hover {
      background: #1b5e20;
    }

    .about, .contact, .offers {
      width: 92%;
      margin: 40px auto;
      background: white;
      padding: 30px;
      border-radius: 16px;
      box-shadow: 0 6px 18px rgba(0,0,0,0.08);
    }

    footer {
      background: #4a148c;
      color: white;
      text-align: center;
      padding: 25px;
      margin-top: 40px;
    }

    @media (max-width: 768px) {
      header {
        flex-direction: column;
        gap: 10px;
        padding: 18px;
      }

      .hero h2 {
        font-size: 32px;
      }

      .hero p {
        font-size: 17px;
      }
    }
  </style>
</head>
<body>

  <header>
    <h1>DressLux</h1>
    <nav>
      <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#shop">Shop</a></li>
        <li><a href="#new">New Arrivals</a></li>
        <li><a href="#party">Party Wear</a></li>
        <li><a href="#casual">Casual</a></li>
        <li><a href="#traditional">Traditional</a></li>
        <li><a href="#western">Western</a></li>
        <li><a href="#bridal">Bridal</a></li>
        <li><a href="#offers">Offers</a></li>
        <li><a href="#cart">Cart</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <section class="hero" id="home">
    <div class="hero-content">
      <h2>Elegant Dress Ordering Website</h2>
      <p>Choose your dream dress from our latest collections and place your order instantly.</p>
      <button onclick="document.getElementById('shop').scrollIntoView()">Shop Now</button>
    </div>
  </section>

  <h2 class="section-title" id="shop">Our Dress Collection</h2>

  <div class="controls">
    <input type="text" id="searchInput" placeholder="Search for dresses..." onkeyup="renderProducts()">
    <select id="categoryFilter" onchange="renderProducts()">
      <option value="all">All Categories</option>
      <option value="Party Wear">Party Wear</option>
      <option value="Casual">Casual</option>
      <option value="Traditional">Traditional</option>
      <option value="Western">Western</option>
      <option value="Bridal">Bridal</option>
    </select>
  </div>

  <section class="products" id="productContainer"></section>

  <section class="offers" id="offers">
    <h2>Special Offers</h2>
    <p>Get up to 30% discount on bridal collections and 20% on selected party wear dresses.</p>
  </section>

  <section class="cart-section" id="cart">
    <h2>Your Cart</h2>
    <div class="cart-items" id="cartItems"></div>
    <div class="total" id="cartTotal">Total: ₹0</div>
    <button class="checkout-btn" onclick="checkout()">Place Order</button>
  </section>

  <section class="about" id="about">
    <h2>About DressLux</h2>
    <p>DressLux is an online fashion ordering website designed for customers to explore premium dresses with beautiful design, size options, and easy ordering functionality.</p>
  </section>

  <section class="contact" id="contact">
    <h2>Contact Us</h2>
    <p>Email: support@dresslux.com</p>
    <p>Phone: +91 98765 43210</p>
    <p>Address: Chennai, Tamil Nadu, India</p>
  </section>

  <footer>
    <p>© 2026 DressLux. All Rights Reserved.</p>
  </footer>

  <script>
    const products = [
      {
        id: 1,
        name: "Royal Bridal Gown",
        category: "Bridal",
        price: 5999,
        image: "https://images.unsplash.com/photo-1524504388940-b1c1722653e1?auto=format&fit=crop&w=800&q=80",
        desc: "Luxury bridal gown with elegant embroidery."
      },
      {
        id: 2,
        name: "Pink Party Dress",
        category: "Party Wear",
        price: 2499,
        image: "https://images.unsplash.com/photo-1515886657613-9f3515b0c78f?auto=format&fit=crop&w=800&q=80",
        desc: "Stylish pink dress perfect for parties."
      },
      {
        id: 3,
        name: "Casual Summer Dress",
        category: "Casual",
        price: 1499,
        image: "https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?auto=format&fit=crop&w=800&q=80",
        desc: "Comfortable summer casual outfit."
      },
      {
        id: 4,
        name: "Traditional Saree Style Dress",
        category: "Traditional",
        price: 2999,
        image: "https://images.unsplash.com/photo-1610030469983-98e550d6193c?auto=format&fit=crop&w=800&q=80",
        desc: "Traditional wear with ethnic elegance."
      },
      {
        id: 5,
        name: "Modern Western Outfit",
        category: "Western",
        price: 1999,
        image: "https://images.unsplash.com/photo-1496747611176-843222e1e57c?auto=format&fit=crop&w=800&q=80",
        desc: "Trendy western style for modern women."
      },
      {
        id: 6,
        name: "Blue Evening Gown",
        category: "Party Wear",
        price: 3299,
        image: "https://images.unsplash.com/photo-1483985988355-763728e1935b?auto=format&fit=crop&w=800&q=80",
        desc: "Elegant evening gown for special occasions."
      },
      {
        id: 7,
        name: "Floral Casual Dress",
        category: "Casual",
        price: 1799,
        image: "https://images.unsplash.com/photo-1487412720507-e7ab37603c6f?auto=format&fit=crop&w=800&q=80",
        desc: "Soft floral print casual wear."
      },
      {
        id: 8,
        name: "Designer Lehenga",
        category: "Traditional",
        price: 4599,
        image: "https://images.unsplash.com/photo-1583391733981-849d6f1c0e30?auto=format&fit=crop&w=800&q=80",
        desc: "Beautiful lehenga with premium design."
      },
      {
        id: 9,
        name: "Black Western Dress",
        category: "Western",
        price: 2199,
        image: "https://images.unsplash.com/photo-1495385794356-15371f348c31?auto=format&fit=crop&w=800&q=80",
        desc: "Classic black western wear outfit."
      },
      {
        id: 10,
        name: "Luxury Wedding Dress",
        category: "Bridal",
        price: 6999,
        image: "https://images.unsplash.com/photo-1512436991641-6745cdb1723f?auto=format&fit=crop&w=800&q=80",
        desc: "Premium wedding dress with luxury finish."
      },
      {
        id: 11,
        name: "Golden Party Dress",
        category: "Party Wear",
        price: 2899,
        image: "https://images.unsplash.com/photo-1529139574466-a303027c1d8b?auto=format&fit=crop&w=800&q=80",
        desc: "Shiny golden party wear for special nights."
      },
      {
        id: 12,
        name: "Classic Kurti Set",
        category: "Traditional",
        price: 1899,
        image: "https://images.unsplash.com/photo-1603252109303-2751441dd157?auto=format&fit=crop&w=800&q=80",
        desc: "Comfortable and stylish ethnic kurti set."
      }
    ];

    let cart = JSON.parse(localStorage.getItem("dressCart")) || [];

    function renderProducts() {
      const container = document.getElementById("productContainer");
      const search = document.getElementById("searchInput").value.toLowerCase();
      const category = document.getElementById("categoryFilter").value;

      const filtered = products.filter(product => {
        const matchSearch = product.name.toLowerCase().includes(search) || product.category.toLowerCase().includes(search);
        const matchCategory = category === "all" || product.category === category;
        return matchSearch && matchCategory;
      });

      container.innerHTML = filtered.map(product => `
        <div class="card">
          <img src="${product.image}" alt="${product.name}">
          <div class="card-content">
            <h3>${product.name}</h3>
            <div class="price">₹${product.price}</div>
            <div class="desc">${product.desc}</div>
            <select id="size-${product.id}">
              <option value="S">Size S</option>
              <option value="M">Size M</option>
              <option value="L">Size L</option>
              <option value="XL">Size XL</option>
            </select>
            <input type="number" id="qty-${product.id}" min="1" value="1">
            <button onclick="addToCart(${product.id})">Add to Cart</button>
          </div>
        </div>
      `).join("");
    }

    function addToCart(id) {
      const product = products.find(p => p.id === id);
      const size = document.getElementById(`size-${id}`).value;
      const qty = parseInt(document.getElementById(`qty-${id}`).value);

      const existing = cart.find(item => item.id === id && item.size === size);

      if (existing) {
        existing.qty += qty;
      } else {
        cart.push({ ...product, size, qty });
      }

      localStorage.setItem("dressCart", JSON.stringify(cart));
      renderCart();
      alert(product.name + " added to cart!");
    }

    function renderCart() {
      const cartItems = document.getElementById("cartItems");
      const cartTotal = document.getElementById("cartTotal");

      if (cart.length === 0) {
        cartItems.innerHTML = "<p>Your cart is empty.</p>";
        cartTotal.innerText = "Total: ₹0";
        return;
      }

      cartItems.innerHTML = cart.map((item, index) => `
        <div class="cart-item">
          <div>
            <strong>${item.name}</strong><br>
            Size: ${item.size}<br>
            Quantity: ${item.qty}<br>
            Price: ₹${item.price * item.qty}
          </div>
          <button onclick="removeFromCart(${index})">Remove</button>
        </div>
      `).join("");

      const total = cart.reduce((sum, item) => sum + item.price * item.qty, 0);
      cartTotal.innerText = "Total: ₹" + total;
    }

    function removeFromCart(index) {
      cart.splice(index, 1);
      localStorage.setItem("dressCart", JSON.stringify(cart));
      renderCart();
    }

    function checkout() {
      if (cart.length === 0) {
        alert("Your cart is empty!");
        return;
      }
      alert("Order placed successfully!");
      cart = [];
      localStorage.setItem("dressCart", JSON.stringify(cart));
      renderCart();
    }

    renderProducts();
    renderCart();
  </script>
</body>
</html>
