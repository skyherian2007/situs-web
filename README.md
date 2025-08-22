# situs-web
                    nano index.html
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MiniShop</title>
<link rel="stylesheet" href="style.css">
</head>
<body>

<header>
  <h1>MiniShop</h1>
  <p>Belanja digital asset / produk mini</p>
</header>

<section id="products">
  <div class="product">
    <img src="https://raw.githubusercontent.com/NdikzDatabase/Database/main/Database/1755612697709-w04mvm.jpg" alt="Product 1">
    <h3>Product 1</h3>
    <p>Rp 50.000</p>
    <button onclick="addToCart('Product 1', 50000)">Add to Cart</button>
  </div>
  <div class="product">
    <img src="https://raw.githubusercontent.com/NdikzDatabase/Database/main/Database/1755612711971-5jl9vx.jpg" alt="Product 2">
    <h3>Product 2</h3>
    <p>Rp 75.000</p>
    <button onclick="addToCart('Product 2', 75000)">Add to Cart</button>
  </div>
  <div class="product">
    <img src="https://raw.githubusercontent.com/NdikzDatabase/Database/main/Database/1755612684556-1lmqsu.jpg" alt="Product 3">
    <h3>Product 3</h3>
    <p>Rp 100.000</p>
    <button onclick="addToCart('Product 3', 100000)">Add to Cart</button>
  </div>
</section>

<section id="cart">
  <h2>Cart</h2>
  <ul id="cartItems"></ul>
  <p>Total: Rp <span id="total">0</span></p>
  <button onclick="checkout()">Checkout</button>
</section>

<script src="script.js"></script>
</body>
</html>


               nano style.css

body {
    font-family: Arial, sans-serif;
    text-align: center;
    background: #f0f0f0;
    margin: 0;
    padding: 20px;
}

header {
    background: #00796b;
    color: white;
    padding: 20px;
    border-radius: 10px;
    margin-bottom: 20px;
}

#products {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
}

.product {
    background: #fff;
    margin: 10px;
    padding: 15px;
    border-radius: 15px;
    box-shadow: 0 6px 12px rgba(0,0,0,0.15);
    width: 200px;
}

.product img {
    width: 100%;
    height: 150px;
    object-fit: cover;
    border-radius: 10px;
}

button {
    padding: 8px 12px;
    border: none;
    border-radius: 8px;
    background: #00796b;
    color: white;
    cursor: pointer;
    margin-top: 10px;
}

button:hover {
    background: #004d40;
}

#cart {
    margin-top: 30px;
    padding: 20px;
    background: #fff;
    border-radius: 15px;
    box-shadow: 0 6px 12px rgba(0,0,0,0.15);
}

           Java scrip

let cart = [];
let total = 0;

function addToCart(product, price){
    cart.push({product, price});
    total += price;
    updateCart();
}

function updateCart(){
    const cartItems = document.getElementById('cartItems');
    cartItems.innerHTML = '';
    cart.forEach(item => {
        const li = document.createElement('li');
        li.textContent = `${item.product} - Rp ${item.price}`;
        cartItems.appendChild(li);
    });
    document.getElementById('total').textContent = total;
}

function checkout(){
    if(cart.length === 0){
        alert('Cart kosong!');
        return;
    }
    alert(`Total pembayaran: Rp ${total}\nSilakan transfer atau hubungi penjual.`);
    cart = [];
    total = 0;
    updateCart();
}



