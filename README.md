# TrustBuyV4 - Django E-Commerce Platform

<div align="center">

![Django](https://img.shields.io/badge/Django-4.1.4-092E20?style=for-the-badge&logo=django&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-4-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-3-003B57?style=for-the-badge&logo=sqlite&logoColor=white)

**A full-featured e-commerce web application built with Django**

[Features](#features) • [Installation](#installation) • [Architecture](#architecture) • [Usage](#usage) • [License](#license)

</div>

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Database Schema](#database-schema)
- [Configuration](#configuration)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## Overview

**TrustBuyV4** is a modern, responsive e-commerce platform built with Django 4.1.4. It provides a complete online shopping experience with user authentication, product catalog management, shopping cart functionality, and PayPal integration for secure payments.

This project demonstrates best practices in Django development, including custom user models, session-based cart management, context processors, and clean separation of concerns across Django apps.

### Key Highlights

- **Custom User Authentication** - Email-based authentication system
- **Session-Based Shopping Cart** - Works for both guests and authenticated users
- **Product Management** - Complete CRUD operations via Django admin
- **Category Filtering** - Browse products by categories
- **PayPal Integration** - Secure payment processing (sandbox ready)
- **Responsive Design** - Mobile-friendly Bootstrap 4 interface
- **Admin Dashboard** - Comprehensive backend management

---

## Features

### User Management
- ✅ Custom user model with email as username
- ✅ User registration with password confirmation
- ✅ Login/logout functionality
- ✅ Login-protected cart operations
- ✅ Admin and staff user roles

### Product Catalog
- ✅ Product listing with images and descriptions
- ✅ Product detail pages with specifications
- ✅ Category-based product organization
- ✅ Stock management and availability tracking
- ✅ Product brand information
- ✅ Dynamic category filtering
- ✅ Product image upload support

### Shopping Cart
- ✅ Session-based cart (works for guest users)
- ✅ Add products to cart
- ✅ Update item quantities
- ✅ Remove items from cart
- ✅ Automatic subtotal calculation
- ✅ Real-time cart counter in navigation
- ✅ Tax calculation (2% flat rate)
- ✅ Grand total computation

### Checkout & Payment
- ✅ Order review page
- ✅ PayPal integration (sandbox environment)
- ✅ Cart summary on checkout
- ✅ Secure payment processing

### UI/UX
- ✅ Responsive Bootstrap 4 design
- ✅ Dynamic category dropdown menu
- ✅ Shopping cart badge counter
- ✅ Product search bar interface
- ✅ Guest user welcome message
- ✅ Clean and modern interface
- ✅ Font Awesome icons

---

## Tech Stack

### Backend
- **Django 4.1.4** - High-level Python web framework
- **Python 3.9+** - Programming language
- **SQLite3** - Database (development)
- **Pillow** - Python Imaging Library for image processing

### Frontend
- **Bootstrap 4** - Responsive CSS framework
- **jQuery 2.0.0** - JavaScript library
- **Font Awesome 5** - Icon library
- **HTML5/CSS3** - Markup and styling

### Payment Integration
- **PayPal SDK** - Payment processing

### Development Tools
- **Django Sessions** - Session management
- **Django Admin** - Backend administration
- **Django ORM** - Database abstraction

---

## Architecture

TrustBuyV4 follows Django's MVT (Model-View-Template) architecture pattern with a modular app structure:

```
┌─────────────────────────────────────────────────────┐
│                    TrustBuyV4                       │
│              (Main Project Configuration)            │
└─────────────────────────────────────────────────────┘
                          │
          ┌───────────────┼───────────────┐
          │               │               │
    ┌─────▼─────┐   ┌────▼────┐   ┌─────▼─────┐
    │ Accounts  │   │  Store  │   │    Cart   │
    │  (Auth)   │   │(Products)│   │ (Shopping)│
    └─────┬─────┘   └────┬────┘   └─────┬─────┘
          │               │               │
    ┌─────▼─────┐   ┌────▼────┐         │
    │   Home    │   │Category │         │
    │(Homepage) │   │(Catalog)│         │
    └───────────┘   └─────────┘         │
                                         │
                ┌────────────────────────▼────┐
                │   Session-Based Cart        │
                │   Context Processors        │
                │   Template Inheritance      │
                └─────────────────────────────┘
```

### Django Apps

| App | Purpose | Key Components |
|-----|---------|----------------|
| **Accounts** | User authentication & management | Custom user model, registration, login |
| **home** | Homepage & product details | Landing page, product detail view |
| **category** | Product categorization | Category model, context processor |
| **store** | Product listing & filtering | Product model, store views |
| **cart** | Shopping cart & checkout | Cart model, cart operations, PayPal |
| **TrustBuyV4** | Project configuration | Settings, URLs, WSGI/ASGI |

---

## Installation

### Prerequisites

- Python 3.9 or higher
- pip (Python package manager)
- Virtual environment (recommended)
- Git

### Step-by-Step Setup

1. **Clone the repository**

```bash
git clone https://github.com/Andro0o0o0w-Romany/Django-ecommerce-2.git
cd Django-ecommerce-2
```

2. **Create and activate virtual environment**

```bash
# On Linux/Mac
python3 -m venv venv
source venv/bin/activate

# On Windows
python -m venv venv
venv\Scripts\activate
```

3. **Install dependencies**

```bash
pip install django==4.1.4
pip install Pillow
```

4. **Apply database migrations**

```bash
python manage.py migrate
```

5. **Load sample data (optional)**

```bash
python manage.py loaddata category.json
python manage.py loaddata store.json
python manage.py loaddata Accounts.json
python manage.py loaddata cart.json
```

6. **Create superuser for admin access**

```bash
python manage.py createsuperuser
```

7. **Run the development server**

```bash
python manage.py runserver
```

8. **Access the application**

- Frontend: http://127.0.0.1:8000/
- Admin panel: http://127.0.0.1:8000/admin/

---

## Usage

### For Users

1. **Browse Products**
   - Visit the homepage to see featured products
   - Navigate to "Store" to view all products
   - Use category filters to browse specific product types

2. **Create an Account**
   - Click "Register" in the navigation
   - Fill out the registration form
   - Log in with your credentials

3. **Shop**
   - Click on products to view details
   - Add items to cart (login required)
   - Adjust quantities in cart
   - Proceed to checkout

4. **Checkout**
   - Review your order
   - Complete payment via PayPal (sandbox mode)

### For Administrators

1. **Access Admin Panel**
   - Navigate to `/admin/`
   - Log in with superuser credentials

2. **Manage Products**
   - Add/edit/delete products
   - Upload product images
   - Set stock levels and prices
   - Manage product availability

3. **Manage Categories**
   - Create product categories
   - Organize products by category
   - Upload category images

4. **Manage Users**
   - View registered users
   - Edit user permissions
   - Activate/deactivate accounts

---

## Project Structure

```
Django-ecommerce-2/
│
├── Accounts/                   # User authentication app
│   ├── migrations/            # Database migrations
│   ├── templates/Accounts/    # Login & registration templates
│   ├── admin.py              # Custom user admin
│   ├── forms.py              # Registration form
│   ├── models.py             # Custom Account model
│   ├── urls.py               # Authentication URLs
│   └── views.py              # Login & registration views
│
├── TrustBuyV4/                # Main project configuration
│   ├── settings.py           # Project settings
│   ├── urls.py               # Main URL configuration
│   ├── wsgi.py               # WSGI configuration
│   └── asgi.py               # ASGI configuration
│
├── cart/                      # Shopping cart app
│   ├── migrations/           # Database migrations
│   ├── models.py             # Cart & CartItem models
│   ├── views.py              # Cart operations & checkout
│   ├── urls.py               # Cart URLs
│   ├── context_processors.py # Cart counter processor
│   └── admin.py              # Cart admin
│
├── category/                  # Product categories app
│   ├── migrations/           # Database migrations
│   ├── models.py             # Category model
│   ├── context_processors.py # Category menu processor
│   ├── admin.py              # Category admin
│   └── urls.py               # Category URLs
│
├── home/                      # Homepage app
│   ├── templates/home/       # Homepage templates
│   │   ├── base.html        # Base template
│   │   └── home.html        # Homepage template
│   ├── static/               # Static files (CSS, JS, images)
│   ├── views.py              # Homepage & product detail views
│   ├── urls.py               # Home URLs
│   └── migrations/           # Database migrations
│
├── store/                     # Product store app
│   ├── templates/store/      # Store templates
│   │   ├── store.html       # Product listing
│   │   ├── product_detail.html
│   │   ├── cart.html
│   │   └── checkout.html
│   ├── migrations/           # Database migrations
│   ├── models.py             # Product model
│   ├── views.py              # Store views
│   ├── urls.py               # Store URLs
│   └── admin.py              # Product admin
│
├── media/                     # User-uploaded media files
│   └── photos/               # Product images
│
├── db.sqlite3                 # SQLite database
├── manage.py                  # Django management script
├── LICENSE                    # Proprietary license
└── README.md                  # This file
```

---

## Database Schema

### Entity Relationship Diagram

```
┌─────────────────┐
│    Account      │
│─────────────────│
│ id (PK)         │
│ first_name      │
│ last_name       │
│ username        │
│ email (UNIQUE)  │
│ phone_number    │
│ password        │
│ is_admin        │
│ is_staff        │
│ is_active       │
└─────────────────┘

┌─────────────────┐         ┌─────────────────┐
│    Category     │         │     Product     │
│─────────────────│         │─────────────────│
│ id (PK)         │◄───────┐│ id (PK)         │
│ category_name   │        ││ product_name    │
│ slug            │        ││ product_brand   │
│ description     │        ││ product_price   │
│ cart_image      │        ││ product_description│
└─────────────────┘        ││ product_specs   │
                           ││ product_image   │
                           ││ stock           │
                           ││ is_available    │
                           ││ category_id (FK)│
                           │└─────────────────┘
                           │         ▲
                           │         │
┌─────────────────┐        │ ┌───────┴─────────┐
│      Cart       │        │ │    CartItem     │
│─────────────────│        │ │─────────────────│
│ id (PK)         │◄───────┼─│ id (PK)         │
│ cart_id         │        │ │ product_id (FK) │
│ date_added      │        │ │ cart_id (FK)    │
└─────────────────┘        └─│ quantity        │
                             │ is_active       │
                             └─────────────────┘
```

### Model Details

#### Account Model
- **Purpose**: Custom user authentication
- **Username Field**: Email (instead of username)
- **Authentication**: Django's AbstractBaseUser
- **Permissions**: Admin, staff, superadmin roles

#### Category Model
- **Purpose**: Product categorization
- **Fields**: Name, slug, description, image
- **Relationship**: One-to-Many with Product
- **URL**: SEO-friendly slug URLs

#### Product Model
- **Purpose**: Product catalog
- **Fields**: Name, brand, price, description, specs, image, stock
- **Relationship**: Many-to-One with Category
- **Features**: Stock tracking, availability flag

#### Cart Model
- **Purpose**: Session-based shopping cart
- **Identification**: Unique cart_id from session
- **Persistence**: Database-backed sessions

#### CartItem Model
- **Purpose**: Items in shopping cart
- **Relationships**:
  - Many-to-One with Cart
  - Many-to-One with Product
- **Calculations**: Subtotal method (price × quantity)

---

## Configuration

### Settings Overview

**File**: `TrustBuyV4/settings.py`

#### Database Configuration

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```

#### Static Files

```python
STATIC_URL = 'static/'
STATICFILES_DIRS = [BASE_DIR / 'home/static']
```

#### Media Files

```python
MEDIA_URL = '/media/'
MEDIA_ROOT = BASE_DIR / 'media'
```

#### Custom User Model

```python
AUTH_USER_MODEL = 'Accounts.Account'
```

#### Session Configuration

```python
SESSION_ENGINE = 'django.contrib.sessions.backends.db'
SESSION_SAVE_EVERY_REQUEST = True
```

#### Context Processors

```python
TEMPLATES['OPTIONS']['context_processors'] = [
    # ... default processors
    'category.context_processors.menu_links',  # Category menu
    'cart.context_processors.counter',          # Cart counter
]
```

### Environment Variables

For production deployment, create a `.env` file:

```env
SECRET_KEY=your-secret-key-here
DEBUG=False
ALLOWED_HOSTS=yourdomain.com,www.yourdomain.com
DATABASE_URL=your-database-url
PAYPAL_CLIENT_ID=your-paypal-client-id
PAYPAL_SECRET=your-paypal-secret
```

---

## Screenshots

### Homepage
The landing page displays featured products in a clean, responsive grid layout.

### Product Detail
Detailed product view with specifications, pricing, and add-to-cart functionality.

### Shopping Cart
Review cart items with quantity adjustment and total calculation including tax.

### Checkout
Secure checkout process with PayPal integration for payment processing.

### Admin Dashboard
Comprehensive backend for managing products, categories, and users.

---

## API Endpoints

### Main URL Patterns

| URL Pattern | View | Description |
|-------------|------|-------------|
| `/` | home.views.home | Homepage |
| `/product/<pk>/` | home.views.ProductDetailView | Product details |
| `/store/` | store.views.store | All products |
| `/store/<slug>/` | store.views.store | Category filter |
| `/cart/` | cart.views.cart | View cart |
| `/cart/add_cart/<pk>` | cart.views.add_cart | Add to cart |
| `/cart/delete_cart/<id>` | cart.views.delete_cart | Decrease quantity |
| `/cart/remove-cart/<id>` | cart.views.remove_cart | Remove item |
| `/cart/checkout/` | cart.views.checkout | Checkout page |
| `/accounts/register/` | Accounts.views.register | User registration |
| `/accounts/login/` | Accounts.views.log_in | User login |
| `/admin/` | Django admin | Admin panel |

---

## Context Processors

### Category Menu Links
**File**: `category/context_processors.py`

Provides global access to all categories for the navigation menu.

```python
def menu_links(request):
    links = category.objects.all()
    return dict(links=links)
```

### Cart Counter
**File**: `cart/context_processors.py`

Displays the total quantity of items in the user's cart.

```python
def counter(request):
    cart_counter = 0
    # Calculates total items in cart
    return dict(cart_counter=cart_counter)
```

---

## Security Considerations

### Current Setup (Development)

⚠️ **The following settings are for development only:**

- `DEBUG = True` - Should be `False` in production
- Secret key exposed in settings.py
- No environment variables configuration
- PayPal sandbox credentials in template
- SQLite database (consider PostgreSQL for production)

### Production Recommendations

1. **Environment Variables**
   - Use `python-decouple` or `django-environ`
   - Store sensitive data in `.env` file
   - Never commit `.env` to version control

2. **Security Settings**
   ```python
   DEBUG = False
   ALLOWED_HOSTS = ['yourdomain.com']
   SECURE_SSL_REDIRECT = True
   SESSION_COOKIE_SECURE = True
   CSRF_COOKIE_SECURE = True
   ```

3. **Database**
   - Migrate to PostgreSQL or MySQL
   - Use connection pooling
   - Regular backups

4. **Static Files**
   - Use CDN for static file serving
   - Configure `collectstatic` for production
   - Enable gzip compression

5. **Payment Processing**
   - Move PayPal credentials to backend
   - Use environment variables for API keys
   - Implement proper error handling

---

## Future Enhancements

### Planned Features

- [ ] Order management system
- [ ] Order history for users
- [ ] Email verification for registration
- [ ] Password reset functionality
- [ ] User dashboard/profile page
- [ ] Product reviews and ratings
- [ ] Product search functionality
- [ ] Advanced filtering (price range, size, color)
- [ ] Product variations (size, color options)
- [ ] Wishlist functionality
- [ ] Inventory management
- [ ] Sales and discount system
- [ ] Email notifications (order confirmation, shipping)
- [ ] Multi-image product gallery
- [ ] Related products recommendations
- [ ] Social media authentication
- [ ] Shipping address management
- [ ] Multiple payment gateway options

### Performance Optimizations

- [ ] Implement caching (Redis)
- [ ] Database query optimization
- [ ] Lazy loading for images
- [ ] Pagination for product listings
- [ ] API endpoints for AJAX operations

### DevOps

- [ ] Docker containerization
- [ ] CI/CD pipeline setup
- [ ] Automated testing suite
- [ ] Production deployment guide
- [ ] Monitoring and logging

---

## Testing

### Running Tests

```bash
# Run all tests
python manage.py test

# Run tests for specific app
python manage.py test Accounts
python manage.py test cart
python manage.py test store
```

### Test Coverage

```bash
# Install coverage tool
pip install coverage

# Run tests with coverage
coverage run --source='.' manage.py test
coverage report
coverage html
```

---

## Deployment

### Production Checklist

- [ ] Set `DEBUG = False`
- [ ] Configure `ALLOWED_HOSTS`
- [ ] Set up environment variables
- [ ] Configure production database
- [ ] Set up static file serving (WhiteNoise/CDN)
- [ ] Configure email backend
- [ ] Set up HTTPS/SSL
- [ ] Configure secure cookies
- [ ] Set up logging
- [ ] Create backup strategy
- [ ] Configure CORS if needed
- [ ] Set up monitoring (Sentry)
- [ ] Performance testing

### Deployment Platforms

**Recommended platforms:**
- **Heroku** - Easy deployment, free tier available
- **DigitalOcean** - VPS with more control
- **AWS Elastic Beanstalk** - Scalable AWS solution
- **PythonAnywhere** - Simple Django hosting
- **Railway** - Modern deployment platform

---

## Troubleshooting

### Common Issues

**Issue**: `No such table` error
```bash
# Solution: Run migrations
python manage.py migrate
```

**Issue**: Static files not loading
```bash
# Solution: Collect static files
python manage.py collectstatic
```

**Issue**: Can't upload images
```bash
# Solution: Install Pillow
pip install Pillow
```

**Issue**: Cart counter not showing
```bash
# Solution: Check context processors in settings.py
# Ensure 'cart.context_processors.counter' is included
```

**Issue**: PayPal not working
```bash
# Solution: Verify PayPal sandbox credentials
# Check browser console for JavaScript errors
```

---

## Contributing

Contributions are welcome! Please follow these guidelines:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Commit your changes**
   ```bash
   git commit -m "Add amazing feature"
   ```
4. **Push to the branch**
   ```bash
   git push origin feature/amazing-feature
   ```
5. **Open a Pull Request**

### Coding Standards

- Follow PEP 8 style guide for Python
- Write descriptive commit messages
- Add docstrings to functions and classes
- Update documentation for new features
- Write tests for new functionality

---

## License

**PROPRIETARY LICENSE**

Copyright (c) 2026 Andrew Romany. All Rights Reserved.

This software and associated documentation files (the "Software") are the proprietary and confidential information of Andrew Romany. Unauthorized copying, distribution, modification, or use of this Software is strictly prohibited without express written permission.

See the [LICENSE](LICENSE) file for full details.

---

## Contact

**Author**: Andrew Romany

**Repository**: [https://github.com/Andro0o0o0w-Romany/Django-ecommerce-2](https://github.com/Andro0o0o0w-Romany/Django-ecommerce-2)

For questions, issues, or permission requests, please open an issue on GitHub.

---

## Acknowledgments

- **Django** - The web framework for perfectionists with deadlines
- **Bootstrap** - Responsive CSS framework
- **PayPal** - Payment processing
- **Font Awesome** - Icon library
- **jQuery** - JavaScript library

---

## Project Statistics

- **Lines of Code**: ~5,000+
- **Django Apps**: 5
- **Database Models**: 5
- **URL Patterns**: 15+
- **Templates**: 10+
- **Migrations**: 79
- **Django Version**: 4.1.4
- **Python Version**: 3.9+

---

<div align="center">

**Made with ❤️ by Andrew Romany**

⭐ Star this repository if you find it useful!

</div>
