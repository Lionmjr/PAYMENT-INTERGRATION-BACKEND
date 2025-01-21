# Pesapal Payment API Integration

This project provides a Django-based API for integrating with the Pesapal payment gateway. It supports initiating payments, handling payment callbacks, and retrieving the iframe URL for payment processing.

## Table of Contents
1. [Requirements](#requirements)
2. [Installation](#installation)
3. [Environment Variables](#environment-variables)
4. [Usage](#usage)
   - [Starting the Server](#starting-the-server)
   - [API Endpoints](#api-endpoints)
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

##installing dependencies

python -m venv env
source env/bin/activate  # On Windows: `env\Scripts\activate`
pip install -r requirements.txt

##Configure your .env file

python manage.py migrate

 ## add the following variables to your .env file
 
 DJANGO_SECRET_KEY=your_secret_key
PESAPAL_CONSUMER_KEY=your_consumer_key
PESAPAL_CONSUMER_SECRET=your_consumer_secret
PESAPAL_CALLBACK_URL=https://yourdomain.com/response-page

##Run the server

python manage.py runserver

```markdown
## Authentication with Pesapal APIs

The following steps are automated in the `PesapalAPI` utility:

1. **Obtain an authentication token**:
   - The API fetches the token using the Consumer Key and Consumer Secret specified in the `.env` file.

2. **Register an IPN (Instant Payment Notification)**:
   - An IPN is registered during payment initialization. The returned IPN ID is used to track notifications.

---

## Retrieving the Pesapal Iframe URL

1. Make a `POST` request to the `/api/initiate-payment/` endpoint.
2. The API response includes:
   - `order_tracking_id`: A unique identifier for the payment.
   - `redirect_url`: The iframe URL for the payment process.
3. Use the `redirect_url` in your frontend to embed the payment interface.
```





