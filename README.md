# hk.index
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ShopEase - E-Commerce</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            background: #f5f5f5;
            color: #222;
        }

        /* Navbar */
        header {
            background: #111827;
            color: white;
            padding: 15px 5%;
            display: flex;
            align-items: center;
            justify-content: space-between;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .logo {
            font-size: 25px;
            font-weight: bold;
            color: #38bdf8;
        }

        .search-box {
            width: 40%;
            display: flex;
        }

        .search-box input {
            width: 100%;
            padding: 10px;
            border: none;
            outline: none;
            border-radius: 5px 0 0 5px;
        }

        .search-box button {
            border: none;
            padding: 10px 15px;
            background: #38bdf8;
            cursor: pointer;
            border-radius: 0 5px 5px 0;
        }

        .cart-button {
            background: #38bdf8;
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        }

        /* Hero */
        .hero {
            background: linear-gradient(135deg, #0f172a, #0369a1);
            color: white;
            padding: 70px 5%;
            text-align: center;
        }

        .hero h1 {
            font-size: 45px;
            margin-bottom: 15px;
        }

        .hero p {
            font-size: 18px;
            margin-bottom: 25px;
        }

        .shop-btn {
            background: #38bdf8;
            color: #111;
            padding: 12px 25px;
            border: none;
            border-radius: 5px;
            font-weight: bold;
            cursor: pointer;
        }

        /* Categories */
        .categories {
            padding: 30px 5%;
            text-align: center;
        }

        .categories button {
            margin: 5px;
            padding: 10px 18px;
            border: 1px solid #ddd;
            background: white;
            border-radius: 20px;
            cursor: pointer;
        }

        .categories button:hover {
            background: #38bdf8;
        }

        /* Products */
        .products-section {
            padding: 20px 5% 50px;
        }

        .products-section h2 {
            margin-bottom: 25px;
            text-align: center;
        }

        .products {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 25px;
        }

        .product {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
            transition: 0.3s;
        }

        .product:hover {
            transform: translateY(-5px);
        }

        .product img {
            width: 100%;
            height: 220px;
            object-fit: cover;
        }

        .product-info {
            padding: 15px;
        }

        .product-info h3 {
            margin-bottom: 8px;
        }

        .product-info p {
            color: #666;
            margin-bottom: 10px;
        }

        .price {
            font-size: 20px;
            font-weight: bold;
            color: #0284c7;
            margin-bottom: 12px;
        }

        .add-btn {
            width: 100%;
            padding: 10px;
            background: #111827;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .add-btn:hover {
            background: #0284c7;
        }

        /* Cart */
        .cart {
            position: fixed;
            top: 0;
            right: -400px;
            width: 380px;
            max-width: 100%;
            height: 100vh;
            background: white;
            z-index: 200;
            box-shadow: -5px 0 15px rgba(0,0,0,0.2);
            padding: 20px;
            transition: 0.3s;
            overflow-y: auto;
        }

        .cart.active {
            right: 0;
        }

        .cart-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .close-cart {
            background: #ef4444;
            color: white;
            border: none;
            padding: 8px 12px;
            border-radius: 5px;
            cursor: pointer;
        }

        .cart-item {
            display: flex;
            align-items: center;
            gap: 10px;
            border-bottom: 1px solid #ddd;
            padding: 12px 0;
        }

        .cart-item img {
            width: 60px;
            height: 60px;
            object-fit: cover;
            border-radius: 5px;
        }

        .cart-item-info {
            flex: 1;
        }

        .cart-item-info h4 {
            margin-bottom: 5px;
        }

        .quantity button {
            padding: 3px 8px;
            cursor: pointer;
        }

        .remove {
            background: #ef4444;
            color: white;
            border: none;
            padding: 5px;
            cursor: pointer;
            border-radius: 3px;
        }

        .cart-total {
            font-size: 22px;
            font-weight: bold;
            margin-top: 20px;
        }

        .checkout {
            width: 100%;
            margin-top: 15px;
            padding: 13px;
            background: #22c55e;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
        }

        /* Footer */
        footer {
            background: #111827;
            color: white;
            text-align: center;
            padding: 25px;
        }

        @media (max-width: 700px) {
            header {
                flex-wrap: wrap;
                gap: 12px;
            }

            .search-box {
                order: 3;
                width: 100%;
            }

            .hero h1 {
                font-size: 32px;
            }

            .cart {
                width: 100%;
            }
        }
    </style>
</head>

<body>

    <!-- Navbar -->
    <header>
        <div class="logo">ShopEase</div>

        <div class="search-box">
            <input
                type="text"
                id="searchInput"
                placeholder="Search products..."
                onkeyup="searchProducts()"
            >
            <button>🔍</button>
        </div>

        <button class="cart-button" onclick="openCart()">
            🛒 Cart (<span id="cartCount">0</span>)
        </button>
    </header>


    <!-- Hero -->
    <section class="hero">
        <h1>Welcome to ShopEase</h1>
        <p>Discover amazing products at great prices.</p>
        <button class="shop-btn" onclick="scrollToProducts()">
            Shop Now
        </button>
    </section>


    <!-- Categories -->
    <section class="categories">
        <h2>Categories</h2>

        <button onclick="filterProducts('all')">All</button>
        <button onclick="filterProducts('electronics')">Electronics</button>
        <button onclick="filterProducts('fashion')">Fashion</button>
        <button onclick="filterProducts('shoes')">Shoes</button>
        <button onclick="filterProducts('accessories')">Accessories</button>
    </section>


    <!-- Products -->
    <section class="products-section" id="productsSection">

        <h2>Featured Products</h2>

        <div class="products" id="productList">

            <div class="product" data-category="electronics" data-name="Wireless Headphones">
                <img src="https://picsum.photos/400/300?random=1">
                <div class="product-info">
                    <h3>Wireless Headphones</h3>
                    <p>High quality wireless headphones.</p>
                    <div class="price">₹2,499</div>
                    <button class="add-btn"
                        onclick="addToCart('Wireless Headphones', 2499, 'https://picsum.photos/400/300?random=1')">
                        Add to Cart
                    </button>
                </div>
            </div>


            <div class="product" data-category="electronics" data-name="Smart Watch">
                <img src="https://picsum.photos/400/300?random=2">
                <div class="product-info">
                    <h3>Smart Watch</h3>
                    <p>Smart watch with fitness tracking.</p>
                    <div class="price">₹3,999</div>
                    <button class="add-btn"
                        onclick="addToCart('Smart Watch', 3999, 'https://picsum.photos/400/300?random=2')">
                        Add to Cart
                    </button>
                </div>
            </div>


            <div class="product" data-category="fashion" data-name="Casual T-Shirt">
                <img src="https://picsum.photos/400/300?random=3">
                <div class="product-info">
                    <h3>Casual T-Shirt</h3>
                    <p>Comfortable cotton T-shirt.</p>
                    <div class="price">₹799</div>
                    <button class="add-btn"
                        onclick="addToCart('Casual T-Shirt', 799, 'https://picsum.photos/400/300?random=3')">
                        Add to Cart
                    </button>
                </div>
            </div>


            <div class="product" data-category="shoes" data-name="Running Shoes">
                <img src="https://picsum.photos/400/300?random=4">
                <div class="product-info">
                    <h3>Running Shoes</h3>
                    <p>Lightweight shoes for running.</p>
                    <div class="price">₹2,999</div>
                    <button class="add-btn"
                        onclick="addToCart('Running Shoes', 2999, 'https://picsum.photos/400/300?random=4')">
                        Add to Cart
                    </button>
                </div>
            </div>


            <div class="product" data-category="accessories" data-name="Leather Wallet">
                <img src="https://picsum.photos/400/300?random=5">
                <div class="product-info">
                    <h3>Leather Wallet</h3>
                    <p>Premium leather wallet.</p>
                    <div class="price">₹999</div>
                    <button class="add-btn"
                        onclick="addToCart('Leather Wallet', 999, 'https://picsum.photos/400/300?random=5')">
                        Add to Cart
                    </button>
                </div>
            </div>


            <div class="product" data-category="fashion" data-name="Denim Jacket">
                <img src="https://picsum.photos/400/300?random=6">
                <div class="product-info">
                    <h3>Denim Jacket</h3>
                    <p>Stylish denim jacket.</p>
                    <div class="price">₹1,999</div>
                    <button class="add-btn"
                        onclick="addToCart('Denim Jacket', 1999, 'https://picsum.photos/400/300?random=6')">
                        Add to Cart
                    </button>
                </div>
            </div>

        </div>
    </section>


    <!-- Cart -->
    <div class="cart" id="cart">

        <div class="cart-header">
            <h2>Shopping Cart</h2>
            <button class="close-cart" onclick="closeCart()">✕</button>
        </div>

        <div id="cartItems">
            <p>Your cart is empty.</p>
        </div>

        <div class="cart-total">
            Total: ₹<span id="cartTotal">0</span>
        </div>

        <button class="checkout" onclick="checkout()">
            Proceed to Checkout
        </button>

    </div>


    <!-- Footer -->
    <footer>
        <p>© 2026 ShopEase. All rights reserved.</p>
    </footer>


    <script>

        let cart = [];


        // Add product to cart
        function addToCart(name, price, image) {

            const existingProduct = cart.find(
                product => product.name === name
            );

            if (existingProduct) {
                existingProduct.quantity++;
            } else {
                cart.push({
                    name: name,
                    price: price,
                    image: image,
                    quantity: 1
                });
            }

            updateCart();

            alert(name + " added to cart!");
        }


        // Update cart
        function updateCart() {

            const cartItems = document.getElementById("cartItems");
            const cartCount = document.getElementById("cartCount");
            const cartTotal = document.getElementById("cartTotal");

            cartItems.innerHTML = "";

            let total = 0;
            let count = 0;

            if (cart.length === 0) {
                cartItems.innerHTML = "<p>Your cart is empty.</p>";
            }

            cart.forEach((item, index) => {

                total += item.price * item.quantity;
                count += item.quantity;

                cartItems.innerHTML += `
                    <div class="cart-item">

                        <img src="${item.image}">

                        <div class="cart-item-info">
                            <h4>${item.name}</h4>

                            <p>₹${item.price}</p>

                            <div class="quantity">
                                <button onclick="changeQuantity(${index}, -1)">
                                    -
                                </button>

                                ${item.quantity}

                                <button onclick="changeQuantity(${index}, 1)">
                                    +
                                </button>
                            </div>
                        </div>

                        <button class="remove"
                            onclick="removeItem(${index})">
                            🗑
                        </button>

                    </div>
                `;
            });

            cartCount.innerText = count;
            cartTotal.innerText = total.toLocaleString("en-IN");
        }


        // Change quantity
        function changeQuantity(index, amount) {

            cart[index].quantity += amount;

            if (cart[index].quantity <= 0) {
                cart.splice(index, 1);
            }

            updateCart();
        }


        // Remove item
        function removeItem(index) {

            cart.splice(index, 1);

            updateCart();
        }


        // Open cart
        function openCart() {

            document.getElementById("cart")
                .classList.add("active");
        }


        // Close cart
        function closeCart() {

            document.getElementById("cart")
                .classList.remove("active");
        }


        // Search products
        function searchProducts() {

            const search =
                document.getElementById("searchInput")
                .value
                .toLowerCase();

            const products =
                document.querySelectorAll(".product");

            products.forEach(product => {

                const name =
                    product.dataset.name.toLowerCase();

                if (name.includes(search)) {
                    product.style.display = "block";
                } else {
                    product.style.display = "none";
                }
            });
        }


        // Filter products
        function filterProducts(category) {

            const products =
                document.querySelectorAll(".product");

            products.forEach(product => {

                if (
                    category === "all" ||
                    product.dataset.category === category
                ) {
                    product.style.display = "block";
                } else {
                    product.style.display = "none";
                }
            });
        }


        // Scroll to products
        function scrollToProducts() {

            document.getElementById("productsSection")
                .scrollIntoView({
                    behavior: "smooth"
                });
        }


        // Checkout
        function checkout() {

            if (cart.length === 0) {
                alert("Your cart is empty!");
                return;
            }

            alert(
                "Thank you for your order! Checkout system can be connected to a payment gateway."
            );
        }

    </script>

</body>
</html>
