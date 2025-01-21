

# Pesapal Payment API Integration

This project provides a Django-based API for integrating with the Pesapal payment gateway. It supports initiating payments, handling payment callbacks, and retrieving the iframe URL for payment processing.

## Table of Contents

- [Requirements](#requirements)
- [Installation](#installation)
- [Environment Variables](#environment-variables)
- [Usage](#usage)
- [Authentication](#authentication)
- [Project Structure](#project-structure)
- [Troubleshooting](#troubleshooting)

## Requirements

* Python 3.10 or above
* Django 5.1.5
* Django REST Framework
* Pesapal API credentials (Consumer Key and Consumer Secret)

## Installation

1. Clone the repository:
   ```bash
   git clone <repository_url>
   cd <repository_directory>
   ```

2. Set up a virtual environment and install dependencies:
   ```bash
   python -m venv env
   source env/bin/activate  # On Windows: `env\Scripts\activate`
   pip install -r requirements.txt
   ```

3. Apply database migrations:
   ```bash
   python manage.py migrate
   ```

## Environment Variables

Create a `.env` file with the following variables:

```plaintext
DJANGO_SECRET_KEY=your_secret_key
PESAPAL_CONSUMER_KEY=your_consumer_key
PESAPAL_CONSUMER_SECRET=your_consumer_secret
PESAPAL_CALLBACK_URL=https://yourdomain.com/response-page
```

## Usage

### Starting the Server

```bash
python manage.py runserver
```

### API Endpoints

#### 1. Initiate Payment

**Endpoint:** `/api/initiate-payment/`  
**Method:** POST

**Request Body:**
```json
{
  "currency": "KES",
  "amount": 100.00,
  "description": "Payment for goods",
  "billing_address": {
    "email": "customer@example.com",
    "phone_number": "254700000000"
  }
}
```

**Response:**
```json
{
  "order_tracking_id": "tracking_id",
  "redirect_url": "iframe_url"
}
```

## Authentication

The PesapalAPI utility handles authentication automatically through these steps:

1. **Token Generation**: Fetches authentication token using provided Consumer Key and Secret
2. **IPN Registration**: Registers an Instant Payment Notification during payment initialization

## Project Structure

* `views.py`: API views for payment operations
* `settings.py`: Django project configuration
* `manage.py`: Django management commands entry point

## Troubleshooting

* Verify `.env` file contains valid Pesapal API credentials
* Check `debug.log` for detailed error information
* Ensure callback URL is properly configured and accessible


