<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Online Shopping Platform</title>
  <style>
    /* CSS for styling the page */
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #f4f4f4;
    }

    header {
      background-color: #333;
      color: #fff;
      text-align: center;
      padding: 1em 0;
    }

    main {
      padding: 20px;
    }

    h2 {
      color: #333;
    }

    .products {
      display: flex;
      justify-content: space-around;
      margin-bottom: 20px;
    }

    .product {
      background-color: white;
      padding: 10px;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
      text-align: center;
      width: 200px;
    }

    .product img {
      width: 100%;
      height: auto;
      border-radius: 8px;
    }

    .product h3 {
      font-size: 1.2em;
      color: #333;
    }

    .product .price {
      font-size: 1.3em;
      color: green;
    }

    button {
      background-color: #28a745;
      color: white;
      padding: 10px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background-color: #218838;
    }

    .customer-info {
      margin-top: 20px;
    }

    form input, form textarea {
      width: 100%;
      padding: 10px;
      margin: 5px 0;
      border-radius: 5px;
      border: 1px solid #ddd;
    }

    form button {
      background-color: #007bff;
      color: white;
      padding: 10px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    form button:hover {
      background-color: #0056b3;
    }

    #cart {
      margin-top: 20px;
    }

    #cartItems {
      list-style-type: none;
      padding: 0;
    }

    #cartItems li {
      background-color: #f9f9f9;
      margin: 5px 0;
      padding: 10px;
      border-radius: 5px;
    }

    #totalPrice {
      font-size: 1.5em;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <header>
    <h1>Welcome to Our Online Shop</h1>
  </header>

  <main>
    <section class="products">
      <div class="product">
        <img src="https://via.placeholder.com/200" alt="Product 1">
        <h3>Product 1</h3>
        <p class="price">$19.99</p>
        <button onclick="addToCart('Product 1', 19.99)">Add to Cart</button>
      </div>
      <div class="product">
        <img src="https://via.placeholder.com/200" alt="Product 2">
        <h3>Product 2</h3>
        <p class="price">$29.99</p>
        <button onclick="addToCart('Product 2', 29.99)">Add to Cart</button>
      </div>
      <div class="product">
        <img src="https://via.placeholder.com/200" alt="Product 3">
        <h3>Product 3</h3>
        <p class="price">$39.99</p>
        <button onclick="addToCart('Product 3', 39.99)">Add to Cart</button>
      </div>
    </section>

    <section class="customer-info">
      <h2>Customer Information</h2>
      <form id="customerForm">
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required><br><br>
        
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required><br><br>
        
        <label for="address">Address:</label>
        <textarea id="address" name="address" required></textarea><br><br>

        <button type="submit">Submit Order</button>
      </form>
    </section>

    <section id="cart">
      <h2>Your Cart</h2>
      <ul id="cartItems">
        <!-- Cart items will be listed here -->
      </ul>
      <p id="totalPrice">Total: $0.00</p>
    </section>
  </main>

  <footer>
    <p>&copy; 2024 Online Shop</p>
  </footer>

  <script>
    // JavaScript to handle cart and form submission
    let cart = [];
    let total = 0;

    function addToCart(product, price) {
      // Add product to the cart array
      cart.push({ product, price });
      total += price;

      // Update cart display
      updateCart();
    }

    function updateCart() {
      const cartItems = document.getElementById('cartItems');
      const totalPrice = document.getElementById('totalPrice');
      
      // Clear the cart list
      cartItems.innerHTML = '';
      
      // Add each item in the cart to the display
      cart.forEach(item => {
        const li = document.createElement('li');
        li.textContent = `${item.product} - $${item.price.toFixed(2)}`;
        cartItems.appendChild(li);
      });

      // Update the total price
      totalPrice.textContent = `Total: $${total.toFixed(2)}`;
    }

    document.getElementById('customerForm').addEventListener('submit', function(event) {
      event.preventDefault(); // Prevent page refresh
      
      // Get customer info
      const name = document.getElementById('name').value;
      const email = document.getElementById('email').value;
      const address = document.getElementById('address').value;

      // Display a confirmation message
      alert(`Order submitted! \n\nName: ${name}\nEmail: ${email}\nAddress: ${address}\nTotal: $${total.toFixed(2)}`);

      // Optionally, you can reset the form and cart after submission
      document.getElementById('customerForm').reset();
      cart = [];
      total = 0;
      updateCart();
    });
  </script>
</body>
</html>
