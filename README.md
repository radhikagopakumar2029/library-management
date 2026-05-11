<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Library Management System</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Login Page -->
    <div id="loginPage" class="page active">
        <div class="login-container">
            <h1>Library Management System</h1>
            <form id="loginForm" onsubmit="handleLogin(event)">
                <div class="form-group">
                    <label for="identifier">Name, Email, or Phone Number:</label>
                    <input type="text" id="identifier" placeholder="Enter your name, email, or phone" required>
                </div>
                
                <div class="form-group" id="otpGroup" style="display:none;">
                    <label for="otp">Enter OTP:</label>
                    <input type="text" id="otp" placeholder="Enter OTP">
                </div>
                
                <div class="form-group">
                    <label for="password">Password:</label>
                    <input type="password" id="password" placeholder="Enter your password" required>
                </div>
                
                <button type="submit" class="btn btn-primary">Login</button>
                <p class="signup-link">Don't have an account? <a href="#" onclick="showSignup(event)">Sign up</a></p>
            </form>
        </div>
    </div>

    <!-- Genre Selection Page -->
    <div id="genrePage" class="page">
        <div class="container">
            <header>
                <h1>Select Genre</h1>
                <div class="user-menu">
                    <span id="userName">User</span>
                    <button class="btn btn-secondary" onclick="logout()">Logout</button>
                </div>
            </header>
            <nav class="navbar">
                <a href="#" onclick="showPage('cartPage')">🛒 Cart</a>
                <a href="#" onclick="showPage('returnPage')">📖 My Books</a>
                <a href="#" onclick="showPage('contactPage')">📞 Contact Us</a>
            </nav>
            <div class="genres-grid">
                <div class="genre-card" onclick="selectGenre('Fiction')">
                    <h3>Fiction</h3>
                    <p>Explore stories and novels</p>
                </div>
                <div class="genre-card" onclick="selectGenre('Science')">
                    <h3>Science</h3>
                    <p>Discover scientific knowledge</p>
                </div>
                <div class="genre-card" onclick="selectGenre('History')">
                    <h3>History</h3>
                    <p>Learn from the past</p>
                </div>
                <div class="genre-card" onclick="selectGenre('Biography')">
                    <h3>Biography</h3>
                    <p>Read inspiring life stories</p>
                </div>
                <div class="genre-card" onclick="selectGenre('Technology')">
                    <h3>Technology</h3>
                    <p>Stay updated with tech trends</p>
                </div>
                <div class="genre-card" onclick="selectGenre('Self-Help')">
                    <h3>Self-Help</h3>
                    <p>Improve yourself</p>
                </div>
            </div>
        </div>
    </div>

    <!-- Books Available Page -->
    <div id="booksPage" class="page">
        <div class="container">
            <header>
                <button class="btn btn-secondary" onclick="showPage('genrePage')">← Back</button>
                <h1 id="genreTitle">Books</h1>
                <div class="user-menu">
                    <span id="userName2">User</span>
                    <button class="btn btn-secondary" onclick="logout()">Logout</button>
                </div>
            </header>
            <nav class="navbar">
                <a href="#" onclick="showPage('cartPage')">🛒 Cart</a>
                <a href="#" onclick="showPage('returnPage')">📖 My Books</a>
                <a href="#" onclick="showPage('contactPage')">📞 Contact Us</a>
            </nav>
            <div class="books-grid" id="booksGrid">
                <!-- Books will be loaded here -->
            </div>
        </div>
    </div>

    <!-- Book Order Page -->
    <div id="orderPage" class="page">
        <div class="container">
            <header>
                <button class="btn btn-secondary" onclick="showPage('booksPage')">← Back</button>
                <h1>Order Book</h1>
            </header>
            <div class="order-form">
                <div class="book-details" id="bookDetails"></div>
                <form onsubmit="handleOrder(event)">
                    <h3>Delivery Address</h3>
                    <div class="form-group">
                        <label for="fullName">Full Name:</label>
                        <input type="text" id="fullName" required>
                    </div>
                    <div class="form-group">
                        <label for="email">Email:</label>
                        <input type="email" id="email" required>
                    </div>
                    <div class="form-group">
                        <label for="phone">Phone:</label>
                        <input type="tel" id="phone" required>
                    </div>
                    <div class="form-group">
                        <label for="address">Address:</label>
                        <textarea id="address" required></textarea>
                    </div>
                    <div class="form-group">
                        <label for="city">City:</label>
                        <input type="text" id="city" required>
                    </div>
                    <div class="form-group">
                        <label for="zipcode">Zip Code:</label>
                        <input type="text" id="zipcode" required>
                    </div>
                    <button type="submit" class="btn btn-primary">Proceed to Payment</button>
                </form>
            </div>
        </div>
    </div>

    <!-- Payment Page -->
    <div id="paymentPage" class="page">
        <div class="container">
            <header>
                <h1>Payment</h1>
            </header>
            <div class="payment-container">
                <h2>Select Payment Method</h2>
                <div class="payment-options">
                    <div class="payment-method" onclick="selectPayment('upi')">
                        <h3>💳 UPI</h3>
                        <p>Google Pay / Phone Pay</p>
                    </div>
                    <div class="payment-method" onclick="selectPayment('card')">
                        <h3>💰 Debit/Credit Card</h3>
                        <p>Visa / Mastercard</p>
                    </div>
                </div>
                
                <div id="upiForm" class="payment-form" style="display:none;">
                    <h3>UPI Payment</h3>
                    <p>Scan the QR code or enter your UPI ID</p>
                    <input type="text" placeholder="Enter UPI ID (e.g., name@upi)" id="upiId">
                    <button class="btn btn-primary" onclick="processPayment('upi')">Pay with UPI</button>
                </div>

                <div id="cardForm" class="payment-form" style="display:none;">
                    <h3>Card Payment</h3>
                    <div class="form-group">
                        <label for="cardNumber">Card Number:</label>
                        <input type="text" id="cardNumber" placeholder="1234 5678 9012 3456" maxlength="19">
                    </div>
                    <div class="form-group">
                        <label for="expiryDate">Expiry Date:</label>
                        <input type="text" id="expiryDate" placeholder="MM/YY" maxlength="5">
                    </div>
                    <div class="form-group">
                        <label for="cvv">CVV:</label>
                        <input type="text" id="cvv" placeholder="123" maxlength="3">
                    </div>
                    <button class="btn btn-primary" onclick="processPayment('card')">Pay with Card</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Return Date Page -->
    <div id="returnPage" class="page">
        <div class="container">
            <header>
                <button class="btn btn-secondary" onclick="showPage('genrePage')">← Back</button>
                <h1>My Books - Return Schedule</h1>
            </header>
            <nav class="navbar">
                <a href="#" onclick="showPage('cartPage')">🛒 Cart</a>
                <a href="#" onclick="showPage('contactPage')">📞 Contact Us</a>
            </nav>
            <div class="books-list" id="returnBooksList">
                <!-- Books to return will be listed here -->
            </div>
        </div>
    </div>

    <!-- Return Date Extension Page -->
    <div id="extensionPage" class="page">
        <div class="container">
            <header>
                <button class="btn btn-secondary" onclick="showPage('returnPage')">← Back</button>
                <h1>Request Return Date Extension</h1>
            </header>
            <div class="extension-form">
                <div class="book-info" id="extensionBookInfo"></div>
                <form onsubmit="handleExtension(event)">
                    <div class="form-group">
                        <label for="extendDays">Extend by (days):</label>
                        <input type="number" id="extendDays" min="1" max="30" value="7" required>
                    </div>
                    <div class="form-group">
                        <label for="reason">Reason (optional):</label>
                        <textarea id="reason" placeholder="Why do you need an extension?"></textarea>
                    </div>
                    <div class="cost-info">
                        <p>Extension Cost: <strong>₹<span id="extensionCost">50</span></strong></p>
                        <small>Fine per day: ₹10</small>
                    </div>
                    <button type="submit" class="btn btn-primary">Proceed to Payment</button>
                </form>
            </div>
        </div>
    </div>

    <!-- Cart Page -->
    <div id="cartPage" class="page">
        <div class="container">
            <header>
                <button class="btn btn-secondary" onclick="showPage('genrePage')">← Back</button>
                <h1>Shopping Cart</h1>
            </header>
            <nav class="navbar">
                <a href="#" onclick="showPage('returnPage')">📖 My Books</a>
                <a href="#" onclick="showPage('contactPage')">📞 Contact Us</a>
            </nav>
            <div class="cart-container">
                <div class="cart-items" id="cartItems">
                    <!-- Cart items will be listed here -->
                </div>
                <div class="cart-summary">
                    <h3>Summary</h3>
                    <p>Total Items: <strong id="cartTotal">0</strong></p>
                    <button class="btn btn-primary" onclick="checkoutCart()">Checkout</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Contact Us Page -->
    <div id="contactPage" class="page">
        <div class="container">
            <header>
                <button class="btn btn-secondary" onclick="showPage('genrePage')">← Back</button>
                <h1>Contact Us</h1>
            </header>
            <nav class="navbar">
                <a href="#" onclick="showPage('cartPage')">🛒 Cart</a>
                <a href="#" onclick="showPage('returnPage')">📖 My Books</a>
            </nav>
            <div class="contact-container">
                <div class="contact-info">
                    <div class="contact-card">
                        <h3>📧 Email</h3>
                        <p>support@library.com</p>
                        <p>info@library.com</p>
                    </div>
                    <div class="contact-card">
                        <h3>📞 Phone</h3>
                        <p>+91 1234-567-8900</p>
                        <p>+91 9876-543-2100</p>
                    </div>
                    <div class="contact-card">
                        <h3>📍 Address</h3>
                        <p>123 Library Street</p>
                        <p>New Delhi, India 110001</p>
                    </div>
                    <div class="contact-card">
                        <h3>🕐 Working Hours</h3>
                        <p>Mon-Fri: 9:00 AM - 6:00 PM</p>
                        <p>Sat-Sun: 10:00 AM - 4:00 PM</p>
                    </div>
                </div>
                <div class="contact-form">
                    <h3>Send us a Message</h3>
                    <form onsubmit="handleContactForm(event)">
                        <div class="form-group">
                            <label for="contactName">Name:</label>
                            <input type="text" id="contactName" required>
                        </div>
                        <div class="form-group">
                            <label for="contactEmail">Email:</label>
                            <input type="email" id="contactEmail" required>
                        </div>
                        <div class="form-group">
                            <label for="subject">Subject:</label>
                            <input type="text" id="subject" required>
                        </div>
                        <div class="form-group">
                            <label for="message">Message:</label>
                            <textarea id="message" required></textarea>
                        </div>
                        <button type="submit" class="btn btn-primary">Send Message</button>
                    </form>
                </div>
            </div>
        </div>
    </div>

    <!-- Exit Confirmation Modal -->
    <div id="exitModal" class="modal" style="display:none;">
        <div class="modal-content">
            <h2>Exit Library Management System?</h2>
            <p>Are you sure you want to exit?</p>
            <div class="modal-buttons">
                <button class="btn btn-primary" onclick="confirmExit()">Yes, Exit</button>
                <button class="btn btn-secondary" onclick="closeExitModal()">No, Stay</button>
            </div>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>


// Sample Books Data
const booksDatabase = {
    Fiction: [
        { id: 1, title: 'The Great Gatsby', author: 'F. Scott Fitzgerald', returnDays: 14 },
        { id: 2, title: 'To Kill a Mockingbird', author: 'Harper Lee', returnDays: 14 },
        { id: 3, title: '1984', author: 'George Orwell', returnDays: 14 },
        { id: 4, title: 'Pride and Prejudice', author: 'Jane Austen', returnDays: 14 },
        { id: 5, title: 'The Catcher in the Rye', author: 'J.D. Salinger', returnDays: 14 }
    ],
    Science: [
        { id: 6, title: 'A Brief History of Time', author: 'Stephen Hawking', returnDays: 21 },
        { id: 7, title: 'The Selfish Gene', author: 'Richard Dawkins', returnDays: 21 },
        { id: 8, title: 'Cosmos', author: 'Carl Sagan', returnDays: 21 },
        { id: 9, title: 'The Structure of Scientific Revolutions', author: 'Thomas Kuhn', returnDays: 21 },
        { id: 10, title: 'Sapiens', author: 'Yuval Noah Harari', returnDays: 21 }
    ],
    History: [
        { id: 11, title: 'The History of Ancient Rome', author: 'Michael Grant', returnDays: 21 },
        { id: 12, title: 'A History of England', author: 'John Richard Green', returnDays: 21 },
        { id: 13, title: 'The Origins of Modern Science', author: 'Herbert Butterfield', returnDays: 21 },
        { id: 14, title: 'The Cold War', author: 'John Lewis Gaddis', returnDays: 21 },
        { id: 15, title: 'World War II', author: 'Antony Beevor', returnDays: 21 }
    ],
    Biography: [
        { id: 16, title: 'Steve Jobs', author: 'Walter Isaacson', returnDays: 14 },
        { id: 17, title: 'Elon Musk', author: 'Ashlee Vance', returnDays: 14 },
        { id: 18, title: 'The Autobiography of Malcolm X', author: 'Malcolm X', returnDays: 14 },
        { id: 19, title: 'Leonardo da Vinci', author: 'Walter Isaacson', returnDays: 14 },
        { id: 20, title: 'Benjamin Franklin', author: 'Walter Isaacson', returnDays: 14 }
    ],
    Technology: [
        { id: 21, title: 'The Code Breaker', author: 'Walter Isaacson', returnDays: 21 },
        { id: 22, title: 'Clean Code', author: 'Robert C. Martin', returnDays: 21 },
        { id: 23, title: 'The Pragmatic Programmer', author: 'David Thomas', returnDays: 21 },
        { id: 24, title: 'Design Patterns', author: 'Gang of Four', returnDays: 21 },
        { id: 25, title: 'Introduction to Algorithms', author: 'CLRS', returnDays: 21 }
    ],
    'Self-Help': [
        { id: 26, title: 'Atomic Habits', author: 'James Clear', returnDays: 14 },
        { id: 27, title: 'Think and Grow Rich', author: 'Napoleon Hill', returnDays: 14 },
        { id: 28, title: 'The 7 Habits of Highly Effective People', author: 'Stephen Covey', returnDays: 14 },
        { id: 29, title: 'How to Win Friends and Influence People', author: 'Dale Carnegie', returnDays: 14 },
        { id: 30, title: 'The Power of Now', author: 'Eckhart Tolle', returnDays: 14 }
    ]
};

// Global State
let currentUser = null;
let cart = [];
let borrowedBooks = [];
let currentGenre = null;
let currentBook = null;

// Initialize
document.addEventListener('DOMContentLoaded', function() {
    loadBorrowedBooks();
});

// Page Navigation
function showPage(pageId) {
    document.querySelectorAll('.page').forEach(page => {
        page.classList.remove('active');
    });
    document.getElementById(pageId).classList.add('active');
    
    if (pageId === 'booksPage' && currentGenre) {
        loadBooks(currentGenre);
    }
    if (pageId === 'returnPage') {
        displayReturnBooks();
    }
    if (pageId === 'cartPage') {
        displayCart();
    }
}

// Login Functionality
function handleLogin(event) {
    event.preventDefault();
    const identifier = document.getElementById('identifier').value;
    const password = document.getElementById('password').value;
    
    if (identifier && password) {
        currentUser = {
            name: identifier.split('@')[0] || identifier,
            identifier: identifier,
            loginTime: new Date()
        };
        
        document.getElementById('userName').textContent = currentUser.name;
        document.getElementById('userName2').textContent = currentUser.name;
        
        showPage('genrePage');
        document.getElementById('loginForm').reset();
    } else {
        alert('Please enter all fields');
    }
}

function logout() {
    if (confirm('Are you sure you want to logout?')) {
        currentUser = null;
        cart = [];
        showPage('loginPage');
        document.getElementById('loginForm').reset();
    }
}

// Genre Selection
function selectGenre(genre) {
    currentGenre = genre;
    document.getElementById('genreTitle').textContent = `Books - ${genre}`;
    showPage('booksPage');
}

// Load Books
function loadBooks(genre) {
    const books = booksDatabase[genre] || [];
    const booksGrid = document.getElementById('booksGrid');
    booksGrid.innerHTML = '';
    
    books.forEach(book => {
        const bookCard = document.createElement('div');
        bookCard.className = 'book-card';
        bookCard.innerHTML = `
            <div class="book-cover">📚</div>
            <div class="book-info">
                <h3>${book.title}</h3>
                <p>by ${book.author}</p>
                <p>Return: ${book.returnDays} days</p>
                <div class="book-buttons">
                    <button class="btn btn-primary" onclick="orderBook(${book.id}, '${book.title}', '${book.author}')">Order</button>
                    <button class="btn btn-secondary" onclick="addToCart(${book.id}, '${book.title}', '${book.author}')">Add to Cart</button>
                </div>
            </div>
        `;
        booksGrid.appendChild(bookCard);
    });
}

// Add to Cart
function addToCart(bookId, title, author) {
    const existingItem = cart.find(item => item.id === bookId);
    
    if (existingItem) {
        existingItem.quantity += 1;
    } else {
        cart.push({ id: bookId, title, author, quantity: 1 });
    }
    
    alert(`"${title}" added to cart!`);
}

// Display Cart
function displayCart() {
    const cartItems = document.getElementById('cartItems');
    const cartTotal = document.getElementById('cartTotal');
    
    if (cart.length === 0) {
        cartItems.innerHTML = `
            <div class="empty-state">
                <h3>Your cart is empty</h3>
                <p>Start adding books to your cart!</p>
            </div>
        `;
        cartTotal.textContent = '0';
        return;
    }
    
    cartItems.innerHTML = '';
    let totalItems = 0;
    
    cart.forEach((item, index) => {
        totalItems += item.quantity;
        const cartItem = document.createElement('div');
        cartItem.className = 'cart-item';
        cartItem.innerHTML = `
            <div class="cart-item-info">
                <h4>${item.title}</h4>
                <p>by ${item.author}</p>
                <p>Quantity: ${item.quantity}</p>
            </div>
            <div class="cart-item-actions">
                <button class="btn btn-secondary" onclick="removeFromCart(${index})">Remove</button>
            </div>
        `;
        cartItems.appendChild(cartItem);
    });
    
    cartTotal.textContent = totalItems;
}

// Remove from Cart
function removeFromCart(index) {
    cart.splice(index, 1);
    displayCart();
}

// Checkout
function checkoutCart() {
    if (cart.length === 0) {
        alert('Your cart is empty!');
        return;
    }
    
    currentBook = cart[0];
    const bookDetails = document.getElementById('bookDetails');
    bookDetails.innerHTML = `
        <h3>${currentBook.title}</h3>
        <p>Author: ${currentBook.author}</p>
        <p>Quantity: ${currentBook.quantity}</p>
    `;
    
    showPage('orderPage');
}

// Order Book
function orderBook(bookId, title, author) {
    currentBook = { id: bookId, title, author, quantity: 1 };
    const bookDetails = document.getElementById('bookDetails');
    bookDetails.innerHTML = `
        <h3>${title}</h3>
        <p>Author: ${author}</p>
    `;
    
    showPage('orderPage');
}

// Handle Order Submission
function handleOrder(event) {
    event.preventDefault();
    
    const orderData = {
        book: currentBook.title,
        fullName: document.getElementById('fullName').value,
        email: document.getElementById('email').value,
        phone: document.getElementById('phone').value,
        address: document.getElementById('address').value,
        city: document.getElementById('city').value,
        zipcode: document.getElementById('zipcode').value
    };
    
    console.log('Order Details:', orderData);
    showPage('paymentPage');
}

// Payment Methods
function selectPayment(method) {
    document.getElementById('upiForm').style.display = 'none';
    document.getElementById('cardForm').style.display = 'none';
    
    if (method === 'upi') {
        document.getElementById('upiForm').style.display = 'block';
    } else if (method === 'card') {
        document.getElementById('cardForm').style.display = 'block';
    }
}

// Process Payment
function processPayment(method) {
    let paymentInfo = {};
    
    if (method === 'upi') {
        paymentInfo.upiId = document.getElementById('upiId').value;
        if (!paymentInfo.upiId) {
            alert('Please enter UPI ID');
            return;
        }
    } else if (method === 'card') {
        paymentInfo.cardNumber = document.getElementById('cardNumber').value;
        paymentInfo.expiryDate = document.getElementById('expiryDate').value;
        paymentInfo.cvv = document.getElementById('cvv').value;
        
        if (!paymentInfo.cardNumber || !paymentInfo.expiryDate || !paymentInfo.cvv) {
            alert('Please enter all card details');
            return;
        }
    }
    
    // Simulate payment processing
    alert('Processing payment...');
    
    // Add book to borrowed books
    const returnDate = new Date();
    const borrowedBook = {
        id: currentBook.id,
        title: currentBook.title,
        author: currentBook.author,
        borrowDate: new Date(),
        returnDate: new Date(returnDate.setDate(returnDate.getDate() + (booksDatabase[currentGenre].find(b => b.id === currentBook.id)?.returnDays || 14))),
        extended: false,
        extensionRequested: false
    };
    
    borrowedBooks.push(borrowedBook);
    saveBorrowedBooks();
    
    // Generate invoice
    generateInvoice(paymentInfo);
    
    // Clear cart
    cart = [];
    
    alert('Payment successful! Invoice sent to your email.');
    showPage('genrePage');
}

// Generate Invoice
function generateInvoice(paymentInfo) {
    const invoice = {
        id: 'INV-' + Date.now(),
        date: new Date().toLocaleDateString(),
        book: currentBook.title,
        paymentMethod: paymentInfo.upiId ? 'UPI' : 'Card',
        amount: 0,
        status: 'Paid'
    };
    
    console.log('Invoice:', invoice);
    // In a real application, this would be sent to the user's email
    localStorage.setItem('lastInvoice', JSON.stringify(invoice));
}

// Return Date Page
function displayReturnBooks() {
    const returnBooksList = document.getElementById('returnBooksList');
    
    if (borrowedBooks.length === 0) {
        returnBooksList.innerHTML = `
            <div class="empty-state">
                <h3>No borrowed books</h3>
                <p>Start borrowing books from our library!</p>
            </div>
        `;
        return;
    }
    
    returnBooksList.innerHTML = '';
    const now = new Date();
    
    borrowedBooks.forEach((book, index) => {
        const daysRemaining = Math.ceil((book.returnDate - now) / (1000 * 60 * 60 * 24));
        let statusClass = 'status-success';
        let statusText = `${daysRemaining} days remaining`;
        
        if (daysRemaining < 0) {
            statusClass = 'status-danger';
            statusText = `Overdue by ${Math.abs(daysRemaining)} days`;
        } else if (daysRemaining <= 3) {
            statusClass = 'status-warning';
            statusText = `${daysRemaining} days remaining`;
        }
        
        const bookItem = document.createElement('div');
        bookItem.className = 'book-item';
        bookItem.innerHTML = `
            <div class="book-item-info">
                <h3>${book.title}</h3>
                <p>by ${book.author}</p>
                <p>Borrowed: ${book.borrowDate.toLocaleDateString()}</p>
                <p>Return by: ${book.returnDate.toLocaleDateString()}</p>
            </div>
            <div class="book-item-actions">
                <div class="return-status ${statusClass}">${statusText}</div>
                <button class="btn btn-primary" onclick="requestExtension(${index})">Request Extension</button>
                <button class="btn btn-success" onclick="returnBook(${index})">Return Book</button>
            </div>
        `;
        returnBooksList.appendChild(bookItem);
    });
}

// Request Extension
function requestExtension(bookIndex) {
    const book = borrowedBooks[bookIndex];
    document.getElementById('extensionBookInfo').innerHTML = `
        <h3>${book.title}</h3>
        <p>by ${book.author}</p>
        <p>Current return date: ${book.returnDate.toLocaleDateString()}</p>
    `;
    
    currentBook = { ...book, index: bookIndex };
    showPage('extensionPage');
}

// Update Extension Cost
document.addEventListener('change', function(e) {
    if (e.target.id === 'extendDays') {
        const days = parseInt(e.target.value) || 0;
        const cost = days * 10; // ₹10 per day
        document.getElementById('extensionCost').textContent = cost;
    }
});

// Handle Extension
function handleExtension(event) {
    event.preventDefault();
    
    const extendDays = parseInt(document.getElementById('extendDays').value);
    const reason = document.getElementById('reason').value;
    const cost = extendDays * 10;
    
    if (confirm(`Extension cost: ₹${cost}. Proceed to payment?`)) {
        // Update borrowed book
        const bookIndex = currentBook.index;
        borrowedBooks[bookIndex].extensionRequested = true;
        
        // Proceed to payment for extension
        showPage('paymentPage');
    }
}

// Return Book
function returnBook(bookIndex) {
    if (confirm('Are you sure you want to return this book?')) {
        borrowedBooks.splice(bookIndex, 1);
        saveBorrowedBooks();
        alert('Book returned successfully!');
        displayReturnBooks();
    }
}

// Contact Form
function handleContactForm(event) {
    event.preventDefault();
    
    const contactData = {
        name: document.getElementById('contactName').value,
        email: document.getElementById('contactEmail').value,
        subject: document.getElementById('subject').value,
        message: document.getElementById('message').value
    };
    
    console.log('Contact Message:', contactData);
    alert('Thank you for contacting us! We will get back to you soon.');
    document.getElementById('contactForm').reset();
}

// Exit Functionality
function showExitModal() {
    document.getElementById('exitModal').style.display = 'flex';
}

function closeExitModal() {
    document.getElementById('exitModal').style.display = 'none';
}

function confirmExit() {
    alert('Thank you for using Library Management System!');
    currentUser = null;
    showPage('loginPage');
    closeExitModal();
}

// Local Storage Management
function saveBorrowedBooks() {
    localStorage.setItem('borrowedBooks', JSON.stringify(borrowedBooks));
}

function loadBorrowedBooks() {
    const stored = localStorage.getItem('borrowedBooks');
    if (stored) {
        const parsed = JSON.parse(stored);
        borrowedBooks = parsed.map(book => ({
            ...book,
            borrowDate: new Date(book.borrowDate),
            returnDate: new Date(book.returnDate)
        }));
    }
}

// Signup Functionality
function showSignup(event) {
    event.preventDefault();
    alert('Signup feature coming soon!');
}


* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

:root {
    --primary-color: #2c3e50;
    --secondary-color: #3498db;
    --success-color: #27ae60;
    --danger-color: #e74c3c;
    --warning-color: #f39c12;
    --light-bg: #ecf0f1;
    --text-color: #2c3e50;
    --border-radius: 8px;
    --transition: all 0.3s ease;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: var(--light-bg);
    color: var(--text-color);
    line-height: 1.6;
}

/* Page Styling */
.page {
    display: none;
    min-height: 100vh;
}

.page.active {
    display: block;
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
}

/* Header */
header {
    background-color: var(--primary-color);
    color: white;
    padding: 20px;
    margin-bottom: 20px;
    border-radius: var(--border-radius);
    display: flex;
    justify-content: space-between;
    align-items: center;
}

header h1 {
    font-size: 28px;
}

.user-menu {
    display: flex;
    align-items: center;
    gap: 15px;
}

/* Navigation Bar */
.navbar {
    background-color: white;
    padding: 15px;
    margin-bottom: 20px;
    border-radius: var(--border-radius);
    display: flex;
    gap: 20px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.navbar a {
    text-decoration: none;
    color: var(--secondary-color);
    font-weight: 600;
    transition: var(--transition);
    font-size: 16px;
}

.navbar a:hover {
    color: var(--primary-color);
    text-decoration: underline;
}

/* Buttons */
.btn {
    padding: 10px 20px;
    border: none;
    border-radius: var(--border-radius);
    cursor: pointer;
    font-size: 16px;
    transition: var(--transition);
    font-weight: 600;
}

.btn-primary {
    background-color: var(--secondary-color);
    color: white;
}

.btn-primary:hover {
    background-color: #2980b9;
}

.btn-secondary {
    background-color: #95a5a6;
    color: white;
}

.btn-secondary:hover {
    background-color: #7f8c8d;
}

.btn-success {
    background-color: var(--success-color);
    color: white;
}

.btn-danger {
    background-color: var(--danger-color);
    color: white;
}

/* Login Page */
.login-container {
    max-width: 400px;
    margin: 100px auto;
    background: white;
    padding: 40px;
    border-radius: var(--border-radius);
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
}

.login-container h1 {
    text-align: center;
    margin-bottom: 30px;
    color: var(--primary-color);
}

.form-group {
    margin-bottom: 20px;
}

.form-group label {
    display: block;
    margin-bottom: 8px;
    font-weight: 600;
    color: var(--primary-color);
}

.form-group input,
.form-group textarea,
.form-group select {
    width: 100%;
    padding: 12px;
    border: 1px solid #bdc3c7;
    border-radius: var(--border-radius);
    font-size: 14px;
    transition: var(--transition);
}

.form-group input:focus,
.form-group textarea:focus,
.form-group select:focus {
    outline: none;
    border-color: var(--secondary-color);
    box-shadow: 0 0 5px rgba(52, 152, 219, 0.3);
}

.signup-link {
    text-align: center;
    margin-top: 15px;
    font-size: 14px;
}

.signup-link a {
    color: var(--secondary-color);
    text-decoration: none;
    font-weight: 600;
}

/* Genre Page */
.genres-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
}

.genre-card {
    background: white;
    padding: 30px;
    border-radius: var(--border-radius);
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    cursor: pointer;
    transition: var(--transition);
    text-align: center;
}

.genre-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 6px 16px rgba(0,0,0,0.15);
    background-color: var(--light-bg);
}

.genre-card h3 {
    color: var(--primary-color);
    margin-bottom: 10px;
    font-size: 20px;
}

.genre-card p {
    color: #7f8c8d;
    font-size: 14px;
}

/* Books Grid */
.books-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 20px;
}

.book-card {
    background: white;
    border-radius: var(--border-radius);
    overflow: hidden;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    transition: var(--transition);
    cursor: pointer;
}

.book-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 6px 16px rgba(0,0,0,0.15);
}

.book-cover {
    width: 100%;
    height: 250px;
    background: linear-gradient(135deg, var(--secondary-color), var(--primary-color));
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-size: 50px;
}

.book-info {
    padding: 15px;
}

.book-info h3 {
    font-size: 16px;
    margin-bottom: 5px;
    color: var(--primary-color);
}

.book-info p {
    font-size: 13px;
    color: #7f8c8d;
    margin-bottom: 10px;
}

.book-buttons {
    display: flex;
    gap: 10px;
}

.book-buttons .btn {
    flex: 1;
    padding: 8px;
    font-size: 13px;
}

/* Order Form */
.order-form {
    background: white;
    padding: 30px;
    border-radius: var(--border-radius);
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.book-details {
    background: var(--light-bg);
    padding: 20px;
    border-radius: var(--border-radius);
    margin-bottom: 30px;
}

.book-details h3 {
    color: var(--primary-color);
    margin-bottom: 10px;
}

.book-details p {
    margin: 5px 0;
}

/* Payment Page */
.payment-container {
    background: white;
    padding: 40px;
    border-radius: var(--border-radius);
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    max-width: 600px;
    margin: 40px auto;
}

.payment-container h2 {
    text-align: center;
    margin-bottom: 30px;
    color: var(--primary-color);
}

.payment-options {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
    margin-bottom: 30px;
}

.payment-method {
    background: var(--light-bg);
    padding: 20px;
    border-radius: var(--border-radius);
    text-align: center;
    cursor: pointer;
    transition: var(--transition);
    border: 2px solid transparent;
}

.payment-method:hover {
    border-color: var(--secondary-color);
    background: white;
}

.payment-method h3 {
    color: var(--primary-color);
    margin-bottom: 10px;
}

.payment-method p {
    font-size: 13px;
    color: #7f8c8d;
}

.payment-form {
    background: var(--light-bg);
    padding: 20px;
    border-radius: var(--border-radius);
    margin-top: 20px;
}

.payment-form h3 {
    color: var(--primary-color);
    margin-bottom: 15px;
}

.payment-form p {
    margin-bottom: 15px;
    color: #7f8c8d;
}

/* Return Page */
.books-list {
    display: grid;
    gap: 20px;
}

.book-item {
    background: white;
    padding: 20px;
    border-radius: var(--border-radius);
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.book-item-info h3 {
    color: var(--primary-color);
    margin-bottom: 5px;
}

.book-item-info p {
    font-size: 14px;
    color: #7f8c8d;
    margin: 5px 0;
}

.return-status {
    padding: 8px 15px;
    border-radius: var(--border-radius);
    font-size: 13px;
    font-weight: 600;
}

.status-warning {
    background: #fff3cd;
    color: #856404;
}

.status-danger {
    background: #f8d7da;
    color: #721c24;
}

.status-success {
    background: #d4edda;
    color: #155724;
}

/* Extension Form */
.extension-form {
    background: white;
    padding: 30px;
    border-radius: var(--border-radius);
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    max-width: 500px;
    margin: 40px auto;
}

.cost-info {
    background: var(--light-bg);
    padding: 15px;
    border-radius: var(--border-radius);
    margin-top: 20px;
    text-align: center;
}

.cost-info p {
    font-size: 16px;
    margin-bottom: 5px;
}

.cost-info strong {
    color: var(--success-color);
    font-size: 20px;
}

.cost-info small {
    color: #7f8c8d;
}

/* Cart Page */
.cart-container {
    display: grid;
    grid-template-columns: 1fr 300px;
    gap: 20px;
}

.cart-items {
    background: white;
    padding: 20px;
    border-radius: var(--border-radius);
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.cart-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px;
    border-bottom: 1px solid var(--light-bg);
}

.cart-item:last-child {
    border-bottom: none;
}

.cart-item-info h4 {
    color: var(--primary-color);
    margin-bottom: 5px;
}

.cart-item-info p {
    font-size: 13px;
    color: #7f8c8d;
}

.cart-item-actions {
    display: flex;
    gap: 10px;
}

.cart-summary {
    background: white;
    padding: 20px;
    border-radius: var(--border-radius);
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    height: fit-content;
}

.cart-summary h3 {
    color: var(--primary-color);
    margin-bottom: 15px;
    font-size: 18px;
}

.cart-summary p {
    margin-bottom: 15px;
    font-size: 14px;
}

.cart-summary strong {
    color: var(--secondary-color);
    font-size: 16px;
}

.empty-state {
    text-align: center;
    padding: 40px;
    color: #7f8c8d;
}

.empty-state h3 {
    color: var(--primary-color);
    margin-bottom: 10px;
}

/* Contact Page */
.contact-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 30px;
}

.contact-info {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
}

.contact-card {
    background: white;
    padding: 20px;
    border-radius: var(--border-radius);
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.contact-card h3 {
    color: var(--primary-color);
    margin-bottom: 15px;
    font-size: 16px;
}

.contact-card p {
    margin: 8px 0;
    font-size: 14px;
    color: #7f8c8d;
}

.contact-form {
    background: white;
    padding: 20px;
    border-radius: var(--border-radius);
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.contact-form h3 {
    color: var(--primary-color);
    margin-bottom: 20px;
}

/* Modal */
.modal {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0,0,0,0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
}

.modal-content {
    background: white;
    padding: 40px;
    border-radius: var(--border-radius);
    max-width: 400px;
    text-align: center;
    box-shadow: 0 4px 16px rgba(0,0,0,0.3);
}

.modal-content h2 {
    color: var(--primary-color);
    margin-bottom: 15px;
}

.modal-content p {
    color: #7f8c8d;
    margin-bottom: 30px;
    font-size: 14px;
}

.modal-buttons {
    display: flex;
    gap: 15px;
    justify-content: center;
}

.modal-buttons .btn {
    flex: 1;
}

/* Responsive Design */
@media (max-width: 768px) {
    .container {
        padding: 15px;
    }

    header {
        flex-direction: column;
        gap: 15px;
        text-align: center;
    }

    header h1 {
        font-size: 22px;
    }

    .navbar {
        flex-direction: column;
        gap: 10px;
    }

    .genres-grid,
    .books-grid {
        grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    }

    .cart-container {
        grid-template-columns: 1fr;
    }

    .contact-container {
        grid-template-columns: 1fr;
    }

    .contact-info {
        grid-template-columns: 1fr;
    }

    .book-item {
        flex-direction: column;
        gap: 15px;
        text-align: center;
    }

    .book-item-actions {
        width: 100%;
        display: flex;
        gap: 10px;
    }

    .book-item-actions .btn {
        flex: 1;
    }
}

/* Success Message */
.success-message {
    background: #d4edda;
    color: #155724;
    padding: 15px;
    border-radius: var(--border-radius);
    margin-bottom: 20px;
    border-left: 4px solid var(--success-color);
}

.error-message {
    background: #f8d7da;
    color: #721c24;
    padding: 15px;
    border-radius: var(--border-radius);
    margin-bottom: 20px;
    border-left: 4px solid var(--danger-color);
}

/* Loading Animation */
.loading {
    display: inline-block;
    width: 20px;
    height: 20px;
    border: 3px solid var(--light-bg);
    border-top: 3px solid var(--secondary-color);
    border-radius: 50%;
    animation: spin 1s linear infinite;
}

@keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}
