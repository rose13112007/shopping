# <!DOCTYPE html><html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title> DineshRoja shoping websit</title><style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(to right, #4facfe, #00f2fe);
}

header {
  background: #0d47a1;
  color: white;
  padding: 15px;
  text-align: center;
  font-size: 24px;
}

.products {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
  padding: 20px;
}

.card {
  background: white;
  border-radius: 12px;
  padding: 15px;
  text-align: center;
  box-shadow: 0 4px 10px rgba(0,0,0,0.2);
}

.card img {
  width: 100%;
  height: 150px;
  object-fit: cover;
  border-radius: 10px;
}

button {
  margin-top: 10px;
  padding: 10px;
  border: none;
  background: #0d47a1;
  color: white;
  border-radius: 8px;
  cursor: pointer;
}

button:hover {
  background: #1565c0;
}

.cart {
  position: fixed;
  right: 0;
  top: 0;
  width: 300px;
  height: 100%;
  background: white;
  padding: 15px;
  box-shadow: -4px 0 10px rgba(0,0,0,0.3);
}

.cart h2 {
  text-align: center;
}
</style></head><body><header>🛒 DineshRoja Shopping Website</header><div class="products" id="productList"></div><div class="cart">
  <h2>Cart</h2>
  <ul id="cartItems"></ul>
  <h3>Total: ₹<span id="total">0</span></h3>
  <button onclick="checkout()">Checkout</button>
</div><script>
const products = [
  {name: "Shoes", price: 1200, img: "https://via.placeholder.com/200"},
  {name: "Watch", price: 800, img: "https://via.placeholder.com/200"},
  {name: "Bag", price: 1500, img: "https://via.placeholder.com/200"},
  {name: "Headphones", price: 2000, img: "https://via.placeholder.com/200"},
  {name: "Mobile", price: 15000, img: "https://via.placeholder.com/200"}
];

let cart = [];

function displayProducts() {
  let html = "";
  products.forEach((p, index) => {
    html += `
      <div class="card">
        <img src="${p.img}">
        <h3>${p.name}</h3>
        <p>₹${p.price}</p>
        <button onclick="addToCart(${index})">Add to Cart</button>
      </div>`;
  });
  document.getElementById("productList").innerHTML = html;
}

function addToCart(index) {
  cart.push(products[index]);
  updateCart();
}

function updateCart() {
  let list = "";
  let total = 0;
  cart.forEach(item => {
    list += `<li>${item.name} - ₹${item.price}</li>`;
    total += item.price;
  });

  document.getElementById("cartItems").innerHTML = list;
  document.getElementById("total").innerText = total;
}

function checkout() {
  if(cart.length === 0) {
    alert("Cart is empty!");
  } else {
    alert("✅ Your order has been placed successfully!");
    cart = [];
    updateCart();
  }
}

displayProducts();
</script></body>
</html>
