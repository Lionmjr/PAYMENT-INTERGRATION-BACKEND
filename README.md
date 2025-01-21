# Pesapal Payment API Integration

This project provides a Django-based API for integrating with the Pesapal payment gateway. It supports initiating payments, handling payment callbacks, and retrieving the iframe URL for payment processing.

---

## Table of Contents

1. [Requirements](#requirements)
2. [Installation](#installation)
3. [Environment Variables](#environment-variables)
4. [Usage](#usage)
   - [Starting the Server](#starting-the-server)
   - [API Endpoints](#api-endpoints)
     - [Initiate Payment](#1-initiate-payment)
     - [Payment Callback](#2-payment-callback)
5. [Authentication with Pesapal APIs](#authentication-with-pesapal-apis)
6. [Retrieving the Pesapal Iframe URL](#retrieving-the-pesapal-iframe-url)
7. [Project Structure](#project-structure)
8. [Troubleshooting](#troubleshooting)
9. [License](#license)

---

## Requirements

- Python 3.10 or above
- Django 5.1.5
- Django REST Framework
- Pesapal API credentials (Consumer Key and Consumer Secret)

---

## Installation

1. Clone the repository:
   ```bash
   git clone <repository_url>
   cd <repository_directory>
   
Set up a virtual environment and install dependencies:
python -m venv env
source env/bin/activate  # On Windows: `env\Scripts\activate`
pip install -r requirements.txt

Configure your .env file: Add the following variables to your .env file:
DJANGO_SECRET_KEY=your_secret_key
PESAPAL_CONSUMER_KEY=your_consumer_key
PESAPAL_CONSUMER_SECRET=your_consumer_secret
PESAPAL_CALLBACK_URL=https://yourdomain.com/response-page
Apply database migrations:

bash
Copy
Edit
python manage.py migrate
Start the server:


##ENVIRONMENT VARIABLES
The .env file must contain the following variables:
DJANGO_SECRET_KEY=your_secret_key
PESAPAL_CONSUMER_KEY=your_consumer_key
PESAPAL_CONSUMER_SECRET=your_consumer_secret
PESAPAL_CALLBACK_URL=https://yourdomain.com/response-page

##USAGE
Starting the Server
Start the development server with the following command:
python manage.py runserver

##API Endpoints
1. Initiate Payment
Endpoint: /api/initiate-payment/
Method: POST
Request Body:
json
{
  "currency": "KES",
  "amount": 100.00,
  "description": "Payment for goods",
  "billing_address": {
    "email": "customer@example.com",
    "phone_number": "254700000000"
  }
}
Response:
json
{
  "order_tracking_id": "tracking_id",
  "redirect_url": "iframe_url"
}


Authentication with Pesapal APIs
The PesapalAPI utility automates the following steps:

Obtain an authentication token:

The API fetches the token using the Consumer Key and Consumer Secret provided in the .env file.
Register an IPN (Instant Payment Notification):

An IPN is registered during payment initialization. The returned IPN ID is used to track notifications.
Retrieving the Pesapal Iframe URL
Make a POST request to the /api/initiate-payment/ endpoint.
The API response includes:
order_tracking_id: A unique identifier for the payment.
redirect_url: The iframe URL for the payment process.
Use the redirect_url in your frontend to embed the payment interface.

Project Structure
views.py: Contains the API views for initiating payments and handling callbacks.
settings.py: Configuration for the Django project, including Pesapal settings.
manage.py: Entry point for Django management commands.


Troubleshooting
Ensure your .env file is correctly configured with valid Pesapal API credentials.
Check the debug.log file for error detaila

