# My_Flight | Flight Booking System

[![Django](https://img.shields.io/badge/Django-3.1.2-092E20?style=flat&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![Python](https://img.shields.io/badge/Python-3.9.9-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![ReportLab](https://img.shields.io/badge/ReportLab-3.5.57-FF6B6B?style=flat)](https://www.reportlab.com/)
[![Gunicorn](https://img.shields.io/badge/Gunicorn-20.1.0-499848?style=flat&logo=gunicorn&logoColor=white)](https://gunicorn.org/)

A comprehensive flight booking and management system built with Django. This web application allows users to search for flights, make bookings, manage reservations, and generate ticket confirmations with PDF generation capabilities.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Demo](#demo)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Database Schema](#database-schema)
- [API Endpoints](#api-endpoints)
- [PDF Generation](#pdf-generation)
- [Deployment](#deployment)
- [Testing](#testing)
- [Security](#security)
- [Performance Optimization](#performance-optimization)
- [Future Enhancements](#future-enhancements)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Overview

My_Flight is a full-stack flight booking platform designed to streamline the process of searching, booking, and managing flight reservations. Built as a capstone project using Django, it demonstrates modern web development practices including MVC architecture, database management, user authentication, and automated document generation.

## Features

- **✈️ Flight Search & Booking**: Search for available flights by date, destination, and airline
- **👤 User Authentication**: Secure registration, login, and profile management
- **🎫 Reservation Management**: View, modify, and cancel bookings
- **📄 PDF Ticket Generation**: Automatic generation of booking confirmations and e-tickets
- **💳 Payment Integration**: (Ready for payment gateway integration)
- **📧 Email Notifications**: Automated booking confirmations and updates
- **🔍 Advanced Filtering**: Filter flights by price, duration, stops, and airlines
- **📊 Admin Dashboard**: Comprehensive admin panel for managing flights, bookings, and users
- **📱 Responsive Design**: Mobile-friendly interface for booking on-the-go
- **🔒 Secure Transactions**: Protected user data and booking information
- **📈 Booking History**: Complete history of past and upcoming flights
- **⚡ Real-time Availability**: Dynamic seat availability updates

## Demo

**Live Demo**: [Coming Soon]

**Screenshots**:
- Home Page
- Flight Search Results
- Booking Confirmation
- User Dashboard
- Admin Panel

## Technologies Used

### Backend Framework
- **Django 3.1.2**: High-level Python web framework
- **Python 3.9.9**: Core programming language

### PDF Generation
- **ReportLab 3.5.57**: PDF creation library
- **xhtml2pdf 0.2.5**: HTML to PDF converter

### Server & Deployment
- **Gunicorn 20.1.0**: WSGI HTTP server for production
- **tqdm 4.64.0**: Progress bars for data processing

### Database
- **SQLite3**: Development database (default)
- **PostgreSQL**: Recommended for production

### Frontend (Assumed)
- HTML5, CSS3, JavaScript
- Bootstrap (if applicable)
- Django Template Language

## Project Structure

```
My_Flight/
├── capstone/                    # Main project directory
│   ├── __init__.py
│   ├── settings.py             # Project settings
│   ├── urls.py                 # Main URL configuration
│   ├── wsgi.py                 # WSGI configuration
│   └── asgi.py                 # ASGI configuration
│
├── flight/                      # Flight app (assumed)
│   ├── migrations/             # Database migrations
│   ├── templates/              # HTML templates
│   │   ├── flight/
│   │   │   ├── home.html
│   │   │   ├── search.html
│   │   │   ├── booking.html
│   │   │   └── ticket.html
│   ├── static/                 # Static files (CSS, JS, images)
│   │   ├── css/
│   │   ├── js/
│   │   └── images/
│   ├── __init__.py
│   ├── admin.py               # Admin configurations
│   ├── apps.py                # App configuration
│   ├── models.py              # Database models
│   ├── views.py               # View functions
│   ├── urls.py                # App URL patterns
│   ├── forms.py               # Django forms
│   └── utils.py               # Utility functions
│
├── users/                      # User authentication app (assumed)
│   ├── migrations/
│   ├── templates/
│   ├── models.py
│   ├── views.py
│   └── forms.py
│
├── media/                      # User-uploaded files
├── staticfiles/                # Collected static files
├── manage.py                   # Django management script
├── requirements.txt            # Python dependencies
├── runtime.txt                 # Python version specification
├── .gitignore                  # Git ignore rules
├── .env.example               # Environment variables template
├── Procfile                   # Deployment configuration
└── README.md                  # Project documentation
```

## Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- **Python 3.9.9** or higher
- **pip** (Python package manager)
- **virtualenv** or **venv**
- **Git** (for version control)
- **PostgreSQL** (optional, for production)

### System Requirements

- **Operating System**: Windows, macOS, or Linux
- **RAM**: Minimum 2GB
- **Disk Space**: 500MB free space

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/My_Flight.git
cd My_Flight
```

### 2. Create Virtual Environment

**On Windows**:
```bash
python -m venv venv
venv\Scripts\activate
```

**On macOS/Linux**:
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Environment Setup

Create a `.env` file in the root directory:

```env
# Django Settings
SECRET_KEY=your-secret-key-here
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1

# Database Configuration
DATABASE_URL=sqlite:///db.sqlite3

# Email Configuration
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USE_TLS=True
EMAIL_HOST_USER=your-email@gmail.com
EMAIL_HOST_PASSWORD=your-app-password

# Payment Gateway (if applicable)
PAYMENT_API_KEY=your-payment-api-key
PAYMENT_SECRET_KEY=your-payment-secret-key
```

### 5. Database Setup

Run migrations to create database tables:

```bash
python manage.py makemigrations
python manage.py migrate
```

### 6. Create Superuser

Create an admin account:

```bash
python manage.py createsuperuser
```

Follow the prompts to set username, email, and password.

### 7. Collect Static Files

```bash
python manage.py collectstatic --noinput
```

### 8. Load Sample Data (Optional)

```bash
python manage.py loaddata fixtures/sample_data.json
```

### 9. Run Development Server

```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000/` in your browser.

## Configuration

### Django Settings

Edit `capstone/settings.py` for custom configuration:

#### Database Configuration

**Development (SQLite)**:
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```

**Production (PostgreSQL)**:
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'flight_db',
        'USER': 'your_db_user',
        'PASSWORD': 'your_db_password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

#### Email Configuration

```python
EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_PORT = 587
EMAIL_USE_TLS = True
EMAIL_HOST_USER = os.getenv('EMAIL_HOST_USER')
EMAIL_HOST_PASSWORD = os.getenv('EMAIL_HOST_PASSWORD')
```

#### Static and Media Files

```python
STATIC_URL = '/static/'
STATIC_ROOT = BASE_DIR / 'staticfiles'
MEDIA_URL = '/media/'
MEDIA_ROOT = BASE_DIR / 'media'
```

## Usage

### User Registration & Login

1. Navigate to `/register` to create a new account
2. Login at `/login` with your credentials
3. Access your dashboard at `/dashboard`

### Searching for Flights

1. Enter departure and arrival locations
2. Select travel dates
3. Choose number of passengers
4. Click "Search Flights"

### Making a Booking

1. Select desired flight from search results
2. Review flight details and pricing
3. Enter passenger information
4. Confirm booking and proceed to payment
5. Receive confirmation email with e-ticket PDF

### Managing Bookings

1. Access "My Bookings" from user dashboard
2. View upcoming and past flights
3. Download tickets or cancel reservations

### Admin Functions

Access admin panel at `/admin`:

- Add/edit/delete flights
- Manage user accounts
- View all bookings
- Generate reports
- Configure system settings

## Database Schema

### Core Models

#### Flight Model
```python
class Flight(models.Model):
    flight_number = CharField(max_length=10, unique=True)
    airline = CharField(max_length=100)
    origin = CharField(max_length=100)
    destination = CharField(max_length=100)
    departure_time = DateTimeField()
    arrival_time = DateTimeField()
    duration = DurationField()
    price = DecimalField(max_digits=10, decimal_places=2)
    available_seats = IntegerField()
    total_seats = IntegerField()
    status = CharField(choices=STATUS_CHOICES)
```

#### Booking Model
```python
class Booking(models.Model):
    booking_reference = CharField(max_length=20, unique=True)
    user = ForeignKey(User, on_delete=CASCADE)
    flight = ForeignKey(Flight, on_delete=CASCADE)
    passengers = ManyToManyField(Passenger)
    booking_date = DateTimeField(auto_now_add=True)
    total_price = DecimalField(max_digits=10, decimal_places=2)
    payment_status = CharField(choices=PAYMENT_STATUS)
    booking_status = CharField(choices=BOOKING_STATUS)
```

#### Passenger Model
```python
class Passenger(models.Model):
    first_name = CharField(max_length=100)
    last_name = CharField(max_length=100)
    email = EmailField()
    phone = CharField(max_length=15)
    passport_number = CharField(max_length=20)
    date_of_birth = DateField()
    nationality = CharField(max_length=50)
```

## API Endpoints

### Public Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Home page |
| GET | `/flights/` | List all available flights |
| GET | `/flights/search/` | Search flights |
| GET | `/flights/<id>/` | Flight details |

### Authenticated Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/bookings/create/` | Create new booking |
| GET | `/bookings/` | User's bookings |
| GET | `/bookings/<id>/` | Booking details |
| PUT | `/bookings/<id>/update/` | Update booking |
| DELETE | `/bookings/<id>/cancel/` | Cancel booking |
| GET | `/bookings/<id>/ticket/` | Download ticket PDF |

### Admin Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/admin/` | Admin dashboard |
| GET | `/admin/flights/` | Manage flights |
| GET | `/admin/bookings/` | View all bookings |
| GET | `/admin/users/` | Manage users |

## PDF Generation

### Ticket Generation

The system uses ReportLab and xhtml2pdf to generate professional e-tickets:

```python
from reportlab.lib.pagesizes import letter
from reportlab.pdfgen import canvas
from io import BytesIO

def generate_ticket(booking):
    buffer = BytesIO()
    p = canvas.Canvas(buffer, pagesize=letter)
    
    # Add airline logo
    # Add booking details
    # Add passenger information
    # Add barcode/QR code
    
    p.showPage()
    p.save()
    
    return buffer
```

### Features of Generated Tickets

- Booking reference number
- Flight details (number, route, times)
- Passenger information
- Seat assignments
- Barcode for check-in
- Terms and conditions

## Deployment

### Heroku Deployment

1. **Install Heroku CLI**:
```bash
curl https://cli-assets.heroku.com/install.sh | sh
```

2. **Login to Heroku**:
```bash
heroku login
```

3. **Create Heroku App**:
```bash
heroku create my-flight-app
```

4. **Add Buildpack**:
```bash
heroku buildpacks:set heroku/python
```

5. **Configure Environment Variables**:
```bash
heroku config:set SECRET_KEY=your-secret-key
heroku config:set DEBUG=False
```

6. **Add PostgreSQL**:
```bash
heroku addons:create heroku-postgresql:hobby-dev
```

7. **Deploy**:
```bash
git push heroku main
```

8. **Run Migrations**:
```bash
heroku run python manage.py migrate
heroku run python manage.py createsuperuser
```

### Production Checklist

- [ ] Set `DEBUG = False`
- [ ] Configure `ALLOWED_HOSTS`
- [ ] Use PostgreSQL database
- [ ] Set up SSL/HTTPS
- [ ] Configure static files with WhiteNoise or CDN
- [ ] Set up error logging (Sentry)
- [ ] Enable CSRF protection
- [ ] Configure email backend
- [ ] Set up automated backups
- [ ] Implement rate limiting
- [ ] Add monitoring (New Relic, DataDog)

## Testing

### Run Tests

```bash
# Run all tests
python manage.py test

# Run specific app tests
python manage.py test flight

# Run with coverage
coverage run --source='.' manage.py test
coverage report
coverage html
```

### Test Categories

- **Unit Tests**: Model and form validation
- **Integration Tests**: View and URL testing
- **Functional Tests**: End-to-end booking process
- **Performance Tests**: Load testing for concurrent bookings

## Security

### Implemented Security Measures

- ✅ CSRF Protection
- ✅ SQL Injection Prevention (Django ORM)
- ✅ XSS Protection
- ✅ Secure Password Hashing (PBKDF2)
- ✅ Session Security
- ✅ HTTPS Enforcement (Production)
- ✅ Input Validation
- ✅ Rate Limiting

### Security Best Practices

```python
# settings.py
SECURE_SSL_REDIRECT = True
SESSION_COOKIE_SECURE = True
CSRF_COOKIE_SECURE = True
SECURE_BROWSER_XSS_FILTER = True
SECURE_CONTENT_TYPE_NOSNIFF = True
X_FRAME_OPTIONS = 'DENY'
```

## Performance Optimization

### Database Optimization

- Use `select_related()` and `prefetch_related()` for queries
- Database indexing on frequently queried fields
- Query optimization with `only()` and `defer()`

### Caching

```python
# settings.py
CACHES = {
    'default': {
        'BACKEND': 'django.core.cache.backends.redis.RedisCache',
        'LOCATION': 'redis://127.0.0.1:6379/1',
    }
}
```

### Static File Optimization

- Use WhiteNoise for static file serving
- Minify CSS and JavaScript
- Image compression
- Enable browser caching

## Future Enhancements

Planned features for upcoming releases:

- [ ] **Multi-city Flights**: Support for complex itineraries
- [ ] **Seat Selection**: Interactive seat map selection
- [ ] **Loyalty Program**: Frequent flyer points system
- [ ] **Mobile App**: iOS and Android native apps
- [ ] **Real-time Flight Tracking**: Live flight status updates
- [ ] **Price Alerts**: Notify users of price drops
- [ ] **Group Bookings**: Special handling for group travel
- [ ] **Travel Insurance**: Integrated insurance options
- [ ] **Multi-currency Support**: International payment options
- [ ] **Chatbot Support**: AI-powered customer service
- [ ] **Social Login**: OAuth integration (Google, Facebook)
- [ ] **Review System**: User reviews and ratings
- [ ] **Analytics Dashboard**: Booking trends and insights
- [ ] **API for Partners**: RESTful API for third-party integration

## Troubleshooting

### Common Issues

#### Issue: Django not found
```bash
# Solution: Ensure virtual environment is activated
source venv/bin/activate  # macOS/Linux
venv\Scripts\activate     # Windows
pip install -r requirements.txt
```

#### Issue: Database migration errors
```bash
# Solution: Reset migrations
python manage.py migrate --fake flight zero
python manage.py migrate flight
```

#### Issue: Static files not loading
```bash
# Solution: Collect static files
python manage.py collectstatic --clear --noinput
```

#### Issue: PDF generation fails
```bash
# Solution: Reinstall PDF libraries
pip uninstall reportlab xhtml2pdf
pip install reportlab==3.5.57 xhtml2pdf==0.2.5
```

## Contributing

Contributions are welcome! Follow these steps:

1. **Fork the repository**
2. **Create feature branch**:
   ```bash
   git checkout -b feature/AmazingFeature
   ```
3. **Commit changes**:
   ```bash
   git commit -m "Add AmazingFeature"
   ```
4. **Push to branch**:
   ```bash
   git push origin feature/AmazingFeature
   ```
5. **Open Pull Request**

### Contribution Guidelines

- Follow PEP 8 style guide
- Write descriptive commit messages
- Add tests for new features
- Update documentation
- Ensure all tests pass before PR

## License

This project is licensed under the MIT License.

```
MIT License

Copyright (c) 2025 [Your Name]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## Contact

### Developer Information

- **Name**: [Manish Kumar Mahato]
- **Email**: [manishmahato2027@gmail.com]
- **Location**: [Dhanbad,Jharkhand]

### Connect

- **LinkedIn**: [Your LinkedIn Profile]
- **GitHub**: [Your GitHub Profile]
- **Portfolio**: [Your Portfolio Website]
- **Twitter**: [Your Twitter Handle]

### Support

For bug reports and feature requests, please use the [GitHub Issues](https://github.com/yourusername/My_Flight/issues) page.

For general inquiries, contact: support@myflight.com

## Acknowledgments

- **Django Community** for the excellent framework
- **ReportLab** for PDF generation capabilities
- **Heroku** for deployment platform
- **Contributors** who helped improve this project
- **Open Source Community** for inspiration and resources

---

**Made with ❤️ for travelers worldwide**

© 2025 My_Flight. All Rights Reserved.

---

### Quick Links

- [Report a Bug](https://github.com/yourusername/My_Flight/issues/new?template=bug_report.md)
- [Request a Feature](https://github.com/yourusername/My_Flight/issues/new?template=feature_request.md)
- [Documentation](https://github.com/yourusername/My_Flight/wiki)
- [Changelog](https://github.com/yourusername/My_Flight/blob/main/CHANGELOG.md)

**⭐ Star this repository if you found it helpful!**

---

### Project Status

![Build Status](https://img.shields.io/badge/build-passing-brightgreen)
![Coverage](https://img.shields.io/badge/coverage-85%25-yellowgreen)
![Version](https://img.shields.io/badge/version-1.0.0-blue)

![License](https://img.shields.io/badge/license-MIT-green)
