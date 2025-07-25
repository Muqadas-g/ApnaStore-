# ApnaStore-
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ApnaStore - The Everything Store</title>

    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>

    <!-- Google Fonts: Inter -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">

    <!-- Font Awesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

    <!-- Custom Styles -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }

        .page {
            display: none;
        }

        .page.active {
            display: block;
        }

        /* Dropdown styles */
        .dropdown:hover .dropdown-menu {
            display: block;
        }

        /* Modal styles */
        .modal {
            transition: opacity 0.25s ease;
        }

        /* Slider Styles */
        .slider-container {
            position: relative;
            max-width: 100%;
            height: 60vh;
            /* Adjust height as needed */
            margin: auto;
            overflow: hidden;
        }

        .slide {
            display: none;
            width: 100%;
            height: 100%;
        }

        .slide img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .slide-content {
            position: absolute;
            bottom: 10%;
            left: 5%;
            color: white;
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.5);
            border-radius: 8px;
        }

        .prev,
        .next {
            cursor: pointer;
            position: absolute;
            top: 50%;
            width: auto;
            padding: 16px;
            margin-top: -22px;
            color: white;
            font-weight: bold;
            font-size: 24px;
            transition: 0.6s ease;
            border-radius: 0 3px 3px 0;
            user-select: none;
            background-color: rgba(0, 0, 0, 0.3);
        }

        .next {
            right: 0;
            border-radius: 3px 0 0 3px;
        }

        .prev:hover,
        .next:hover {
            background-color: rgba(0, 0, 0, 0.8);
        }

        .dots-container {
            text-align: center;
            position: absolute;
            bottom: 20px;
            width: 100%;
        }

        .dot {
            cursor: pointer;
            height: 15px;
            width: 15px;
            margin: 0 2px;
            background-color: #bbb;
            border-radius: 50%;
            display: inline-block;
            transition: background-color 0.6s ease;
        }

        .dot.active,
        .dot:hover {
            background-color: #717171;
        }

        /* Equal height product cards */
        .product-card {
            display: flex;
            flex-direction: column;
            height: 100%;
        }

        .product-card .card-content {
            flex-grow: 1;
            display: flex;
            flex-direction: column;
        }

        .product-card .card-footer {
            margin-top: auto;
        }

        /* Deal badge */
        .deal-badge {
            position: absolute;
            top: 10px;
            left: 10px;
            background-color: #CC0C39;
            color: white;
            padding: 3px 8px;
            border-radius: 3px;
            font-size: 12px;
            font-weight: bold;
        }
    </style>
</head>

<body class="bg-gray-200">

    <!-- Header Section -->
    <header class="bg-gray-900 text-white sticky top-0 z-50">
        <!-- Top Nav -->
        <div class="container mx-auto px-4 py-2 flex justify-between items-center">
            <a href="#" class="text-3xl font-bold" onclick="showPage('home')">Apna<span
                    class="text-orange-400">Store</span></a>
            <div class="hidden md:flex flex-grow max-w-2xl mx-4">
                <input type="text" placeholder="Search ApnaStore..."
                    class="w-full px-4 py-2 rounded-l-md text-gray-800 focus:outline-none">
                <button class="bg-orange-400 hover:bg-orange-500 text-white px-5 rounded-r-md"><i
                        class="fa fa-search"></i></button>
            </div>
            <div class="flex items-center space-x-4">
                <div class="relative dropdown"><button class="flex items-center space-x-1 hover:text-orange-400"><i
                            class="fa fa-globe text-xl"></i><span class="hidden lg:inline">EN</span><i
                            class="fa fa-caret-down text-xs"></i></button>
                    <ul
                        class="dropdown-menu absolute hidden bg-white text-gray-800 rounded-md shadow-lg mt-2 py-1 w-32 right-0">
                        <li><a href="#" class="block px-4 py-2 text-sm hover:bg-gray-100">English</a></li>
                        <li><a href="#" class="block px-4 py-2 text-sm hover:bg-gray-100">اردو</a></li>
                    </ul>
                </div>
                <button id="signInBtn" class="hover:text-orange-400">
                    <div class="text-xs">Hello, sign in</div>
                    <div class="font-bold flex items-center">Account & Lists <i
                            class="fa fa-caret-down text-xs ml-1"></i></div>
                </button>
                <a href="#" class="hidden sm:block hover:text-orange-400">
                    <div class="text-xs">Returns</div>
                    <div class="font-bold">& Orders</div>
                </a>
                <a href="#" class="relative flex items-end hover:text-orange-400"><i
                        class="fa fa-shopping-cart text-3xl"></i><span
                        class="absolute -top-1 -right-2 bg-orange-400 text-white text-xs font-bold rounded-full h-5 w-5 flex items-center justify-center">3</span><span
                        class="hidden lg:inline font-bold ml-2">Cart</span></a>
                <button id="mobile-menu-button" class="md:hidden text-white focus:outline-none ml-2"><i
                        class="fa fa-bars text-xl"></i></button>
            </div>
        </div>
        <!-- Bottom Nav -->
        <nav class="bg-gray-800 text-white">
            <div class="container mx-auto px-4 flex items-center space-x-6 py-2">
                <a href="#" class="font-semibold hover:text-orange-400" onclick="showPage('home')">Home</a>
                <a href="#" class="font-semibold hover:text-orange-400" onclick="showPage('shop')">Today's Deals</a>
                <a href="#" class="font-semibold hover:text-orange-400" onclick="showPage('contact')">Customer
                    Service</a>
                <a href="#" class="font-semibold hover:text-orange-400" onclick="showPage('messages')">Messages</a>
                <a href="#" class="font-semibold hover:text-orange-400" onclick="showPage('giftcards')">Gift Cards</a>
                <a href="#" class="font-semibold hover:text-orange-400" onclick="showPage('sell')">Sell</a>
            </div>
        </nav>
        <div id="mobile-menu" class="hidden md:hidden bg-gray-800 px-4 pb-3"></div>
    </header>

    <main>
        <!-- Home Page -->
        <div id="home" class="page active">
            <!-- Image Slider -->
            <div class="slider-container">
                <div class="slide">
                    <img src="https://placehold.co/1600x600/334155/FFFFFF?text=Latest+in+Electronics" alt="Electronics">
                    <div class="slide-content">
                        <h2>Discover Cutting-Edge Gadgets</h2>
                        <p>Shop the newest phones, laptops, and accessories.</p>
                    </div>
                </div>
                <div class="slide">
                    <img src="https://placehold.co/1600x600/7c2d12/FFFFFF?text=Shop+Fashion+Trends" alt="Fashion">
                    <div class="slide-content">
                        <h2>Upgrade Your Wardrobe</h2>
                        <p>Find the latest trends in clothing for all seasons.</p>
                    </div>
                </div>
                <div class="slide">
                    <img src="https://placehold.co/1600x600/166534/FFFFFF?text=Beautify+Your+Home" alt="Home Decor">
                    <div class="slide-content">
                        <h2>Transform Your Living Space</h2>
                        <p>Explore stylish furniture and home decor.</p>
                    </div>
                </div>
                <a class="prev">&#10094;</a>
                <a class="next">&#10095;</a>
            </div>
            <div class="dots-container"></div>

            <!-- Product Grid -->
            <div class="container mx-auto px-6 py-12">
                <h2 class="text-3xl font-bold text-center text-gray-800 mb-10">Top Picks for You</h2>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
                    <!-- Product 1: Kitchen Knife -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card">
                        <img src="kitchenknife.jpg" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">6 Inch Kitchen Knife</h3>
                            <p class="text-orange-500 font-bold text-xl">PKR 7,899</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>

                    <!-- Product 2: Wooden Cutting Board -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card">
                        <img src="wood-cutting-board.avif" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">Wooden Cutting Board</h3>
                            <p class="text-orange-500 font-bold text-xl">PKR 4,499</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>

                    <!-- Product 3: Non-Stick Frying Pan -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card">
                        <img src="pan.jpg" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">Non-Stick Frying Pan</h3>
                            <p class="text-orange-500 font-bold text-xl">PKR 9,120</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>

                    <!-- Product 4: Measuring Spoon Set -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card">
                        <img src="spoonset.jpg" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">Measuring Spoon Set</h3>
                            <p class="text-orange-500 font-bold text-xl">PKR 2,750</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Today's Deals Page -->
        <div id="shop" class="page">
            <div class="container mx-auto px-6 py-12">
                <h1 class="text-4xl font-bold text-gray-800 mb-8 text-center">Today's Deals</h1>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
                    <!-- Deal 1 -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card relative">
                        <span class="deal-badge">30% OFF</span>
                        <img src="airbuds.webp" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">Wireless Earbuds Pro</h3>
                            <div class="flex items-center">
                                <p class="text-orange-500 font-bold text-xl">PKR 4,999</p>
                                <p class="text-gray-500 line-through ml-2 text-sm">PKR 7,142</p>
                            </div>
                            <p class="text-green-600 text-sm mt-1">Save PKR 2,143</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>

                    <!-- Deal 2 -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card relative">
                        <span class="deal-badge">50% OFF</span>
                        <img src="watch.webp" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">Smart Watch Series 5</h3>
                            <div class="flex items-center">
                                <p class="text-orange-500 font-bold text-xl">PKR 8,999</p>
                                <p class="text-gray-500 line-through ml-2 text-sm">PKR 17,999</p>
                            </div>
                            <p class="text-green-600 text-sm mt-1">Save PKR 9,000</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>

                    <!-- Deal 3 -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card relative">
                        <span class="deal-badge">25% OFF</span>
                        <img src="blender.webp" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">3-in-1 Blender</h3>
                            <div class="flex items-center">
                                <p class="text-orange-500 font-bold text-xl">PKR 5,625</p>
                                <p class="text-gray-500 line-through ml-2 text-sm">PKR 7,500</p>
                            </div>
                            <p class="text-green-600 text-sm mt-1">Save PKR 1,875</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>

                    <!-- Deal 4 -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card relative">
                        <span class="deal-badge">40% OFF</span>
                        <img src="bag.jpg" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">Premium Travel Backpack</h3>
                            <div class="flex items-center">
                                <p class="text-orange-500 font-bold text-xl">PKR 3,600</p>
                                <p class="text-gray-500 line-through ml-2 text-sm">PKR 6,000</p>
                            </div>
                            <p class="text-green-600 text-sm mt-1">Save PKR 2,400</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Categories Page -->
        <div id="categories" class="page">
            <div class="container mx-auto px-6 py-12">
                <h1 class="text-4xl font-bold text-gray-800 mb-8 text-center">Categories</h1>
                <p class="text-center">Categories page content goes here.</p>
            </div>
        </div>

        <!-- About Page -->
        <div id="about" class="page">
            <div class="container mx-auto px-6 py-16">
                <h1 class="text-4xl font-bold text-gray-800 mb-6 text-center">About Us</h1>
                <div class="bg-white p-8 rounded-lg shadow-lg max-w-4xl mx-auto">
                    <p class="text-lg text-gray-700 leading-relaxed">'ApnaStore' was launched in 2024 with the mission
                        to provide high-quality products at affordable prices to customers across Pakistan. We leverage
                        technology and superior customer service to make your online shopping experience easy and
                        enjoyable.</p>
                </div>
            </div>
        </div>

        <!-- Contact Page -->
        <div id="contact" class="page">
            <div class="container mx-auto px-6 py-16">
                <h1 class="text-4xl font-bold text-gray-800 mb-8 text-center">Customer Service</h1>
                <div class="max-w-2xl mx-auto bg-white p-8 rounded-lg shadow-lg">
                    <form>
                        <div class="mb-4"><label for="name"
                                class="block text-gray-700 font-semibold mb-2">Name</label><input type="text" id="name"
                                class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500">
                        </div>
                        <div class="mb-4"><label for="email"
                                class="block text-gray-700 font-semibold mb-2">Email</label><input type="email"
                                id="email"
                                class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500">
                        </div>
                        <div class="mb-4"><label for="message"
                                class="block text-gray-700 font-semibold mb-2">Message</label><textarea id="message"
                                rows="5"
                                class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500"></textarea>
                        </div>
                        <div class="text-center"><button type="submit"
                                class="bg-gray-800 text-white font-bold py-3 px-8 rounded-lg hover:bg-orange-500 transition duration-300">Send
                                Message</button></div>
                    </form>
                </div>
            </div>
        </div>

        <!-- Messages Page -->
        <div id="messages" class="page">
            <div class="container mx-auto px-6 py-12">
                <h1 class="text-4xl font-bold text-gray-800 mb-8 text-center">Your Messages</h1>
                <div class="bg-white p-8 rounded-lg shadow-lg max-w-4xl mx-auto text-center"><i
                        class="fas fa-envelope-open-text text-6xl text-gray-300 mb-4"></i>
                    <p class="text-gray-500">You have no new messages.</p>
                </div>
            </div>
        </div>

        <!-- Gift Cards Page -->
        <div id="giftcards" class="page">
            <div class="container mx-auto px-6 py-12">
                <h1 class="text-4xl font-bold text-gray-800 mb-8 text-center">Gift Cards</h1>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                    <!-- Gift Card 1 -->
                    <div
                        class="bg-gradient-to-br from-blue-500 to-blue-700 text-white rounded-lg shadow-lg overflow-hidden">
                        <div class="p-6">
                            <h3 class="text-2xl font-bold mb-2">ApnaStore Gift Card</h3>
                            <p class="mb-4">Perfect for any occasion - let them choose what they love!</p>
                            <div class="flex justify-between items-center">
                                <div class="text-3xl font-bold">PKR 1,000</div>
                                <button
                                    class="bg-white text-blue-600 px-4 py-2 rounded-lg font-semibold hover:bg-gray-100">Buy
                                    Now</button>
                            </div>
                        </div>
                    </div>

                    <!-- Gift Card 2 -->
                    <div
                        class="bg-gradient-to-br from-purple-500 to-purple-700 text-white rounded-lg shadow-lg overflow-hidden">
                        <div class="p-6">
                            <h3 class="text-2xl font-bold mb-2">Premium Gift Card</h3>
                            <p class="mb-4">For those who deserve something special!</p>
                            <div class="flex justify-between items-center">
                                <div class="text-3xl font-bold">PKR 5,000</div>
                                <button
                                    class="bg-white text-purple-600 px-4 py-2 rounded-lg font-semibold hover:bg-gray-100">Buy
                                    Now</button>
                            </div>
                        </div>
                    </div>

                    <!-- Gift Card 3 -->
                    <div
                        class="bg-gradient-to-br from-green-500 to-green-700 text-white rounded-lg shadow-lg overflow-hidden">
                        <div class="p-6">
                            <h3 class="text-2xl font-bold mb-2">Custom Amount</h3>
                            <p class="mb-4">Choose any amount between PKR 500 - PKR 50,000</p>
                            <div class="flex justify-between items-center">
                                <input type="number" placeholder="Enter amount"
                                    class="px-3 py-2 rounded-lg text-gray-800 w-32">
                                <button
                                    class="bg-white text-green-600 px-4 py-2 rounded-lg font-semibold hover:bg-gray-100">Buy
                                    Now</button>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="bg-white p-8 rounded-lg shadow-lg max-w-4xl mx-auto mt-12">
                    <h2 class="text-2xl font-bold text-gray-800 mb-4">How Gift Cards Work</h2>
                    <ul class="space-y-4">
                        <li class="flex items-start">
                            <div class="bg-orange-500 text-white rounded-full p-2 mr-4">
                                <i class="fas fa-gift"></i>
                            </div>
                            <div>
                                <h3 class="font-semibold text-gray-800">Purchase a Gift Card</h3>
                                <p class="text-gray-600">Choose from fixed amounts or create a custom value card.</p>
                            </div>
                        </li>
                        <li class="flex items-start">
                            <div class="bg-orange-500 text-white rounded-full p-2 mr-4">
                                <i class="fas fa-envelope"></i>
                            </div>
                            <div>
                                <h3 class="font-semibold text-gray-800">Deliver Instantly</h3>
                                <p class="text-gray-600">Send via email or print at home - delivery is immediate.</p>
                            </div>
                        </li>
                        <li class="flex items-start">
                            <div class="bg-orange-500 text-white rounded-full p-2 mr-4">
                                <i class="fas fa-shopping-cart"></i>
                            </div>
                            <div>
                                <h3 class="font-semibold text-gray-800">Redeem Anywhere</h3>
                                <p class="text-gray-600">Use on ApnaStore.pk for millions of products.</p>
                            </div>
                        </li>
                    </ul>
                </div>
            </div>
        </div>

        <!-- Sell Page -->
        <div id="sell" class="page">
            <div class="container mx-auto px-6 py-12">
                <h1 class="text-4xl font-bold text-gray-800 mb-8 text-center">Sell on ApnaStore</h1>

                <div class="bg-white p-8 rounded-lg shadow-lg max-w-4xl mx-auto mb-12">
                    <h2 class="text-2xl font-bold text-gray-800 mb-6">Start Selling Today</h2>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                        <!-- Step 1 -->
                        <div class="bg-gray-50 p-6 rounded-lg">
                            <div
                                class="bg-orange-500 text-white rounded-full w-10 h-10 flex items-center justify-center mb-4">
                                1</div>
                            <h3 class="font-semibold text-lg mb-2">Create Your Account</h3>
                            <p class="text-gray-600">Register as a seller in just 5 minutes with basic information.</p>
                        </div>

                        <!-- Step 2 -->
                        <div class="bg-gray-50 p-6 rounded-lg">
                            <div
                                class="bg-orange-500 text-white rounded-full w-10 h-10 flex items-center justify-center mb-4">
                                2</div>
                            <h3 class="font-semibold text-lg mb-2">List Your Products</h3>
                            <p class="text-gray-600">Add your products with images, descriptions and pricing.</p>
                        </div>

                        <!-- Step 3 -->
                        <div class="bg-gray-50 p-6 rounded-lg">
                            <div
                                class="bg-orange-500 text-white rounded-full w-10 h-10 flex items-center justify-center mb-4">
                                3</div>
                            <h3 class="font-semibold text-lg mb-2">Start Selling</h3>
                            <p class="text-gray-600">We handle payments, delivery and customer service for you.</p>
                        </div>
                    </div>
                </div>

                <div class="bg-white p-8 rounded-lg shadow-lg max-w-4xl mx-auto">
                    <h2 class="text-2xl font-bold text-gray-800 mb-6">Why Sell With Us?</h2>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                        <div class="flex items-start">
                            <div class="text-orange-500 text-2xl mr-4">
                                <i class="fas fa-users"></i>
                            </div>
                            <div>
                                <h3 class="font-semibold text-lg mb-2">Millions of Customers</h3>
                                <p class="text-gray-600">Access to over 10 million active shoppers across Pakistan.</p>
                            </div>
                        </div>
                        <div class="flex items-start">
                            <div class="text-orange-500 text-2xl mr-4">
                                <i class="fas fa-truck"></i>
                            </div>
                            <div>
                                <h3 class="font-semibold text-lg mb-2">Easy Logistics</h3>
                                <p class="text-gray-600">Our delivery network reaches every corner of the country.</p>
                            </div>
                        </div>
                        <div class="flex items-start">
                            <div class="text-orange-500 text-2xl mr-4">
                                <i class="fas fa-shield-alt"></i>
                            </div>
                            <div>
                                <h3 class="font-semibold text-lg mb-2">Secure Payments</h3>
                                <p class="text-gray-600">Get paid directly to your bank account every week.</p>
                            </div>
                        </div>
                        <div class="flex items-start">
                            <div class="text-orange-500 text-2xl mr-4">
                                <i class="fas fa-chart-line"></i>
                            </div>
                            <div>
                                <h3 class="font-semibold text-lg mb-2">Growth Tools</h3>
                                <p class="text-gray-600">Access to analytics and marketing tools to grow your business.
                                </p>
                            </div>
                        </div>
                    </div>

                    <div class="mt-10 text-center">
                        <button
                            class="bg-orange-500 hover:bg-orange-600 text-white font-bold py-3 px-8 rounded-lg text-lg">
                            Start Selling Now
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <!-- Footer -->
    <footer class="bg-gray-900 text-white">
        <div class="container mx-auto px-6 py-10">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8 text-center md:text-left">
                <div>
                    <h3 class="text-lg font-semibold mb-4">Get to Know Us</h3>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white" onclick="showPage('about')">About Us</a>
                        </li>
                        <li><a href="#" class="text-gray-400 hover:text-white">Careers</a></li>
                    </ul>
                </div>
                <div>
                    <h3 class="text-lg font-semibold mb-4">Connect with Us</h3>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white">Facebook</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white">Twitter</a></li>
                    </ul>
                </div>
                <div>
                    <h3 class="text-lg font-semibold mb-4">Make Money with Us</h3>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white" onclick="showPage('sell')">Become a
                                Seller</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white">Affiliate Program</a></li>
                    </ul>
                </div>
                <div>
                    <h3 class="text-lg font-semibold mb-4">Let Us Help You</h3>
                    <ul class="space-y-2">
                        <li><a href="#" class="text-gray-400 hover:text-white">Your Account</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-white" onclick="showPage('contact')">Help</a>
                        </li>
                    </ul>
                </div>
            </div>
            <div class="border-t border-gray-700 mt-8 pt-6 text-center text-gray-400">
                <p>&copy; 2024 ApnaStore. All Rights Reserved.</p>
            </div>
        </div>
    </footer>

    <!-- Sign In Modal -->
    <div id="signInModal"
        class="modal fixed inset-0 z-50 flex items-center justify-center bg-black bg-opacity-50 hidden">
        <div class="bg-white rounded-lg shadow-xl w-full max-w-md mx-4 p-8 relative"><button id="closeModalBtn"
                class="absolute top-4 right-4 text-gray-500 hover:text-gray-800"><i
                    class="fa fa-times text-2xl"></i></button>
            <h2 class="text-2xl font-bold text-center mb-6">Sign In</h2>
            <div class="space-y-4"><button
                    class="w-full flex items-center justify-center py-3 px-4 border border-gray-300 rounded-lg shadow-sm hover:bg-gray-50"><i
                        class="fab fa-google text-red-500 mr-3 text-xl"></i><span
                        class="font-semibold text-gray-700">Continue with Google</span></button><button
                    class="w-full flex items-center justify-center py-3 px-4 border border-gray-300 rounded-lg shadow-sm hover:bg-gray-50"><i
                        class="fab fa-facebook text-blue-600 mr-3 text-xl"></i><span
                        class="font-semibold text-gray-700">Continue with Facebook</span></button>
                <div class="flex items-center my-4">
                    <hr class="flex-grow border-t border-gray-300"><span class="px-3 text-gray-500">OR</span>
                    <hr class="flex-grow border-t border-gray-300">
                </div>
                <div><label for="email" class="block text-sm font-medium text-gray-700">Email Address</label><input
                        type="email" id="email"
                        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-orange-500 focus:border-orange-500">
                </div>
                <div><label for="password" class="block text-sm font-medium text-gray-700">Password</label><input
                        type="password" id="password"
                        class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-orange-500 focus:border-orange-500">
                </div><button
                    class="w-full bg-orange-500 text-white font-bold py-3 rounded-lg hover:bg-orange-600 transition duration-300">Sign
                    In</button>
                <p class="text-center text-sm text-gray-600 mt-4">New to ApnaStore? <a href="#"
                        class="font-medium text-blue-600 hover:text-blue-500">Create a new account</a></p>
            </div>
        </div>
    </div>

    <script>
        // --- Page Navigation ---
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => page.classList.remove('active'));
            document.getElementById(pageId)?.classList.add('active');
            document.getElementById('mobile-menu').classList.add('hidden');
            window.scrollTo(0, 0);
        }

        // --- Mobile Menu ---
        document.getElementById('mobile-menu-button').addEventListener('click', () => {
            const menu = document.getElementById('mobile-menu');
            menu.classList.toggle('hidden');
            // Populate mobile menu with nav links if it's empty
            if (!menu.innerHTML) {
                const nav = document.querySelector('nav.bg-gray-800 .container');
                menu.innerHTML = nav.innerHTML;
            }
        });

        // --- Sign In Modal ---
        const signInModal = document.getElementById('signInModal');
        const closeModalBtn = document.getElementById('closeModalBtn');
        document.getElementById('signInBtn').addEventListener('click', () => signInModal.classList.remove('hidden'));
        closeModalBtn.addEventListener('click', () => signInModal.classList.add('hidden'));
        signInModal.addEventListener('click', (e) => { if (e.target === signInModal) signInModal.classList.add('hidden'); });

        // --- Image Slider ---
        let slideIndex = 0;
        let slideInterval;
        const slides = document.querySelectorAll(".slide");
        const dotsContainer = document.querySelector(".dots-container");

        function createDots() {
            slides.forEach((_, i) => {
                const dot = document.createElement("span");
                dot.classList.add("dot");
                dot.addEventListener("click", () => {
                    currentSlide(i);
                    resetInterval();
                });
                dotsContainer.appendChild(dot);
            });
        }

        function showSlides() {
            slides.forEach(slide => slide.style.display = "none");
            const dots = document.querySelectorAll(".dot");
            dots.forEach(dot => dot.classList.remove("active"));

            slideIndex++;
            if (slideIndex > slides.length) { slideIndex = 1 }

            slides[slideIndex - 1].style.display = "block";
            dots[slideIndex - 1].classList.add("active");
        }

        function plusSlides(n) {
            slideIndex += n - 1;
            if (slideIndex < 0) { slideIndex = slides.length - 1 }
            showSlides();
            resetInterval();
        }

        function currentSlide(n) {
            slideIndex = n;
            showSlides();
            resetInterval();
        }

        function resetInterval() {
            clearInterval(slideInterval);
            slideInterval = setInterval(showSlides, 5000); // Change image every 5 seconds
        }

        // Initial setup
        createDots();
        showSlides();
        resetInterval();

        document.querySelector('.prev').addEventListener('click', () => plusSlides(-1));
        document.querySelector('.next').addEventListener('click', () => plusSlides(1));
    </script>
</body>

</html>
