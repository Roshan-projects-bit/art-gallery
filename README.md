# ArtVault — Art Gallery System
## Complete PHP + MySQL Web Application

---

## 🚀 SETUP GUIDE

### Step 1 — Requirements
- XAMPP or WAMP (Apache + MySQL + PHP 8.0+)
- PHP Extensions: mysqli, gd, fileinfo

### Step 2 — Install Project
1. Copy the `art-gallery/` folder into your XAMPP/WAMP web root:
   - XAMPP: `C:\xampp\htdocs\art-gallery\`
   - WAMP:  `C:\wamp64\www\art-gallery\`

### Step 3 — Create Database
1. Open phpMyAdmin → http://localhost/phpmyadmin
2. Click **New** → Create database named `art_gallery`
3. Select `art_gallery` → click **Import** tab
4. Choose file: `art-gallery/database.sql` → Click **Go**

### Step 4 — Configure Database
Edit `includes/db.php` if needed:
```php
define('DB_HOST', 'localhost');
define('DB_USER', 'root');   // your MySQL username
define('DB_PASS', '');        // your MySQL password
define('DB_NAME', 'art_gallery');
```

### Step 5 — Uploads Folder Permissions
Ensure the `uploads/` folder is writable (chmod 755 on Linux/Mac).
On Windows with XAMPP this is automatic.

### Step 6 — Launch
Open browser → http://localhost/art-gallery/

---

## 🔑 TEST ACCOUNTS

| Role     | Email                     | Password  |
|----------|---------------------------|-----------|
| Admin    | admin@artgallery.com      | password  |
| Artist   | artist@artgallery.com     | password  |
| Customer | customer@artgallery.com   | password  |

> Use the demo buttons on the login page for quick access.

---

## 📁 PROJECT STRUCTURE

```
art-gallery/
├── index.php              ← Homepage
├── login.php              ← Sign in
├── register.php           ← Register (customer/artist)
├── logout.php             ← Session destroy
├── gallery.php            ← Browse artworks
├── artwork.php            ← Artwork detail + buy
├── artists.php            ← Artists listing
├── artist-profile.php     ← Public artist profile
│
├── admin/
│   ├── index.php          ← Admin dashboard
│   ├── users.php          ← Manage users
│   ├── artworks.php       ← Moderate artworks
│   ├── orders.php         ← All orders
│   ├── categories.php     ← Manage categories
│   ├── withdrawals.php    ← Process withdrawals
│   └── settings.php       ← System settings
│
├── artist/
│   ├── index.php          ← Artist dashboard
│   ├── upload-artwork.php ← Upload new artwork
│   ├── artworks.php       ← Manage artworks
│   ├── edit-artwork.php   ← Edit an artwork
│   ├── orders.php         ← Incoming orders
│   ├── offers.php         ← Customer offers
│   ├── earnings.php       ← Earnings & withdrawal
│   └── profile.php        ← Edit artist profile
│
├── customer/
│   ├── index.php          ← Customer dashboard
│   ├── cart.php           ← Shopping cart
│   ├── checkout.php       ← Checkout & payment
│   ├── orders.php         ← Order history
│   ├── order-detail.php   ← Track single order
│   ├── wishlist.php       ← Saved artworks
│   └── profile.php        ← Edit profile
│
├── includes/
│   ├── db.php             ← Database connection
│   ├── functions.php      ← All helper functions
│   ├── header.php         ← Global HTML header + navbar
│   └── footer.php         ← Global footer + scripts
│
├── api/
│   └── action.php         ← AJAX: like, wishlist, cart
│
├── assets/
│   ├── css/main.css       ← All styles
│   └── js/main.js         ← All JavaScript
│
├── uploads/
│   ├── artworks/          ← Artwork images/videos
│   └── profiles/          ← Profile photos
│
└── database.sql           ← Complete DB schema + seed data
```

---

## ✨ FEATURES IMPLEMENTED

### Artist Panel
- ✅ Registration, login, session management
- ✅ Profile with bio, social links, avatar
- ✅ Upload artworks (image/video, up to 20MB)
- ✅ Edit & delete artworks
- ✅ Category assignment
- ✅ View & manage orders (confirm, ship, deliver, cancel)
- ✅ Accept/reject customer offers
- ✅ Earnings dashboard with Chart.js
- ✅ Withdrawal request system
- ✅ Transaction history

### Customer Panel
- ✅ Registration & login
- ✅ Gallery browsing with search & filters
- ✅ Like artworks (AJAX, no page reload)
- ✅ Wishlist (add/remove)
- ✅ Cart (add/remove/clear)
- ✅ Checkout with simulated payment (eSewa/Khalti/COD)
- ✅ Order tracking with visual progress bar
- ✅ Order detail view
- ✅ Make offers to artists
- ✅ Reviews (1–5 stars) and comments
- ✅ Profile management

### Admin Panel
- ✅ Dashboard with revenue charts
- ✅ User management (approve/block/delete)
- ✅ Artwork moderation (approve/feature/delete)
- ✅ Order overview
- ✅ Withdrawal processing
- ✅ Category management (CRUD)
- ✅ System settings (commission %, site name, payment keys)

---

## 🔐 SECURITY FEATURES
- `password_hash()` / `password_verify()` for all passwords
- Prepared statements (mysqli) throughout — SQL injection safe
- `htmlspecialchars()` on all output — XSS safe
- Role-based access control (`requireRole()`)
- Session-based authentication
- File upload validation (type, size, extension)

---

## 🎨 TECH STACK
- **Backend:** Core PHP 8.0+ (no frameworks)
- **Database:** MySQL via mysqli
- **Frontend:** Bootstrap 5.3, Vanilla JS
- **Charts:** Chart.js 4
- **Fonts:** Cormorant Garamond + DM Sans
- **Icons:** Bootstrap Icons 1.11

---

## ⚙️ CUSTOMIZATION

### Change Commission Rate
Admin Panel → Settings → Commission Percentage

### Add Payment Gateway (Real)
Replace simulated checkout in `customer/checkout.php` with:
- eSewa: https://developer.esewa.com.np
- Khalti: https://docs.khalti.com

### Enable Artist Auto-Approve
Admin → Settings → Auto-Approve Artists → Yes

### Add Sample Artwork Images
Place `.jpg` files in `uploads/artworks/` and update the `artworks`
table with the filenames via phpMyAdmin.

