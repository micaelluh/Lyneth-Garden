<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Online Shop</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

  <header>
    <h1>Welcome to the Online Shop</h1>
  </header>

  <div class="product-list">
    <div class="product">
      <img src="https://via.placeholder.com/150" alt="Product 1">
      <h2>Product 1</h2>
      <p>$25.00</p>
      <button class="add-to-cart" onclick="addToCart('Product 1', 25)">Add to Cart</button>
    </div>
    <div class="product">
      <img src="https://via.placeholder.com/150" alt="Product 2">
      <h2>Product 2</h2>
      <p>$40.00</p>
      <button class="add-to-cart" onclick="addToCart('Product 2', 40)">Add to Cart</button>
    </div>
    <div class="product">
      <img src="https://via.placeholder.com/150" alt="Product 3">
      <h2>Product 3</h2>
      <p>$15.00</p>
      <button class="add-to-cart" onclick="addToCart('Product 3', 15)">Add to Cart</button>
    </div>
    <div class="product">
      <img src="https://via.placeholder.com/150" alt="Product 4">
      <h2>Product 4</h2>
      <p>$30.00</p>
      <button class="add-to-cart" onclick="addToCart('Product 4', 30)">Add to Cart</button>
    </div>
  </div>

  <div id="cart">
    <h2>Your Cart</h2>
    <ul id="cart-items">
      <!-- Cart items will appear here -->
    </ul>
    <p id="total-price">Total: $0.00</p>
  </div>

  <script src="script.js"></script>

</body>
</html>


body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f4f4f4;
}

header {
  background-color: #333;
  color: white;
  text-align: center;
  padding: 20px;
}

.product-list {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  margin: 20px;
}

.product {
  background-color: white;
  border: 1px solid #ddd;
  padding: 20px;
  width: 200px;
  text-align: center;
  margin: 10px;
}

.product img {
  width: 100%;
  height: auto;
}

.product h2 {
  font-size: 18px;
}

.product p {
  color: green;
  font-size: 16px;
}

.add-to-cart {
  background-color: #28a745;
  color: white;
  border: none;
  padding: 10px;
  cursor: pointer;
}

.add-to-cart:hover {
  background-color: #218838;
}

#cart {
  position: fixed;
  right: 20px;
  top: 100px;
  background-color: #fff;
  padding: 20px;
  border: 1px solid #ddd;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

#cart h2 {
  margin-top: 0;
}

#cart-items {
  list-style-type: none;
  padding: 0;
}

#cart-items li {
  padding: 5px 0;
}

#total-price {
  font-weight: bold;
  margin-top: 20px;
}



let cart = [];
let total = 0;

function addToCart(productName, productPrice) {
  // Add the product to the cart
  cart.push({ name: productName, price: productPrice });

  // Update the total price
  total += productPrice;

  // Display the cart items and total price
  updateCart();
}

function updateCart() {
  const cartItemsContainer = document.getElementById('cart-items');
  const totalPriceContainer = document.getElementById('total-price');

  // Clear the current cart items
  cartItemsContainer.innerHTML = '';

  // Display the updated cart items
  cart.forEach(item => {
    const li = document.createElement('li');
    li.textContent = `${item.name} - $${item.price.toFixed(2)}`;
    cartItemsContainer.appendChild(li);
  });

  // Update the total price
  totalPriceContainer.textContent = `Total: $${total.toFixed(2)}`;
}
