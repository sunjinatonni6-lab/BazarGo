# BazarGO — E-Commerce Web Application

BazarGO is a multi-page e-commerce web application featuring a customer storefront, shopping cart, customer authentication, order management, and an administrative back-office portal.

---

## Table of Contents
- [Tech Stack](#tech-stack)
- [Key Features](#key-features)
- [Project Structure](#project-structure)
- [Firebase Configuration](#firebase-configuration)
- [Firestore Security Rules](#firestore-security-rules)


---

## Tech Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript (ES Modules)[cite: 2, 8, 10]
- **Icons & UI**: [Font Awesome 6.5.1](https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css)[cite: 2]
- **Backend & Database**: Firebase Authentication, Cloud Firestore[cite: 8, 10]
- **Hosting**: Vercel

---

## Key Features

### Customer Storefront
- **Product Catalog & Search**: Browse featured products, view product ratings, review counts, and descriptions, and filter products using live search[cite: 6].
- **Interactive Details Modal**: View enlarged product photos, product categories, stock status, and rate products interactively with a 5-star rating system[cite: 6].
- **Shopping Cart**: Real-time quantity controls (`+`, `-`, manual entry), subtotal calculations, and item removal[cite: 3]. Supports guest local storage and Firebase-synced carts[cite: 9].
- **Authentication & Checkout Protection**:
  - Guests can freely browse and add items to the cart[cite: 6].
  - Customers must sign in or register before checking out[cite: 3, 4].
  - Redirects guest users to sign-in with redirect preservation back to checkout[cite: 3, 7].
- **Atomic Order Submission**: Orders decrement product stock in Cloud Firestore via atomic transactions, preventing overselling[cite: 4].
- **Customer Dashboard & Profile**: Update delivery addresses, full names, and phone numbers, and view order history[cite: 2].

### Admin Panel (`/admin`)
- **Protected Admin Routing**: Admin route guard checking `role == 'admin'`[cite: 8].
- **Product Inventory**: Add, edit, and delete products with image URLs, categories, prices, ratings, and stock quantities[cite: 11].
- **Stock Management**: Track available stock quantities, automatically display "Out of Stock" badges, and disable checkout for depleted products[cite: 6, 11].
- **Promotional Hero Banner**: Customise marketing tags, titles, subtitles, and promo images directly from the admin panel[cite: 6, 11].

---

## Project Structure

```text
BazarGO/
├── index.html                  # Storefront home page with catalog & hero banner[cite: 6]
├── cart.html                   # Customer shopping cart page[cite: 3]
├── checkout.html               # Shipping, delivery, and order placement page[cite: 4]
├── login.html                  # Customer and admin sign-in page[cite: 7]
├── register.html               # Customer registration page[cite: 7]
├── account.html                # User profile and delivery address management[cite: 2]
├── my-orders.html              # Customer order history and status tracking
├── firestore.rules             # Cloud Firestore security rules
├── vercel.json                 # Vercel deployment routing configuration
│
├── admin/
│   ├── dashboard.html          # Operational metrics and dashboard
│   ├── products.html           # Product catalog and stock management[cite: 11]
│   ├── orders.html             # Order fulfillment management
│   └── banner.html             # Hero banner management
│
└── assets/
    ├── css/
    │   ├── style.css           # Storefront stylesheet[cite: 2]
    │   └── admin.css           # Admin dashboard stylesheet[cite: 11]
    ├── js/
    │   ├── firebase-config.js  # Firebase SDK initialization
    │   ├── auth.js             # Authentication helpers and route guards[cite: 8]
    │   └── cart.js             # Cart management and badge updates[cite: 9]
    └── images/                 # Static fallback images and assets
