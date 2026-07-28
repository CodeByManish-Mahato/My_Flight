# Flight Booking System | Django Web Application

[![Django](https://img.shields.io/badge/Django-6.0.1-092E20?style=flat&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![Python](https://img.shields.io/badge/Python-3.11.9-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Gunicorn](https://img.shields.io/badge/Gunicorn-23.0.0-green?style=flat)](https://gunicorn.org/)

A full-featured Django web application with PDF generation capabilities, built as a capstone project showcasing modern web development practices and deployment-ready configuration.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [Deployment](#deployment)
- [PDF Generation](#pdf-generation)
- [Database](#database)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Overview

This Django capstone project demonstrates a complete web application with essential features including user management, data handling, and PDF report generation. Built with Django 6.0.1 and Python 3.11.9, it showcases best practices in web development, including proper project structure, database management, and production-ready deployment configuration.

## Features

- 🚀 **Modern Django Framework**: Built with Django 6.0.1
- 📄 **PDF Generation**: Advanced PDF creation and manipulation using ReportLab and xhtml2pdf
- 🗄️ **Database Management**: SQLite database with Django ORM
- 🔐 **User Authentication**: Django's built-in authentication system
- 📊 **Admin Interface**: Powerful Django admin panel for data management
- 🌐 **Production Ready**: Configured for deployment with Gunicorn
- 📦 **Static Files Management**: Organized static files handling
- 🔧 **Modular Architecture**: Clean, maintainable code structure
- 📈 **Progress Tracking**: Built-in progress monitoring with tqdm
- 🚢 **Deployment Scripts**: Automated build and deployment process

## Technologies Used

### Core Framework
- **Django 6.0.1**: High-level Python web framework
- **Python 3.11.9**: Programming language

### PDF Processing
- **ReportLab 4.4.9**: PDF generation library
- **xhtml2pdf 0.2.17**: HTML to PDF conversion

### Web Server
- **Gunicorn 23.0.0**: Python WSGI HTTP Server for production

### Utilities
- **tqdm 4.67.1**: Progress bar for Python

### Database
- **SQLite3**: Lightweight database (included with Python)

## Project Structure

```
capstone/
├── manage.py              # Django management script
├── requirements.txt       # Python dependencies
├── runtime.txt           # Python version specification
├── Procfile              # Deployment configuration (Heroku/Render)
├── build.sh              # Build script for deployment
├── db.sqlite3            # SQLite database
├── Licence               # MIT License file
├── .gitignore            # Git ignore configuration
├── README.md             # Project documentation
└── capstone/             # Main project directory
    ├── __init__.py
    ├── settings.py       # Project settings
    ├── urls.py           # URL configuration
    ├── wsgi.py           # WSGI configuration
    └── asgi.py           # ASGI configuration (async support)
```

## Prerequisites

Before you begin, ensure you have the following installed:

- **Python 3.11.9** or higher
- **pip** (Python package installer)
- **virtualenv** (recommended for isolated environments)
- **Git** (for version control)

Check your Python version:
```bash
python --version
```

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/capstone.git
cd capstone
```

### 2. Create Virtual Environment

**On Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

**On macOS/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

This will install:
- Django 6.0.1
- ReportLab 4.4.9
- xhtml2pdf 0.2.17
- tqdm 4.67.1
- Gunicorn 23.0.0

### 4. Apply Migrations

```bash
python manage.py migrate
```

### 5. Create Superuser (Admin Account)

```bash
python manage.py createsuperuser
```

Follow the prompts to create your admin account.

### 6. Collect Static Files

```bash
python manage.py collectstatic
```

## Configuration

### Environment Variables

Create a `.env` file in the project root (optional but recommended):

```env
DEBUG=True
SECRET_KEY=your-secret-key-here
ALLOWED_HOSTS=localhost,127.0.0.1
DATABASE_URL=sqlite:///db.sqlite3
```

### Settings Configuration

Key settings in `capstone/settings.py`:

- **DEBUG**: Set to `False` in production
- **ALLOWED_HOSTS**: Add your domain names
- **DATABASES**: Configure your database
- **STATIC_URL** and **STATIC_ROOT**: Static files configuration
- **MEDIA_URL** and **MEDIA_ROOT**: Media files configuration

## Running the Application

### Development Server

Start the Django development server:

```bash
python manage.py runserver
```

Access the application at: `http://127.0.0.1:8000/`

Access the admin panel at: `http://127.0.0.1:8000/admin/`

### Production Server (with Gunicorn)

For production deployment:

```bash
gunicorn capstone.wsgi:application --bind 0.0.0.0:8000
```

## Deployment

### Automated Deployment (Render/Heroku)

The project includes a `build.sh` script for automated deployment:

```bash
#!/usr/bin/env bash
set -o errexit

pip install -r requirements.txt
python manage.py collectstatic --noinput
python manage.py migrate
```

### Deployment Platforms

#### Render.com
1. Connect your GitHub repository
2. Select "Web Service"
3. Build command: `./build.sh`
4. Start command: `gunicorn capstone.wsgi`
5. Add environment variables

#### Heroku
```bash
heroku create your-app-name
git push heroku main
heroku run python manage.py migrate
heroku run python manage.py createsuperuser
```

#### Railway
1. Connect GitHub repository
2. Railway will auto-detect Django
3. Add environment variables
4. Deploy

### Manual Deployment Checklist

- [ ] Set `DEBUG = False` in settings
- [ ] Configure `ALLOWED_HOSTS`
- [ ] Set up environment variables
- [ ] Configure database (PostgreSQL for production)
- [ ] Set up static files serving
- [ ] Configure HTTPS/SSL
- [ ] Set up monitoring and logging
- [ ] Configure backup strategy

## PDF Generation

This project includes powerful PDF generation capabilities:

### ReportLab Usage

```python
from reportlab.pdfgen import canvas
from reportlab.lib.pagesizes import letter

def create_pdf(filename):
    c = canvas.Canvas(filename, pagesize=letter)
    c.drawString(100, 750, "Hello World")
    c.save()
```

### xhtml2pdf Usage

```python
from xhtml2pdf import pisa

def html_to_pdf(source_html, output_filename):
    with open(output_filename, "w+b") as result_file:
        pisa_status = pisa.CreatePDF(source_html, dest=result_file)
    return pisa_status.err
```

### Use Cases

- Generate invoices and receipts
- Create reports and analytics documents
- Export data to PDF format
- Generate certificates and tickets
- Create printable forms

## Database

### SQLite (Development)

The project uses SQLite by default for development:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```

### PostgreSQL (Production Recommended)

For production, switch to PostgreSQL:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'capstone_db',
        'USER': 'your_username',
        'PASSWORD': 'your_password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

### Database Commands

```bash
# Create migrations
python manage.py makemigrations

# Apply migrations
python manage.py migrate

# View migration status
python manage.py showmigrations

# Database shell
python manage.py dbshell

# Flush database (clear all data)
python manage.py flush
```

## Testing

### Running Tests

```bash
# Run all tests
python manage.py test

# Run specific app tests
python manage.py test app_name

# Run with coverage
coverage run --source='.' manage.py test
coverage report
```

### Writing Tests

Create tests in `tests.py`:

```python
from django.test import TestCase

class YourModelTestCase(TestCase):
    def setUp(self):
        # Set up test data
        pass
    
    def test_model_creation(self):
        # Test logic
        self.assertEqual(1, 1)
```

## Project Management

### Useful Django Commands

```bash
# Create new app
python manage.py startapp app_name

# Django shell
python manage.py shell

# Database shell
python manage.py dbshell

# Check for issues
python manage.py check

# Create admin user
python manage.py createsuperuser

# Change password
python manage.py changepassword username

# Show migrations
python manage.py showmigrations

# Clear cache
python manage.py clear_cache
```

### Managing Dependencies

```bash
# Install package
pip install package_name

# Update requirements.txt
pip freeze > requirements.txt

# Install from requirements
pip install -r requirements.txt

# Upgrade package
pip install --upgrade package_name
```

## Security Best Practices

- ✅ Keep `SECRET_KEY` confidential
- ✅ Set `DEBUG = False` in production
- ✅ Use environment variables for sensitive data
- ✅ Configure `ALLOWED_HOSTS` properly
- ✅ Enable HTTPS in production
- ✅ Use strong passwords
- ✅ Regular security updates
- ✅ Implement CSRF protection
- ✅ Use Django's built-in security features

## Performance Optimization

### Caching

```python
# In settings.py
CACHES = {
    'default': {
        'BACKEND': 'django.core.cache.backends.memcached.MemcachedCache',
        'LOCATION': '127.0.0.1:11211',
    }
}
```

### Database Optimization

- Use `select_related()` and `prefetch_related()`
- Add database indexes
- Optimize queries with Django Debug Toolbar

### Static Files

- Use CDN for static files
- Enable compression
- Implement browser caching

## Troubleshooting

### Common Issues

**Issue**: `ModuleNotFoundError: No module named 'django'`
```bash
Solution: pip install -r requirements.txt
```

**Issue**: Migration conflicts
```bash
Solution: python manage.py migrate --fake-initial
```

**Issue**: Static files not loading
```bash
Solution: python manage.py collectstatic
```

**Issue**: Port already in use
```bash
Solution: python manage.py runserver 8001
```

## Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**:
   ```bash
   git checkout -b feature/AmazingFeature
   ```
3. **Commit your changes**:
   ```bash
   git commit -m "Add some AmazingFeature"
   ```
4. **Push to the branch**:
   ```bash
   git push origin feature/AmazingFeature
   ```
5. **Open a Pull Request**

### Contribution Guidelines

- Follow PEP 8 style guide
- Write meaningful commit messages
- Add tests for new features
- Update documentation
- Ensure all tests pass

## Future Enhancements

Planned features for future releases:

- [ ] User dashboard with analytics
- [ ] RESTful API with Django REST Framework
- [ ] Real-time notifications
- [ ] Advanced search functionality
- [ ] Email integration
- [ ] Payment gateway integration
- [ ] Multi-language support (i18n)
- [ ] Docker containerization
- [ ] CI/CD pipeline setup
- [ ] Enhanced security features
- [ ] Mobile app integration
- [ ] Advanced reporting system

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2025 Manish Kumar Mahato

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

### Manish Kumar Mahato

- **Email**: [manishmahato2027@gmail.com](mailto:manishmahato2027@gmail.com)
- **Phone**: +91 9142928815
- **Location**: Jharkhand, India

### Connect on Social Media

- **LinkedIn**: [Manish Mahato](https://www.linkedin.com/in/manish-mahato-6bb07029a/)
- **GitHub**: [CodebyManish-M](https://github.com/CodebyManish-Mahato)
- **Twitter**: [@ManishMahat0](https://x.com/ManishMahat0)
- **Instagram**: [@hy._.manish](https://www.instagram.com/hy._.manish/)

## Acknowledgments

- Django Software Foundation for the amazing framework
- ReportLab team for PDF generation capabilities
- Open source community for continuous support
- Contributors and testers

## Support

If you encounter any issues or have questions:

1. Check the [Troubleshooting](#troubleshooting) section
2. Search existing [GitHub Issues](https://github.com/yourusername/capstone/issues)
3. Create a new issue with detailed information
4. Contact via email: manishmahato2027@gmail.com

## Resources

- [Django Documentation](https://docs.djangoproject.com/)
- [Python Documentation](https://docs.python.org/)
- [ReportLab Documentation](https://www.reportlab.com/docs/)
- [Django Deployment Checklist](https://docs.djangoproject.com/en/stable/howto/deployment/checklist/)

---

**Made with ❤️ by Manish Kumar Mahato**

© 2025 Manish Kumar Mahato. All Rights Reserved.

---

### Quick Commands Reference

```bash
# Development
python manage.py runserver
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser

# Testing
python manage.py test
python manage.py check

# Deployment
python manage.py collectstatic
gunicorn capstone.wsgi
```

**⭐ Star this repo if you found it helpful!**
