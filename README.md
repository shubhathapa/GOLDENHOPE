# 💎 Golden Hope — Fine Jewelry E-Commerce Store
> Group project · COMP/IT [Course Code] · Team of 4

---

## 👥 Team & Branch Ownership

| Member  | Feature                        | Git Branch            | Files Owned |
|---------|--------------------------------|-----------------------|-------------|
| Senudi  | Navbar & Navigation            | `senudi/navbar`       | `src/components/Navbar.jsx` |
| Jiaxin  | Product Cards & Listing Page   | `jiaxin/product-card` | `src/components/ProductCard.jsx`, `src/pages/ProductsPage.jsx` |
| Shubha  | Product Details Page           | `shubha/product-page` | `src/pages/ProductPage.jsx` |
| May     | Shopping Cart UI & Functionality | `may/cart-ui`       | `src/pages/CartPage.jsx` |

---

## 🗂 Project Structure

```
project/
├── frontend/
│   ├── index.html
│   ├── vite.config.js
│   ├── tailwind.config.js
│   ├── postcss.config.js
│   ├── package.json
│   └── src/
│       ├── main.jsx              ← React entry point
│       ├── App.jsx               ← Router + global cart state
│       ├── index.css             ← Global Tailwind styles
│       ├── components/
│       │   ├── Navbar.jsx        ← [Senudi] sticky nav, search, cart badge
│       │   └── ProductCard.jsx   ← [Jiaxin] reusable product tile
│       ├── pages/
│       │   ├── HomePage.jsx      ← Hero banner + featured products
│       │   ├── ProductsPage.jsx  ← [Jiaxin] full grid with category filters
│       │   ├── ProductPage.jsx   ← [Shubha] single product detail view
│       │   └── CartPage.jsx      ← [May] cart items, qty controls, totals
│       └── services/
│           └── api.js            ← All fetch() calls to backend
│
├── backend/
│   ├── package.json
│   ├── .env.example
│   └── src/
│       ├── server.js             ← Express app + middleware
│       ├── db/
│       │   ├── connection.js     ← MySQL pool connection
│       │   └── schema.sql        ← DB tables + 10 seed products
│       ├── models/
│       │   ├── productModel.js   ← SQL for products table
│       │   └── cartModel.js      ← SQL for cart_items table
│       ├── controllers/
│       │   ├── productController.js
│       │   └── cartController.js
│       └── routes/
│           ├── productRoutes.js
│           └── cartRoutes.js
│
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- **Node.js** v18+
- **MySQL** v8+
- **Git**

---

### 1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/jewelry-store.git
cd jewelry-store
```

---

### 2. Set up the database
```bash
# Log into MySQL
mysql -u root -p

# Run the schema file (creates DB, tables, and inserts 10 products)
mysql -u root -p < backend/src/db/schema.sql
```

---

### 3. Configure the backend

```bash
cd backend

# Copy the example env file
cp .env.example .env

# Edit .env with your MySQL credentials
nano .env   # or open in VS Code
```

Your `.env` should look like:
```
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_actual_password
DB_NAME=jewelry_store
DB_PORT=3306
PORT=5000
```

---

### 4. Start the backend
```bash
cd backend
npm install
npm run dev     # runs with nodemon (auto-restarts on change)
```
Backend will be running at: **http://localhost:5000**

Test it: `http://localhost:5000/products`

---

### 5. Start the frontend
```bash
cd frontend
npm install
npm run dev
```
Frontend will be running at: **http://localhost:5173**

The Vite dev server proxies `/api/*` → `http://localhost:5000`, so no CORS issues in development.

---

## 🌿 Git Workflow — Branching Guide

### Initial setup (one team member does this)
```bash
git init
git add .
git commit -m "chore: initial project scaffold"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/jewelry-store.git
git push -u origin main
```

### Each team member creates their branch
```bash
# Senudi
git checkout -b senudi/navbar
git push -u origin senudi/navbar

# Jiaxin
git checkout -b jiaxin/product-card
git push -u origin jiaxin/product-card

# Shubha
git checkout -b shubha/product-page
git push -u origin shubha/product-page

# May
git checkout -b may/cart-ui
git push -u origin may/cart-ui
```

### Daily workflow
```bash
# Pull latest main before starting work
git checkout main
git pull origin main

# Switch to your branch and rebase
git checkout your-branch-name
git rebase main

# Stage, commit, push your changes
git add src/components/YourFile.jsx
git commit -m "feat(navbar): add mobile hamburger menu"
git push origin your-branch-name
```

### Merging (via Pull Request on GitHub)
1. Push your branch to GitHub
2. Open a Pull Request → `your-branch` into `main`
3. Assign another team member to review
4. Merge after approval ✅

---

## 📡 API Reference

### Products

| Method | Endpoint             | Description              |
|--------|----------------------|--------------------------|
| GET    | `/products`          | Get all products         |
| GET    | `/products?category=Rings` | Filter by category  |
| GET    | `/products/:id`      | Get single product       |

**Example response — GET /products/:id**
```json
{
  "success": true,
  "data": {
    "id": 1,
    "name": "Eternal Rose Gold Ring",
    "price": "299.99",
    "description": "A timeless rose gold band...",
    "image_url": "https://...",
    "category": "Rings",
    "stock": 25
  }
}
```

### Cart

| Method | Endpoint     | Body                              | Description         |
|--------|--------------|-----------------------------------|---------------------|
| GET    | `/cart`      | —                                 | Get full cart       |
| POST   | `/cart`      | `{ product_id, quantity? }`       | Add item to cart    |
| PUT    | `/cart/:id`  | `{ quantity }`                    | Update quantity     |
| DELETE | `/cart/:id`  | —                                 | Remove item         |

---

## 🎨 Tech Stack

| Layer      | Technology                     |
|------------|--------------------------------|
| Frontend   | React 18, Vite, Tailwind CSS   |
| Routing    | React Router v6                |
| Backend    | Node.js, Express.js            |
| Database   | MySQL 8                        |
| ORM/Query  | mysql2 (raw SQL with pools)    |
| Fonts      | Playfair Display, Cormorant Garamond, DM Sans |

---

## 🎨 Design System

| Token     | Value                            |
|-----------|----------------------------------|
| Gold 500  | `#d4900f` — primary CTA color    |
| Cream     | `#faf7f2` — page background      |
| Charcoal  | `#1a1a1a` — primary text         |
| Display font | Playfair Display (headings)   |
| Body font | Cormorant Garamond (body text)   |
| Sans font | DM Sans (UI labels, buttons)     |

---

## 🐛 Common Issues

**MySQL connection refused**
→ Make sure MySQL is running: `sudo service mysql start` (Linux) or start via MAMP/WAMP

**Port 5000 already in use**
→ Change `PORT=5001` in your `.env` and update `vite.config.js` proxy target

**CORS errors**
→ Make sure you're running the frontend through Vite (`npm run dev`), not opening `index.html` directly

**Products not loading**
→ Check backend is running at port 5000, and `schema.sql` was executed

---

*Built with 💛 by Senudi, Jiaxin, Shubha & May*
