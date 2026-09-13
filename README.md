# 📦 Inventory Management System

A Django-based web application for managing products, stock, purchases, and sales through a simple inventory dashboard.

## 🚀 Overview

The **Inventory Management System** is a web application built with **Python and Django**. It helps track products and inventory movement in one place.

The application maintains stock quantities as purchases and sales are recorded, calculates transaction totals, and highlights products whose stock is at or below their configured minimum level.

## ✨ Features

- 📊 **Dashboard** with total products, stock value, low-stock products, recent sales, and recent purchases
- 📦 **Product management** — create, view, and edit products
- 📈 **Stock tracking** — monitor the current quantity for each product
- 🛒 **Purchase management** — record purchases and automatically increase stock
- 💰 **Sales management** — record sales and automatically decrease stock
- ⚠️ **Low-stock monitoring** using each product's minimum stock level
- 🔐 **Django Admin** for managing application data
- 🗃️ **SQLite database** for local development

## 🛠️ Technology Stack

- **Python**
- **Django 5.1.6**
- **SQLite**
- **Django Templates / HTML / CSS**
- **Git & GitHub**

## 📁 Project Structure

```text
Inventory-Management-System/
│
├── inventory/
│   ├── migrations/
│   ├── templates/
│   │   └── inventory/
│   │       ├── base.html
│   │       ├── dashboard.html
│   │       ├── product_detail.html
│   │       ├── product_form.html
│   │       ├── product_list.html
│   │       ├── purchase_form.html
│   │       └── sale_form.html
│   ├── admin.py
│   ├── apps.py
│   ├── forms.py
│   ├── models.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
│
├── inventory_system/
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── db.sqlite3
└── manage.py
```

## 🔄 Application Flow

```text
Dashboard
   │
   ├── Products
   │     ├── Product List
   │     ├── Create Product
   │     ├── Product Details
   │     └── Edit Product
   │
   ├── Purchases
   │     └── Record Purchase → Stock Increases
   │
   └── Sales
         └── Record Sale → Stock Decreases
```

## 🧩 Core Models

### Product

Stores product information such as:

- Name
- Description
- Price
- Minimum stock level
- Created timestamp
- Updated timestamp

### Stock

Stores the current quantity associated with a product. Stock is initialized when a product is created and is updated when purchases or sales are recorded.

### Sale

Stores the product, quantity, price per unit, total price, and date of a sale. The total is calculated automatically and the product stock is reduced after a sale.

### Purchase

Stores the product, quantity, price per unit, total price, and date of a purchase. The total is calculated automatically and the product stock is increased after a purchase.

## 🌐 Application URLs

| URL | Purpose |
|---|---|
| `/` | Dashboard |
| `/products/` | Product list |
| `/products/create/` | Create a product |
| `/products/<id>/` | Product details |
| `/products/<id>/edit/` | Edit a product |
| `/sales/create/` | Record a sale |
| `/purchases/create/` | Record a purchase |
| `/admin/` | Django administration |

## ⚙️ Installation & Setup

### 1. Clone the repository

```bash
git clone https://github.com/tejasgithub630/Inventory-Management-System.git
cd Inventory-Management-System
```

### 2. Create a virtual environment

**Windows:**

```bash
python -m venv venv
venv\Scripts\activate
```

**macOS/Linux:**

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Django

The project currently does not include a `requirements.txt`, so install the required framework directly:

```bash
pip install django==5.1.6
```

### 4. Apply database migrations

```bash
python manage.py migrate
```

### 5. Start the development server

```bash
python manage.py runserver
```

### 6. Open the application

Open the following address in your browser:

```text
http://127.0.0.1:8000/
```

## 🔐 Django Admin

Create an admin account with:

```bash
python manage.py createsuperuser
```

Then open:

```text
http://127.0.0.1:8000/admin/
```

## 📊 Inventory Logic

- When a **purchase** is recorded, the purchase quantity is added to the product's stock.
- When a **sale** is recorded, the sale quantity is subtracted from the product's stock.
- The sales form checks whether enough stock is available before allowing the sale.
- A product is considered **low stock** when its current quantity is less than or equal to its minimum stock level.
- Sale and purchase totals are calculated from `quantity × price_per_unit`.

## ⚠️ Development & Security Notes

This repository is configured primarily for local development.

Before deploying publicly, review and secure the Django settings, especially:

- `SECRET_KEY`
- `DEBUG`
- `ALLOWED_HOSTS`
- Database configuration
- Static/media file configuration
- Production security settings

Do not use development settings or expose development secrets in a production deployment.

## 🔮 Future Improvements

Potential improvements for a production-ready version include:

- User authentication and role-based access
- Supplier and customer management
- Product categories
- Search, filtering, and pagination
- Inventory transaction history
- Sales and purchase reports
- CSV/PDF export
- Stronger model-level stock validation and transaction handling
- Automated unit/integration tests
- PostgreSQL support
- Production deployment configuration
- Environment-variable based configuration

## 👨‍💻 Author

**Tejas Reddy**

GitHub: https://github.com/tejasgithub630

## 📄 License

No license is currently specified for this repository.
