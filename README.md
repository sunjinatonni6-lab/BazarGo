# BazarGO — E-Commerce Web Application

BazarGO is a multi-page e-commerce web application featuring a customer storefront, shopping cart, customer authentication, order management, and an administrative back-office portal.

---

## Table of Contents
- [Tech Stack](#tech-stack)
- [Key Features](#key-features)
- [Project Structure](#project-structure)



---

## Tech Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript (ES Modules)
- **Icons & UI**: [Font Awesome 6.5.1](https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css)
- **Backend & Database**: Firebase Authentication, Cloud Firestore
- **Hosting**: Vercel

---

## Key Features

### Customer Storefront
- **Product Catalog & Search**: Browse featured products, view product ratings, review counts, and descriptions, and filter products using live search.
- **Interactive Details Modal**: View enlarged product photos, product categories, stock status, and rate products interactively with a 5-star rating system.
- **Shopping Cart**: Real-time quantity controls (`+`, `-`, manual entry), subtotal calculations, and item removal[cite: 3]. Supports guest local storage and Firebase-synced carts.
- **Authentication & Checkout Protection**:
  - Guests can freely browse and add items to the cart.
  - Customers must sign in or register before checking out.
  - Redirects guest users to sign-in with redirect preservation back to checkout.
- **Atomic Order Submission**: Orders decrement product stock in Cloud Firestore via atomic transactions, preventing overselling.
- **Customer Dashboard & Profile**: Update delivery addresses, full names, and phone numbers, and view order history.

### Admin Panel (`/admin`)
- **Protected Admin Routing**: Admin route guard checking `role == 'admin'`.
- **Product Inventory**: Add, edit, and delete products with image URLs, categories, prices, ratings, and stock quantities.
- **Stock Management**: Track available stock quantities, automatically display "Out of Stock" badges, and disable checkout for depleted products.
- **Promotional Hero Banner**: Customise marketing tags, titles, subtitles, and promo images directly from the admin panel.

---

## Project Structure

```text
BazarGO/
├── index.html                  # Storefront home page with catalog & hero banner 
├── cart.html                   # Customer shopping cart page 
├── checkout.html               # Shipping, delivery, and order placement page 
├── login.html                  # Customer and admin sign-in page 
├── register.html               # Customer registration page 
├── account.html                # User profile and delivery address management 
├── my-orders.html              # Customer order history and status tracking
├── firestore.rules             # Cloud Firestore security rules
├── vercel.json                 # Vercel deployment routing configuration
│
├── admin/
│   ├── dashboard.html          # Operational metrics and dashboard
│   ├── products.html           # Product catalog and stock management 
│   ├── orders.html             # Order fulfillment management
│   └── banner.html             # Hero banner management
│
└── assets/
    ├── css/
    │   ├── style.css           # Storefront stylesheet 
    │   └── admin.css           # Admin dashboard stylesheet 
    ├── js/
    │   ├── firebase-config.js  # Firebase SDK initialization
    │   ├── auth.js             # Authentication helpers and route guards 
    │   └── cart.js             # Cart management and badge updates 
    └── images/                 # Static fallback images and assets
