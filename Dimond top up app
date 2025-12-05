<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Top-Up Center</title>
    <style>
        /* CSS RESET & FONT */
        :root {
            --primary-color: #FBC02D;
            --primary-gradient: linear-gradient(45deg, #FFD700, #FBC02D);
            --primary-glow: 0 0 20px rgba(251, 192, 45, 0.6);
            --text-color: #212121;
            --light-text-color: #757575;
            --bg-color: #F9F9F9;
            --white-color: #FFFFFF;
            --card-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
            --danger-color: #e53935;
            --success-color: #43A047;
        }
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: 'Poppins', sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            overscroll-behavior-y: contain;
        }

        /* UTILITY CLASSES */
        .d-none { display: none !important; }
        .container { max-width: 1200px; margin: 0 auto; padding: 0 15px; }

        /* LOADER */
        .loader-wrapper {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(255, 255, 255, 0.9);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            backdrop-filter: blur(5px);
        }
        .loader {
            border: 8px solid #f3f3f3;
            border-top: 8px solid var(--primary-color);
            border-radius: 50%;
            width: 60px;
            height: 60px;
            animation: spin 1s linear infinite;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* --- AUTH VIEWS --- */
        .auth-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }
        .auth-card {
            background: var(--white-color);
            padding: 40px 30px;
            border-radius: 16px;
            box-shadow: var(--card-shadow);
            width: 100%;
            max-width: 400px;
            text-align: center;
        }
        .auth-title {
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 10px;
            color: var(--primary-color);
            text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
        }
        .auth-subtitle {
            font-size: 1rem;
            color: var(--light-text-color);
            margin-bottom: 30px;
        }
        .form-group {
            margin-bottom: 20px;
            text-align: left;
        }
        .form-group input {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            transition: all 0.3s ease;
        }
        .form-group input:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(251, 192, 45, 0.3);
        }
        .btn {
            width: 100%;
            padding: 12px;
            border: none;
            border-radius: 8px;
            background: var(--primary-gradient);
            color: var(--text-color);
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: var(--primary-glow);
        }
        .auth-link {
            color: var(--primary-color);
            text-decoration: none;
            font-weight: 500;
            cursor: pointer;
        }
        .auth-link:hover { text-decoration: underline; }
        .auth-footer { margin-top: 20px; color: var(--light-text-color); }
        .error-message { color: var(--danger-color); font-size: 0.9rem; margin-top: 10px; min-height: 1.2em; }
        
        /* SPLASH SCREEN */
        #splash-screen {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: var(--bg-color);
            z-index: 10000;
        }
        #splash-logo { font-size: 3rem; font-weight: 700; color: var(--primary-color); }

        /* --- MAIN APP VIEW --- */
        #app-view { padding-bottom: 80px; } /* Space for fixed footer nav */
        
        /* Header */
        .app-header {
            background: var(--white-color);
            padding: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
        }
        .app-logo {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary-color);
        }
        .wallet-balance {
            display: flex;
            align-items: center;
            background: #fff8e1;
            padding: 8px 12px;
            border-radius: 20px;
            font-weight: 600;
            border: 1px solid var(--primary-color);
        }
        .wallet-balance svg { width: 20px; height: 20px; margin-right: 8px; fill: var(--primary-color); }

        /* Notice Bar */
        .notice-bar {
            background: var(--primary-gradient);
            color: var(--text-color);
            padding: 8px 0;
            font-weight: 500;
            font-size: 0.9rem;
            overflow: hidden;
        }

        /* Slider */
        .slider-container {
            position: relative;
            max-width: 1200px;
            margin: 20px auto;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: var(--card-shadow);
        }
        .slider { display: flex; transition: transform 0.5s ease-in-out; }
        .slide { min-width: 100%; }
        .slide img { width: 100%; display: block; aspect-ratio: 16/7; object-fit: cover; }

        /* Product Section */
        .category-title {
            font-size: 1.8rem;
            font-weight: 700;
            margin: 30px 0 15px 0;
            padding-bottom: 5px;
            border-bottom: 3px solid var(--primary-color);
            display: inline-block;
        }
        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            gap: 15px;
        }
        .product-card {
            background: var(--white-color);
            border-radius: 12px;
            overflow: hidden;
            box-shadow: var(--card-shadow);
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: center;
        }
        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.12);
        }
        .product-card img {
            width: 100%;
            aspect-ratio: 1/1;
            object-fit: cover;
        }
        .product-info { padding: 10px; }
        .product-name {
            font-weight: 600;
            font-size: 0.9rem;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        .product-price {
            background: var(--primary-gradient);
            color: var(--text-color);
            font-weight: 700;
            padding: 3px 8px;
            border-radius: 20px;
            display: inline-block;
            margin-top: 8px;
            font-size: 0.9rem;
        }
        .product-card.out-of-stock {
            opacity: 0.5;
            cursor: not-allowed;
            position: relative;
        }
        .product-card.out-of-stock::after {
            content: 'Out of Stock';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: rgba(0,0,0,0.7);
            color: white;
            padding: 5px 10px;
            border-radius: 5px;
            font-size: 0.8rem;
            font-weight: 600;
        }

        /* App Pages (Deposit, Account) */
        .app-page { padding: 20px 15px; }
        .page-title { font-size: 2rem; font-weight: 700; margin-bottom: 20px; }

        /* Deposit Page */
        .payment-tabs { display: flex; border-bottom: 1px solid #ddd; margin-bottom: 20px; }
        .tab-link {
            padding: 10px 20px;
            cursor: pointer;
            font-weight: 600;
            border-bottom: 3px solid transparent;
            transition: all 0.3s ease;
        }
        .tab-link.active {
            color: var(--primary-color);
            border-bottom-color: var(--primary-color);
        }
        .tab-content { display: none; }
        .tab-content.active { display: block; animation: fadeIn 0.5s; }
        .payment-info {
            background: #fff8e1;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            border-left: 5px solid var(--primary-color);
        }
        .payment-info p { margin-bottom: 5px; }
        .payment-info strong { font-size: 1.1rem; }

        /* Account Page */
        .account-info {
            background: var(--white-color);
            padding: 20px;
            border-radius: 12px;
            box-shadow: var(--card-shadow);
            margin-bottom: 20px;
        }
        .history-list { list-style: none; }
        .history-item {
            background: var(--white-color);
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        .status-dot {
            width: 12px; height: 12px;
            border-radius: 50%;
            display: inline-block;
            margin-right: 8px;
        }
        .status-Pending { background-color: #FB8C00; } /* Amber */
        .status-Completed { background-color: var(--success-color); } /* Green */
        .status-Rejected { background-color: var(--danger-color); } /* Red */
        .btn-logout { background: var(--danger-color); color: white; }
        .btn-logout:hover { background: #d32f2f; box-shadow: 0 0 15px rgba(229, 57, 53, 0.5); }


        /* Footer Navigation */
        .footer-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            background: var(--white-color);
            display: flex;
            justify-content: space-around;
            box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.08);
            z-index: 100;
        }
        .nav-item {
            flex: 1;
            text-align: center;
            padding: 10px 0;
            cursor: pointer;
            color: var(--light-text-color);
            transition: color 0.3s ease;
        }
        .nav-item svg { width: 24px; height: 24px; margin-bottom: 2px; }
        .nav-item.active { color: var(--primary-color); }
        .nav-item .nav-text { font-size: 0.75rem; font-weight: 500; }

        /* Modal */
        .modal-overlay {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.6);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
        }
        .modal-overlay.active {
            opacity: 1;
            visibility: visible;
        }
        .modal-content {
            background: var(--white-color);
            padding: 30px;
            border-radius: 16px;
            width: 90%;
            max-width: 450px;
            transform: scale(0.9);
            transition: all 0.3s ease;
        }
        .modal-overlay.active .modal-content {
            transform: scale(1);
        }
        .modal-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px; }
        .modal-title { font-size: 1.5rem; font-weight: 600; }
        .modal-close { font-size: 2rem; cursor: pointer; color: var(--light-text-color); border: none; background: none; }
        .modal-body img { width: 100px; height: 100px; object-fit: cover; border-radius: 8px; float: left; margin-right: 15px; margin-bottom: 15px; }
        .modal-body p { margin-bottom: 5px; }
        .modal-footer { margin-top: 20px; }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body>

    <!-- Splash Screen -->
    <div id="splash-screen">
        <div id="splash-logo">Loading...</div>
    </div>
    
    <!-- Loader -->
    <div id="loader" class="loader-wrapper d-none">
        <div class="loader"></div>
    </div>

    <!-- Authentication Views -->
    <div id="auth-view" class="d-none">
        <!-- Login View -->
        <div id="login-view">
            <div class="auth-container">
                <div class="auth-card">
                    <h1 class="auth-title" id="login-app-name">Welcome</h1>
                    <p class="auth-subtitle">Sign in to continue</p>
                    <form id="login-form">
                        <div class="form-group">
                            <input type="email" id="login-email" placeholder="Email" required>
                        </div>
                        <div class="form-group">
                            <input type="password" id="login-password" placeholder="Password" required>
                        </div>
                        <div class="error-message" id="login-error"></div>
                        <button type="submit" class="btn">Login</button>
                    </form>
                    <p class="auth-footer">
                        <a href="#" class="auth-link" id="forgot-password-link">Forgot Password?</a>
                    </p>
                    <p class="auth-footer">
                        Don't have an account? <a href="#" class="auth-link" id="show-signup-link">Sign Up</a>
                    </p>
                </div>
            </div>
        </div>

        <!-- Sign Up View -->
        <div id="signup-view" class="d-none">
            <div class="auth-container">
                <div class="auth-card">
                    <h1 class="auth-title" id="signup-app-name">Create Account</h1>
                    <p class="auth-subtitle">Get started with your new account</p>
                    <form id="signup-form">
                        <div class="form-group">
                            <input type="email" id="signup-email" placeholder="Email" required>
                        </div>
                        <div class="form-group">
                            <input type="password" id="signup-password" placeholder="Password" required>
                        </div>
                        <div class="form-group">
                            <input type="password" id="signup-confirm-password" placeholder="Confirm Password" required>
                        </div>
                        <div class="error-message" id="signup-error"></div>
                        <button type="submit" class="btn">Sign Up</button>
                    </form>
                    <p class="auth-footer">
                        Already have an account? <a href="#" class="auth-link" id="show-login-link">Login</a>
                    </p>
                </div>
            </div>
        </div>
        
        <!-- Forgot Password View -->
        <div id="forgot-password-view" class="d-none">
            <div class="auth-container">
                <div class="auth-card">
                    <h1 class="auth-title">Reset Password</h1>
                    <p class="auth-subtitle">Enter your email to receive a reset link</p>
                    <form id="forgot-password-form">
                        <div class="form-group">
                            <input type="email" id="reset-email" placeholder="Email" required>
                        </div>
                        <div class="error-message" id="reset-message"></div>
                        <button type="submit" class="btn">Send Reset Link</button>
                    </form>
                    <p class="auth-footer">
                        <a href="#" class="auth-link" id="back-to-login-link">Back to Login</a>
                    </p>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Main Application View -->
    <div id="app-view" class="d-none">
        <!-- Header -->
        <header class="app-header">
            <div class="app-logo" id="app-name-header">App</div>
            <div class="wallet-balance">
                <svg viewBox="0 0 24 24"><path d="M21 18v1c0 1.1-.9 2-2 2H5c-1.11 0-2-.9-2-2V5c0-1.1.89-2 2-2h14c1.1 0 2 .9 2 2v1h-9c-1.11 0-2 .9-2 2v8c0 1.1.89 2 2 2h9zm-9-2h10V8H12v8zm4-2.5c-.83 0-1.5-.67-1.5-1.5s.67-1.5 1.5-1.5 1.5.67 1.5 1.5-.67 1.5-1.5 1.5z"/></svg>
                <span id="wallet-balance-value">0</span>
            </div>
        </header>

        <!-- Notice Bar -->
        <div class="notice-bar">
            <marquee id="notice-text">Welcome to our top-up center!</marquee>
        </div>

        <main id="main-content">
            <!-- Home Page -->
            <div id="home-page" class="app-page">
                <div class="slider-container">
                    <div class="slider" id="image-slider">
                        <!-- JS will populate this -->
                    </div>
                </div>
                <div id="product-list" class="container">
                    <!-- JS will populate this -->
                </div>
            </div>
            
            <!-- Deposit Page -->
            <div id="deposit-page" class="app-page d-none">
                <h1 class="page-title">Add Money</h1>
                <div class="payment-tabs">
                    <div class="tab-link active" data-tab="bkash">Bkash</div>
                    <div class="tab-link" data-tab="nagad">Nagad</div>
                    <div class="tab-link" data-tab="rocket">Rocket</div>
                </div>
                
                <div id="bkash-tab" class="tab-content active">
                    <div class="payment-info">
                        <p>Send money to our Bkash Number:</p>
                        <strong id="bkash-number">Loading...</strong>
                        <p style="margin-top:10px;">Minimum deposit amount: <strong>৳ <span class="min-deposit-display">...</span></strong></p>
                    </div>
                    <form class="deposit-form" data-method="Bkash">
                        <div class="form-group">
                            <input type="number" placeholder="Amount" required>
                        </div>
                        <div class="form-group">
                            <input type="text" placeholder="Transaction ID" required>
                        </div>
                        <button type="submit" class="btn">Submit</button>
                    </form>
                </div>
                
                <div id="nagad-tab" class="tab-content">
                     <div class="payment-info">
                        <p>Send money to our Nagad Number:</p>
                        <strong id="nagad-number">Loading...</strong>
                        <p style="margin-top:10px;">Minimum deposit amount: <strong>৳ <span class="min-deposit-display">...</span></strong></p>
                    </div>
                    <form class="deposit-form" data-method="Nagad">
                        <div class="form-group">
                            <input type="number" placeholder="Amount" required>
                        </div>
                        <div class="form-group">
                            <input type="text" placeholder="Transaction ID" required>
                        </div>
                        <button type="submit" class="btn">Submit</button>
                    </form>
                </div>
                
                <div id="rocket-tab" class="tab-content">
                     <div class="payment-info">
                        <p>Send money to our Rocket Number:</p>
                        <strong id="rocket-number">Loading...</strong>
                        <p style="margin-top:10px;">Minimum deposit amount: <strong>৳ <span class="min-deposit-display">...</span></strong></p>
                    </div>
                    <form class="deposit-form" data-method="Rocket">
                        <div class="form-group">
                            <input type="number" placeholder="Amount" required>
                        </div>
                        <div class="form-group">
                            <input type="text" placeholder="Transaction ID" required>
                        </div>
                        <button type="submit" class="btn">Submit</button>
                    </form>
                </div>
            </div>

            <!-- Account Page -->
            <div id="account-page" class="app-page d-none">
                <h1 class="page-title">My Account</h1>
                <div class="account-info">
                    <p><strong>Email:</strong> <span id="user-email-display"></span></p>
                </div>

                <h2>My Orders</h2>
                <ul id="order-history-list" class="history-list">
                    <!-- JS populates this -->
                </ul>

                <h2 style="margin-top: 20px;">Deposit History</h2>
                <ul id="deposit-history-list" class="history-list">
                   <!-- JS populates this -->
                </ul>

                <button id="logout-btn" class="btn btn-logout" style="margin-top: 30px;">Logout</button>
            </div>
        </main>

        <!-- Footer Navigation -->
        <nav class="footer-nav">
            <div class="nav-item active" data-page="home-page">
                <svg viewBox="0 0 24 24" fill="currentColor"><path d="M10 20v-6h4v6h5v-8h3L12 3 2 12h3v8z"/></svg>
                <div class="nav-text">Home</div>
            </div>
            <div class="nav-item" data-page="deposit-page">
                <svg viewBox="0 0 24 24" fill="currentColor"><path d="M20 4H4c-1.11 0-1.99.89-1.99 2L2 18c0 1.11.89 2 2 2h16c1.11 0 2-.89 2-2V6c0-1.11-.89-2-2-2zm0 14H4v-6h16v6zm0-10H4V6h16v2z"/></svg>
                <div class="nav-text">Add Money</div>
            </div>
            <div class="nav-item" data-page="account-page">
                <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/></svg>
                <div class="nav-text">Account</div>
            </div>
        </nav>
    </div>

    <!-- Order Modal -->
    <div id="order-modal" class="modal-overlay">
        <div class="modal-content">
            <div class="modal-header">
                <h2 class="modal-title">Confirm Order</h2>
                <button class="modal-close">&times;</button>
            </div>
            <div class="modal-body" id="order-modal-body">
                <!-- JS populates this -->
            </div>
            <div class="modal-footer">
                <form id="order-form">
                    <div class="form-group">
                        <input type="text" id="player-id" placeholder="Enter Your Player ID" required>
                    </div>
                    <button type="submit" class="btn">Confirm Order</button>
                </form>
            </div>
        </div>
    </div>
    
    <!-- Firebase SDKs -->
    <script src="https://www.gstatic.com/firebasejs/9.15.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.15.0/firebase-auth-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.15.0/firebase-firestore-compat.js"></script>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            // --- FIREBASE CONFIGURATION ---
            const firebaseConfig = {
  apiKey: "AIzaSyA6SrwtJVTfLP8Z04Li83S_X-vlxd1HeL0",
  authDomain: "admin-panel-cod-7fa98.firebaseapp.com",
  projectId: "admin-panel-cod-7fa98",
  storageBucket: "admin-panel-cod-7fa98.firebasestorage.app",
  messagingSenderId: "612649340436",
  appId: "1:612649340436:web:d21641de119042eca8e101",
  measurementId: "G-HMLQWW8GZT"
};
            // --- INITIALIZE FIREBASE ---
            firebase.initializeApp(firebaseConfig);
            const auth = firebase.auth();
            const db = firebase.firestore();

            // --- GLOBAL STATE ---
            let currentUser = null;
            let currentProduct = null;
            let globalSettings = {}; // To store settings like min deposit
            
            // --- UI ELEMENT SELECTORS ---
            const splashScreen = document.getElementById('splash-screen');
            const splashLogo = document.getElementById('splash-logo');
            const loader = document.getElementById('loader');
            const authView = document.getElementById('auth-view');
            const appView = document.getElementById('app-view');
            const mainContent = document.getElementById('main-content');
            
            // --- UTILITY FUNCTIONS ---
            const showLoader = () => loader.classList.remove('d-none');
            const hideLoader = () => loader.classList.add('d-none');
            const showAlert = (message, type = 'success') => {
                alert(message); // Simple alert, can be replaced with a custom modal
            };

            // --- VIEW/PAGE SWITCHING LOGIC ---
            function showAuthSubView(viewId) {
                ['login-view', 'signup-view', 'forgot-password-view'].forEach(id => {
                    document.getElementById(id).classList.add('d-none');
                });
                document.getElementById(viewId).classList.remove('d-none');
            }

            function switchAppPage(pageId) {
                mainContent.querySelectorAll('.app-page').forEach(page => page.classList.add('d-none'));
                document.getElementById(pageId).classList.remove('d-none');
                document.querySelectorAll('.footer-nav .nav-item').forEach(item => {
                    item.classList.toggle('active', item.dataset.page === pageId);
                });
            }

            // --- AUTHENTICATION ---
            auth.onAuthStateChanged(user => {
                if (user) {
                    currentUser = user;
                    authView.classList.add('d-none');
                    appView.classList.remove('d-none');
                    initializeApp();
                } else {
                    currentUser = null;
                    authView.classList.remove('d-none');
                    appView.classList.add('d-none');
                    showAuthSubView('login-view');
                    splashScreen.classList.add('d-none');
                }
            });

            // Login, Signup, Logout, Forgot Password (No changes here)
            document.getElementById('login-form').addEventListener('submit', (e) => { e.preventDefault(); showLoader(); const email = document.getElementById('login-email').value; const password = document.getElementById('login-password').value; auth.signInWithEmailAndPassword(email, password).catch(error => { document.getElementById('login-error').textContent = error.message; }).finally(hideLoader); });
            document.getElementById('signup-form').addEventListener('submit', (e) => { e.preventDefault(); const email = document.getElementById('signup-email').value; const password = document.getElementById('signup-password').value; const confirmPassword = document.getElementById('signup-confirm-password').value; const errorEl = document.getElementById('signup-error'); if (password !== confirmPassword) { errorEl.textContent = "Passwords do not match."; return; } showLoader(); auth.createUserWithEmailAndPassword(email, password).then(userCredential => { return db.collection('users').doc(userCredential.user.uid).set({ email: userCredential.user.email, walletBalance: 0 }); }).catch(error => { errorEl.textContent = error.message; }).finally(hideLoader); });
            document.getElementById('logout-btn').addEventListener('click', () => { auth.signOut(); });
            document.getElementById('forgot-password-form').addEventListener('submit', (e) => { e.preventDefault(); showLoader(); const email = document.getElementById('reset-email').value; const messageEl = document.getElementById('reset-message'); auth.sendPasswordResetEmail(email).then(() => { messageEl.style.color = 'var(--success-color)'; messageEl.textContent = 'Password reset email sent! Check your inbox.'; }).catch(error => { messageEl.style.color = 'var(--danger-color)'; messageEl.textContent = error.message; }).finally(hideLoader); });
            document.getElementById('show-signup-link').addEventListener('click', (e) => { e.preventDefault(); showAuthSubView('signup-view'); });
            document.getElementById('show-login-link').addEventListener('click', (e) => { e.preventDefault(); showAuthSubView('login-view'); });
            document.getElementById('forgot-password-link').addEventListener('click', (e) => { e.preventDefault(); showAuthSubView('forgot-password-view'); });
            document.getElementById('back-to-login-link').addEventListener('click', (e) => { e.preventDefault(); showAuthSubView('login-view'); });
            
            // --- FIRESTORE DATA & APP LOGIC ---
            async function initializeApp() {
                showLoader();
                await loadSettings();
                await loadProducts();
                listenToUserData();
                switchAppPage('home-page');
                splashScreen.classList.add('d-none');
                hideLoader();
            }

            // Load Global Settings
            async function loadSettings() {
                try {
                    const doc = await db.collection('settings').doc('global').get();
                    if (doc.exists) {
                        const settings = doc.data();
                        globalSettings = settings; // Store settings globally
                        
                        // Update UI
                        const appName = settings.appName || 'TopUp Center';
                        splashLogo.textContent = appName;
                        document.getElementById('login-app-name').textContent = appName;
                        document.getElementById('signup-app-name').textContent = `Join ${appName}`;
                        document.getElementById('app-name-header').textContent = appName;
                        document.getElementById('notice-text').textContent = settings.notice || '';

                        // Slider
                        const slider = document.getElementById('image-slider');
                        slider.innerHTML = '';
                        [settings.slider_url_1, settings.slider_url_2, settings.slider_url_3].forEach(url => {
                            if (url) {
                                slider.innerHTML += `<div class="slide"><img src="${url}" alt="Banner"></div>`;
                            }
                        });
                        initSlider();

                        // Payment numbers
                        document.getElementById('bkash-number').textContent = settings.payment_numbers?.bkash || 'Not available';
                        document.getElementById('nagad-number').textContent = settings.payment_numbers?.nagad || 'Not available';
                        document.getElementById('rocket-number').textContent = settings.payment_numbers?.rocket || 'Not available';
                        
                        // ** NEW: Update Minimum Deposit Display **
                        const minDeposit = settings.minDepositAmount || 0;
                        document.querySelectorAll('.min-deposit-display').forEach(el => {
                            el.textContent = minDeposit;
                        });

                    } else {
                        console.log("No settings document!");
                    }
                } catch (error) {
                    console.error("Error loading settings: ", error);
                }
            }

            // Load Products
            async function loadProducts() {
                try {
                    const snapshot = await db.collection('products').orderBy('price').get();
                    const products = snapshot.docs.map(doc => ({ id: doc.id, ...doc.data() }));
                    
                    const productsByCategory = products.reduce((acc, product) => {
                        (acc[product.category] = acc[product.category] || []).push(product);
                        return acc;
                    }, {});

                    const productListEl = document.getElementById('product-list');
                    productListEl.innerHTML = '';
                    for (const category in productsByCategory) {
                        productListEl.innerHTML += `<h2 class="category-title">${category}</h2>`;
                        const grid = document.createElement('div');
                        grid.className = 'product-grid';
                        productsByCategory[category].forEach(product => {
                            const isOutOfStock = product.status === 'Out of Stock';
                            grid.innerHTML += `
                                <div class="product-card ${isOutOfStock ? 'out-of-stock' : ''}" 
                                     data-product-id="${product.id}" 
                                     data-product-name="${product.name}" 
                                     data-product-price="${product.price}" 
                                     data-product-image="${product.imageUrl}">
                                    <img src="${product.imageUrl}" alt="${product.name}">
                                    <div class="product-info">
                                        <div class="product-name">${product.name}</div>
                                        <div class="product-price">৳ ${product.price}</div>
                                    </div>
                                </div>
                            `;
                        });
                        productListEl.appendChild(grid);
                    }
                } catch (error) {
                    console.error("Error loading products: ", error);
                }
            }
            
            // Listen to User Data (Wallet, Orders, Deposits)
            function listenToUserData() {
                if (!currentUser) return;
                db.collection('users').doc(currentUser.uid).onSnapshot(doc => { const userData = doc.data(); if (userData) { document.getElementById('wallet-balance-value').textContent = `৳ ${userData.walletBalance.toFixed(2)}`; document.getElementById('user-email-display').textContent = userData.email; } });
                db.collection('users').doc(currentUser.uid).collection('orders').orderBy('timestamp', 'desc').onSnapshot(snapshot => { const orderListEl = document.getElementById('order-history-list'); orderListEl.innerHTML = ''; if (snapshot.empty) { orderListEl.innerHTML = '<li>No orders yet.</li>'; return; } snapshot.forEach(doc => { const order = doc.data(); orderListEl.innerHTML += `<li class="history-item"><div><strong>${order.productName}</strong><br><small>ID: ${order.playerID} | ৳ ${order.price}</small></div><span class="status"><span class="status-dot status-${order.status}"></span>${order.status}</span></li>`; }); });
                db.collection('users').doc(currentUser.uid).collection('deposits').orderBy('timestamp', 'desc').onSnapshot(snapshot => { const depositListEl = document.getElementById('deposit-history-list'); depositListEl.innerHTML = ''; if (snapshot.empty) { depositListEl.innerHTML = '<li>No deposits yet.</li>'; return; } snapshot.forEach(doc => { const deposit = doc.data(); depositListEl.innerHTML += `<li class="history-item"><div><strong>${deposit.method} - ৳ ${deposit.amount}</strong><br><small>TnxID: ${deposit.transactionId}</small></div><span class="status"><span class="status-dot status-${deposit.status}"></span>${deposit.status}</span></li>`; }); });
            }
            
            // --- INTERACTIONS ---

            // Footer Navigation
            document.querySelector('.footer-nav').addEventListener('click', (e) => { const navItem = e.target.closest('.nav-item'); if (navItem) { switchAppPage(navItem.dataset.page); } });
            // Deposit Tabs
            document.querySelector('.payment-tabs').addEventListener('click', (e) => { const tabLink = e.target.closest('.tab-link'); if (tabLink) { const tabId = tabLink.dataset.tab; document.querySelectorAll('.tab-link').forEach(t => t.classList.remove('active')); tabLink.classList.add('active'); document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active')); document.getElementById(`${tabId}-tab`).classList.add('active'); } });
            
            // Deposit Form Submission
            document.querySelectorAll('.deposit-form').forEach(form => {
                form.addEventListener('submit', async (e) => {
                    e.preventDefault();
                    showLoader();
                    const amount = parseFloat(e.target.querySelector('input[type="number"]').value);
                    const transactionId = e.target.querySelector('input[type="text"]').value;
                    const method = e.target.dataset.method;

                    // ** NEW: Minimum Deposit Check **
                    const minDepositAmount = globalSettings.minDepositAmount || 0;
                    if (amount < minDepositAmount) {
                        showAlert(`Minimum deposit amount is ৳${minDepositAmount}.`, 'error');
                        hideLoader();
                        return;
                    }
                    if (isNaN(amount) || amount <= 0) { showAlert('Please enter a valid amount.', 'error'); hideLoader(); return; }

                    const depositData = { uid: currentUser.uid, userEmail: currentUser.email, amount: amount, method: method, transactionId: transactionId, status: 'Pending', timestamp: firebase.firestore.FieldValue.serverTimestamp() };
                    try {
                        const topLevelDocRef = db.collection('deposits').doc();
                        const userSubDocRef = db.collection('users').doc(currentUser.uid).collection('deposits').doc(topLevelDocRef.id);
                        const batch = db.batch();
                        batch.set(topLevelDocRef, depositData);
                        batch.set(userSubDocRef, depositData);
                        await batch.commit();
                        showAlert('Deposit request submitted successfully!', 'success');
                        form.reset();
                        switchAppPage('account-page');
                    } catch (error) { console.error("Error submitting deposit: ", error); showAlert('Failed to submit deposit request. Please try again.', 'error'); } 
                    finally { hideLoader(); }
                });
            });

            // Order Modal Logic
            const orderModal = document.getElementById('order-modal');
            const orderModalBody = document.getElementById('order-modal-body');
            document.getElementById('product-list').addEventListener('click', (e) => { const card = e.target.closest('.product-card:not(.out-of-stock)'); if (card) { currentProduct = { id: card.dataset.productId, name: card.dataset.productName, price: parseFloat(card.dataset.productPrice), imageUrl: card.dataset.productImage, }; orderModalBody.innerHTML = `<img src="${currentProduct.imageUrl}" alt="${currentProduct.name}"><p><strong>Product:</strong> ${currentProduct.name}</p><p><strong>Price:</strong> ৳ ${currentProduct.price}</p><div style="clear: both;"></div>`; orderModal.classList.add('active'); } });
            orderModal.querySelector('.modal-close').addEventListener('click', () => { orderModal.classList.remove('active'); currentProduct = null; });
            orderModal.addEventListener('click', (e) => { if (e.target === orderModal) { orderModal.classList.remove('active'); currentProduct = null; } });
            
            // Place Order
            document.getElementById('order-form').addEventListener('submit', (e) => {
                e.preventDefault();
                showLoader();
                const playerID = document.getElementById('player-id').value;
                if (!playerID.trim()) { showAlert('Please enter a Player ID.', 'error'); hideLoader(); return; }
                
                const userRef = db.collection('users').doc(currentUser.uid);
                
                db.runTransaction(async (transaction) => {
                    const userDoc = await transaction.get(userRef);
                    if (!userDoc.exists) { throw "User document does not exist!"; }

                    const currentBalance = userDoc.data().walletBalance;
                    
                    // ** NEW: Specific balance checks **
                    if (currentBalance <= 0) {
                        throw "ZERO_BALANCE";
                    }
                    if (currentBalance < currentProduct.price) {
                        throw "INSUFFICIENT_BALANCE";
                    }

                    const newBalance = currentBalance - currentProduct.price;
                    transaction.update(userRef, { walletBalance: newBalance });
                    
                    const orderData = { uid: currentUser.uid, userEmail: currentUser.email, playerID: playerID, productName: currentProduct.name, productId: currentProduct.id, price: currentProduct.price, status: 'Pending', timestamp: firebase.firestore.FieldValue.serverTimestamp() };
                    const newOrderRef = db.collection('orders').doc();
                    transaction.set(newOrderRef, orderData);
                    transaction.set(userRef.collection('orders').doc(newOrderRef.id), orderData);
                    
                }).then(() => {
                    showAlert('Order placed successfully!', 'success');
                    orderModal.classList.remove('active');
                    document.getElementById('order-form').reset();
                }).catch(error => {
                    console.error("Order transaction failed: ", error);
                    // ** NEW: Custom error messages **
                    let errorMessage = `Order failed: ${error}`;
                    if (error === "ZERO_BALANCE") {
                        errorMessage = 'আপনার ওয়ালেটে কোন টাকা নেই। দয়া করে টাকা যোগ করুন। (Your wallet has no money. Please add money.)';
                    } else if (error === "INSUFFICIENT_BALANCE") {
                         errorMessage = 'Insufficient balance to place this order.';
                    }
                    showAlert(errorMessage, 'error');
                }).finally(hideLoader);
            });
            
            // Simple Image Slider
            function initSlider() {
                const slider = document.querySelector('.slider');
                if (!slider || slider.children.length <= 1) return;
                let currentIndex = 0;
                const slides = document.querySelectorAll('.slide');
                const totalSlides = slides.length;
                setInterval(() => { currentIndex = (currentIndex + 1) % totalSlides; slider.style.transform = `translateX(-${currentIndex * 100}%)`; }, 3000);
            }

        });
    </script>
</body>
</html>
