Inventory Management System
This project is a simple Inventory Management System built using Django Rest Framework. The system supports CRUD operations on inventory items and uses JWT-based authentication for secure access. The API leverages PostgreSQL for the database, Redis for caching, and includes unit tests to ensure functionality. Proper error handling with appropriate error codes and integrated logging for debugging and monitoring are also implemented.

Features
JWT Authentication: Secure all endpoints.

CRUD Operations: Create, read, update, and delete inventory items.

Caching: Improve performance using Redis.

Logging: Integrated logging for API usage and error tracking.

Unit Testing: Ensures functionality through comprehensive tests.

Technologies Used
Django

Django Rest Framework

PostgreSQL

Redis

JWT Authentication

Setup Instructions
Prerequisites
Python 3.8+

PostgreSQL

Redis

pip (Python package installer)

Installation
Clone the repository:

sh


git clone https://github.com/yourusername/inventory-management-system.git
cd inventory-management-system
Create and activate a virtual environment:

sh


python3 -m venv env
source env/bin/activate
Install dependencies:

sh


pip install -r requirements.txt
Configure PostgreSQL and Redis in your settings.py:

python


DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'inventory_db',
        'USER': 'your_db_user',
        'PASSWORD': 'your_db_password',
        'HOST': 'localhost',
        'PORT': '',
    }
}

CACHES = {
    'default': {
        'BACKEND': 'django_redis.cache.RedisCache',
        'LOCATION': 'redis://127.0.0.1:6379/1',
        'OPTIONS': {
            'CLIENT_CLASS': 'django_redis.client.DefaultClient',
        }
    }
}
Run database migrations:

sh


python manage.py makemigrations
python manage.py migrate
Create a superuser for accessing the admin panel:

sh


python manage.py createsuperuser
Start the development server:

sh


python manage.py runserver
Endpoints
User Registration and Authentication

POST /register/ - Create a new user

POST /api/token/ - Obtain JWT token

POST /api/token/refresh/ - Refresh JWT token

CRUD Operations on Items

POST /items/ - Create a new item

GET /items/{item_id}/ - Retrieve an item

PUT /items/{item_id}/ - Update an item

DELETE /items/{item_id}/ - Delete an item

Caching
The retrieve method in the ItemViewSet uses Redis to cache item details for improved performance. The cache key is based on the item ID.

Testing
Unit tests for all endpoints are included in tests.py. Run the tests using:

sh


python manage.py test
Logging
Logging is configured to track API usage, errors, and other significant events. Logs are stored in debug.log.

License
This project is licensed under the MIT License. See the LICENSE file for details.
