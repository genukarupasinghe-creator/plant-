<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Green Aqua | Live Interactive Store</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f3f7f6;
            color: #1a2925;
            position: relative;
            overflow-x: hidden;
        }

        /* Navigation Bar */
        header {
            background-color: #ffffff;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 10%;
            box-shadow: 0 2px 15px rgba(11, 79, 78, 0.05);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .logo {
            font-size: 26px;
            font-weight: bold;
            color: #0b4f4e;
            text-decoration: none;
        }

        .cart-icon-btn {
            background: #0b4f4e;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 20px;
            font-weight: bold;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        /* Hero Banner */
        .hero {
            background: linear-gradient(rgba(11, 79, 78, 0.45), rgba(10, 25, 30, 0.75)), 
                        url('https://images.unsplash.com/photo-1544551763-46a013bb70d5?q=80&w=1470&auto=format&fit=crop') no-repeat center center/cover;
            height: 50vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: white;
            padding: 0 20px;
        }

        .hero h1 { font-size: 50px; margin-bottom: 10px; }

        /* Plant Product Grid */
        .section { padding: 60px 10%; text-align: center; }
        .section h2 { color: #0b4f4e; margin-bottom: 30px; font-size: 32px; }
        
        .plant-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 35px;
        }

        .plant-card {
            background: white;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 6px 20px rgba(11, 79, 78, 0.04);
            text-align: left;
        }

        .plant-image { width: 100%; height: 260px; object-fit: cover; }
        .plant-info { padding: 25px; }
        .plant-name { font-size: 20px; font-weight: 600; color: #0b4f4e; margin-bottom: 5px; }
        .plant-price { color: #128280; font-weight: 700; font-size: 18px; margin-bottom: 15px; }
        
        .add-to-cart-btn {
            display: block;
            width: 100%;
            padding: 12px;
            background-color: #eaf4f2;
            color: #0b4f4e;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            text-align: center;
            transition: all 0.2s;
        }

        .add-to-cart-btn:hover { background-color: #0b4f4e; color: white; }

        /* LIVE CART DRAWER (SLIDE OUT) */
        .cart-drawer {
            position: fixed;
            top: 0; right: -400px;
            width: 400px; height: 100vh;
            background: white;
            box-shadow: -5px 0 25px rgba(0,0,0,0.15);
            z-index: 1000;
            transition: right 0.3s ease;
            display: flex;
            flex-direction: column;
            padding: 30px;
        }

        .cart-drawer.open { right: 0; }
        .cart-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px; border-bottom: 2px solid #f0f4f3; padding-bottom: 15px;}
        .cart-header h3 { color: #0b4f4e; font-size: 24px; }
        .close-cart { background: none; border: none; font-size: 24px; cursor: pointer; color: #999; }
        
        .cart-items-list { flex-grow: 1; overflow-y: auto; margin-bottom: 20px; }
        .cart-item { display: flex; justify-content: space-between; padding: 10px 0; border-bottom: 1px solid #f0f4f3; font-size: 15px; }
        
        .cart-total { font-size: 20px; font-weight: bold; color: #0b4f4e; display: flex; justify-content: space-between; margin-bottom: 20px; }
        .checkout-btn { background: #128280; color: white; border: none; padding: 15px; border-radius: 8px; width: 100%; font-size: 16px; font-weight: bold; cursor: pointer; }
        .checkout-btn:hover { background: #0b4f4e; }

        /* Floating WhatsApp */
        .whatsapp-float { position: fixed; bottom: 30px; right: 30px; background-color: #25d366; color: white; width: 60px; height: 60px; border-radius: 50%; text-align: center; font-size: 30px; box-shadow: 2px 4px 15px rgba(0,0,0,0.15); z-index: 100; display: flex; align-items: center; justify-content: center; text-decoration: none; }
    </style>
</head>
<body>

    <header>
        <a href="#" class="logo">🌊 Green Aqua</a>
        <button class="cart-icon-btn" onclick="toggleCart()">
            🛒 Shopping Cart (<span id="cart-count">0</span>)
        </button>
    </header>

    <section class="hero">
        <h1>Green Aqua Storefront</h1>
        <p>Interactive functionality test room. Experience adding items to an active registry.</p>
    </section>

    <section class="section">
        <h2>Our Catalog</h2>
        <div class="plant-grid">
            
            <div class="plant-card">
                <img src="https://images.unsplash.com/photo-1614594975525-e45190c55d0b?q=80&w=600" class="plant-image">
                <div class="plant-info">
                    <div class="plant-name">Monstera Deliciosa</div>
                    <div class="plant-price">LKR 2,450</div>
                    <button class="add-to-cart-btn" onclick="addToCart('Monstera Deliciosa', 2450)">Add to Cart</button>
                </div>
            </div>

            <div class="plant-card">
                <img src="https://images.unsplash.com/photo-1685412502690-ca19fa3910c5?q=80&w=600" class="plant-image">
                <div class="plant-info">
                    <div class="plant-name">Anubias Nana on Wood</div>
                    <div class="plant-price">LKR 1,950</div>
                    <button class="add-to-cart-btn" onclick="addToCart('Anubias Nana on Wood', 1950)">Add to Cart</button>
                </div>
            </div>

            <div class="plant-card">
                <img src="https://images.unsplash.com/photo-1508817628294-5a453fa0b8fb?q=80&w=600" class="plant-image">
                <div class="plant-info">
                    <div class="plant-name">Marimo Moss Balls</div>
                    <div class="plant-price">LKR 850</div>
                    <button class="add-to-cart-btn" onclick="addToCart('Marimo Moss Balls', 850)">Add to Cart</button>
                </div>
            </div>

        </div>
    </section>

    <div class="cart-drawer" id="cartDrawer">
        <div class="cart-header">
            <h3>Your Order</h3>
            <button class="close-cart" onclick="toggleCart()">✕</button>
        </div>
        <div class="cart-items-list" id="cartItems">
            <p style="color: #888; text-align: center; margin-top: 20px;">Your cart is empty</p>
        </div>
        <div class="cart-total">
            <span>Total:</span>
            <span>LKR <span id="cartTotal">0</span></span>
        </div>
        <button class="checkout-btn" onclick="checkoutViaWhatsApp()">Place Order via WhatsApp</button>
    </div>

    <a href="https://wa.me/94771234567" class="whatsapp-float" target="_blank">💬</a>

    <script>
        let cart = [];
        let totalCost = 0;

        function toggleCart() {
            document.getElementById('cartDrawer').classList.toggle('open');
        }

        function addToCart(name, price) {
            cart.push({ name: name, price: price });
            totalCost += price;
            updateCartUI();
            document.getElementById('cartDrawer').classList.add('open');
        }

        function updateCartUI() {
            document.getElementById('cart-count').innerText = cart.length;
            document.getElementById('cartTotal').innerText = totalCost.toLocaleString();

            const itemsContainer = document.getElementById('cartItems');
            if(cart.length === 0) {
                itemsContainer.innerHTML = `<p style="color: #888; text-align: center; margin-top: 20px;">Your cart is empty</p>`;
                return;
            }

            itemsContainer.innerHTML = '';
            cart.forEach(item => {
                const itemRow = document.createElement('div');
                itemRow.className = 'cart-item';
                itemRow.innerHTML = `<span>🌿 ${item.name}</span> <strong>LKR ${item.price.toLocaleString()}</strong>`;
                itemsContainer.appendChild(itemRow);
            });
        }

        function checkoutViaWhatsApp() {
            if(cart.length === 0) {
                alert("Your shopping cart is empty!");
                return;
            }
            
            let message = `Hello Green Aqua! I want to order:\n`;
            cart.forEach(item => {
                message += `- ${item.name} (LKR ${item.price})\n`;
            });
            message += `\nTotal Amount: LKR ${totalCost.toLocaleString()}\nKindly let me know how to pay!`;
            
            let encodedMessage = encodeURIComponent(message);
            window.open(`https://wa.me/94771234567?text=${encodedMessage}`, '_blank');
        }
    </script>
</body>
</html>
