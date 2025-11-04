#  BookStore - Aplikasi Pemesanan Buku Online

**Nama   :** Wahyu Andika  
**NIM    :** 312410182  
**Kelas  :** TI.24.A2  
**Matkul :** Pemrograman Web 1  
**Dosen Pengampu :** Agung Nugroho, S.Kom., M.Kom


##  Deskripsi Proyek
BookStore adalah aplikasi web pemesanan buku online yang dibangun menggunakan **HTML5, CSS3, dan JavaScript**. Aplikasi ini menampilkan implementasi lengkap front-end development dengan fitur-fitur modern seperti dynamic content loading, form validation, local storage, dan responsive design.

---

##  Struktur Project

```
bookstore-app/
│
├── 📄 index.html              # Halaman Login
├── 📄 dashboard.html          # Dashboard Utama
├── 📄 stok.html               # Katalog & Manajemen Stok Buku
├── 📄 checkout.html           # Form Pemesanan & Checkout
├── 📄 tracking.html           # Tracking Pengiriman
│
├── 📁 css/
│   └── 📄 style.css           # Global Stylesheet
│
├── 📁 js/
│   ├── 📄 script.js           # Utility Functions
│   └── 📄 data.js             # Data Dummy JSON
│
├── 📁 assets/
│   └── 🖼️ logo.png            # Logo Aplikasi
│
└── 📁 img/
    ├── 🖼️ pengantar_komunikasi.jpg
    ├── 🖼️ manajemen_keuangan.jpg
    ├── 🖼️ kepemimpinan.jpg
    ├── 🖼️ mikrobiologi.jpg
    └── 🖼️ paud_perkembangan.jpg
```

---

##  Fitur Utama

### 1.  **Sistem Autentikasi** (`index.html`)
- **Form Validation**: Validasi email dan password real-time
- **Modal System**: Modal untuk lupa password dan registrasi
- **User Experience**: Loading states dan error handling
- **Security**: Client-side authentication dengan data dummy

```javascript
// Contoh implementasi validasi
function validateLogin(email, password) {
    const user = users.find(u => u.email === email && u.password === password);
    return user ? { success: true, user } : { success: false };
}
```

### 2.  **Dashboard Interaktif** (`dashboard.html`)
- **Dynamic Greeting**: Salam berdasarkan waktu (Pagi/Siang/Malam)
- **Statistics Cards**: Overview cepat dengan animasi
- **Activity Timeline**: Riwayat aktivitas terbaru
- **Responsive Grid**: Layout adaptif untuk semua device

### 3.  **Manajemen Katalog Buku** (`stok.html`)
- **CRUD Operations**: Create, Read, Update, Delete buku
- **Search & Filter**: Pencarian real-time dan filter kategori
- **Sorting System**: Urutkan berdasarkan nama, harga, stok
- **Image Handling**: Fallback mechanism untuk cover buku
- **Cart Integration**: Tambah ke keranjang dengan validasi stok

```javascript
// Fungsi pencarian buku
function searchBooks(query) {
    return dataKatalogBuku.filter(book => 
        book.namaBarang.toLowerCase().includes(query) ||
        book.kodeBarang.toLowerCase().includes(query)
    );
}
```

### 4.  **Sistem Pemesanan** (`checkout.html`)
- **Shopping Cart**: Kelola item dengan quantity
- **Form Validation**: Validasi data customer lengkap
- **Order Summary**: Kalkulasi total otomatis
- **Payment Methods**: Multiple payment options
- **Order Processing**: Generate order ID dan tracking number

### 5.  **Tracking Pengiriman** (`tracking.html`)
- **Real-time Tracking**: Lacak status berdasarkan nomor DO
- **Progress Visualization**: Progress bar dengan status
- **Timeline System**: Riwayat perjalanan pengiriman
- **Order History**: Riwayat semua pesanan user

---

### **Architecture Patterns:**

#### 1. **Component-Based Structure**
```html
<!-- Book Card Component -->
<div class="book-card">
    <div class="book-cover">
        <img src="cover.jpg" alt="Book Cover">
    </div>
    <div class="book-info">
        <h5>Book Title</h5>
        <p class="price">Rp 150.000</p>
        <button class="btn-add-cart">Add to Cart</button>
    </div>
</div>
```

#### 2. **Modular JavaScript**
```javascript
// Data Module
const DataManager = {
    getBooks: () => JSON.parse(localStorage.getItem('books')),
    saveBooks: (books) => localStorage.setItem('books', JSON.stringify(books)),
    // ... other methods
};

// Cart Module  
const CartManager = {
    addItem: (book) => { /* implementation */ },
    removeItem: (id) => { /* implementation */ },
    getTotal: () => { /* implementation */ }
};
```

#### 3. **CSS Methodology - BEM**
```css
/* Block Element Modifier */
.book-card { /* block */ }
.book-card__cover { /* element */ }
.book-card--featured { /* modifier */ }
.book-card__button--disabled { /* element with modifier */ }
```

---

##  UI/UX Features

### **Design System:**
- **Color Palette**: 
  - Primary: `#6366f1` 
  - Secondary: `#f59e0b`
  - Accent: `#ec4899`
  - Gradient: `linear-gradient(135deg, #667eea 0%, #764ba2 100%)`

- **Typography**: 
  - Font Family: Poppins, Segoe UI
  - Hierarchy: Clear heading levels
  - Readability: Optimal contrast ratios

### **Interactive Elements:**
- **Hover Effects**: Smooth transitions dan elevation
- **Loading States**: Spinner dan skeleton screens
- **Form Feedback**: Real-time validation messages
- **Micro-interactions**: Button presses dan card animations

### **Accessibility:**
- **Semantic HTML**: Proper heading structure
- **ARIA Labels**: Screen reader support
- **Keyboard Navigation**: Tab-able interfaces
- **Color Contrast**: WCAG compliant

---

## 📱 Responsive Design

### **Breakpoints:**
- **Mobile**: < 768px
- **Tablet**: 768px - 992px  
- **Desktop**: > 992px

### **Mobile-First Approach:**
```css
/* Base styles (mobile) */
.book-card {
    padding: 1rem;
    margin-bottom: 1rem;
}

/* Tablet */
@media (min-width: 768px) {
    .book-card {
        padding: 1.5rem;
    }
}

/* Desktop */
@media (min-width: 992px) {
    .book-card {
        padding: 2rem;
    }
}
```

---

##  Data Management

### **Data Structure:**
```javascript
// User Data
const users = [
    {
        id: 1,
        name: "John Doe",
        email: "john@example.com",
        password: "hashed_password",
        role: "customer"
    }
];

// Book Catalog
const books = [
    {
        id: "B001",
        title: "Book Title",
        author: "Author Name",
        price: 150000,
        stock: 50,
        category: "Fiction",
        cover: "cover.jpg"
    }
];

// Order Data
const orders = [
    {
        orderId: "ORD-001",
        userId: 1,
        items: [{ bookId: "B001", quantity: 2 }],
        total: 300000,
        status: "processing",
        trackingNumber: "TRK-001"
    }
];
```

### **Local Storage Strategy:**
```javascript
const Storage = {
    // Key naming convention
    keys: {
        CART: 'bookstore_cart',
        ORDERS: 'bookstore_orders',
        CATALOG: 'bookstore_catalog',
        USERS: 'bookstore_users'
    },
    
    // Generic methods
    get: (key) => JSON.parse(localStorage.getItem(key)),
    set: (key, value) => localStorage.setItem(key, JSON.stringify(value)),
    remove: (key) => localStorage.removeItem(key),
    clear: () => localStorage.clear()
};
```

---

##  Performance Optimizations

### **1. Code Splitting:**
- Separate HTML files for each page
- Modular JavaScript components
- Lazy loading for images

### **2. DOM Optimization:**
```javascript
// Efficient DOM updates
function updateBookList(books) {
    const container = document.getElementById('book-container');
    const fragment = document.createDocumentFragment();
    
    books.forEach(book => {
        const element = createBookElement(book);
        fragment.appendChild(element);
    });
    
    container.innerHTML = '';
    container.appendChild(fragment);
}
```

### **3. Event Delegation:**
```javascript
// Single event listener for multiple elements
document.getElementById('book-container').addEventListener('click', (e) => {
    if (e.target.classList.contains('add-to-cart')) {
        const bookId = e.target.dataset.bookId;
        addToCart(bookId);
    }
});
```

---

##  Security Features

### **Client-Side Security:**
- Input sanitization
- XSS prevention
- CSRF protection (conceptual)

### **Data Validation:**
```javascript
function validateEmail(email) {
    const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return re.test(email);
}

function validatePrice(price) {
    return !isNaN(price) && price > 0;
}
```

---

##  Testing & Quality Assurance

### **Manual Testing Checklist:**
- [ ] Form validation working
- [ ] Cart functionality
- [ ] Responsive design
- [ ] Cross-browser compatibility
- [ ] Local storage persistence

---

##  Installation & Setup

### **Prerequisites:**
- Web browser modern
- Local server (untuk menghindari CORS issues)

### **Quick Start:**
```bash
# Clone repository
git clone https://github.com/username/bookstore-app.git

# Navigate to project directory
cd bookstore-app

# Serve with local server (Python)
python -m http.server 8000

# Or with Node.js
npx http-server

# Access application
# Open http://localhost:8000 in browser
```

### **Default Login Credentials:**
```javascript
Email: wahyuandika0147@gmail.com
Password: password123
```

---

##  Usage Guide

### **1. Login & Authentication**
- Masuk dengan email dan password
- Gunakan modal untuk lupa password/registrasi

### **2. Browse Catalog** 
- Lihat daftar buku tersedia
- Gunakan search dan filter untuk menemukan buku
- Tambah buku ke keranjang

### **3. Shopping Cart**
- Review item yang dipilih
- Update quantity atau hapus item
- Lanjut ke checkout

### **4. Checkout Process**
- Isi data customer
- Pilih metode pembayaran
- Konfirmasi pesanan

### **5. Order Tracking**
- Gunakan nomor tracking untuk melacak
- Lihat riwayat pesanan
- Pantau status pengiriman

---

##  Future Enhancements

### **Planned Features:**
- [ ] Backend integration dengan REST API
- [ ] Database persistence dengan MySQL/PostgreSQL
- [ ] User authentication dengan JWT
- [ ] Payment gateway integration
- [ ] Admin dashboard
- [ ] Advanced analytics
- [ ] Email notifications
- [ ] Wishlist functionality
- [ ] Book reviews dan ratings

### **Technical Improvements:**
- [ ] PWA (Progressive Web App)
- [ ] Service Workers untuk offline capability
- [ ] WebSocket untuk real-time updates
- [ ] Image optimization dengan WebP
- [ ] Code splitting dengan dynamic imports

---

##  Development Notes

### **Code Standards:**
- ES6+ JavaScript features
- CSS Grid dan Flexbox untuk layout
- Semantic HTML5 elements
- Mobile-first responsive design
- Accessibility best practices

### **File Organization:**
```
src/
├── components/     # Reusable UI components
├── services/       # Data management services  
├── utils/          # Utility functions
├── styles/         # CSS modules
└── assets/         # Static files
```

---

## Login

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/32cd0332-1cb2-477f-97c0-b0188d17e32f" />

## Dashboard

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/32e810d7-e937-4773-90de-43922a56c261" />

## Katalog Buku

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/fdd20c4a-5689-4e94-8b56-a9adbf16efda" />

## Checkout

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/07c5d5bf-24b7-4c62-881d-01ce5fa37ac8" />

## Tracking

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/a1ba5d49-a2ec-4685-af01-7a4d0b30ea99" />

## Logout

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/7d2ff647-349b-468d-b4f2-3ad51f4c33c6" />
