# Flask Dropshipping Website

A small-scale dropshipping website built with Flask, designed to validate an end-to-end e-commerce workflow using free-tier services before focusing on scaling.

---

## Overview

This project implements a complete dropshipping pipeline, including product display, secure payments, order storage, supplier fulfillment, and customer communication.

The primary goal is **functional correctness and automation**, not high traffic or large-scale optimization.
All architectural decisions intentionally favor simplicity, low cost, and clarity.

The system is designed so that:

- Customers can browse products and place orders securely
- Payments are handled by a third-party processor
- Orders are automatically forwarded to a fulfillment provider
- Tracking and order status are stored and communicated back to the customer
- Manual intervention is minimized but still possible where brand experience matters

---

## High-Level Architecture

**Frontend**

- Flask-rendered HTML templates
- Product pages, checkout initiation, and contact form
- Static assets (CSS, JS, images) served via Flask

**Backend**

- Flask application hosted on HelioHost
- Handles routing, order logic, email sending, and API integrations

**Database**

- SQLite for lightweight persistence
- Stores products, orders, payment status, and tracking data

**External Services**

- Square (payments and disputes)
- CJ Dropshipping (product fulfillment)
- Gmail SMTP (customer communication)
- Let’s Encrypt (HTTPS / SSL)

---

## Tech Stack

- **Backend:** Flask (Python)
- **Database:** SQLite
- **Hosting:** HelioHost (free tier)
- **Payments:** Square
- **Fulfillment:** CJ Dropshipping
- **Email:** Gmail SMTP
- **Security:** Let’s Encrypt SSL
- **Frontend:** HTML, CSS (Bootstrap), JavaScript

---

## Core Workflow

### Checkout & Fulfillment Flow

1. User arrives at the site via marketing or organic traffic
2. Customer views a product on the Flask site
3. Customer completes payment via Square checkout
4. Square confirms payment
5. Order is stored in SQLite
6. Square emails the customer a receipt
7. Backend sends order data to CJ Dropshipping via API
8. CJ Dropshipping:
   - Checks inventory in real time
   - Creates the fulfillment order
   - Ships the product
9. Tracking number is returned and stored
10. Customer is emailed tracking details automatically

---

## Customer Support & Issues

### Payment Issues

- Refunds and chargebacks are handled by Square

### Product Issues

- Customers contact the store via email or contact form
- Initial communication is handled manually to preserve brand experience
- Backend communicates with CJ Dropshipping to request:
  - Replacement
  - Refund
  - Return
- Order status updates are synced and emailed to the customer

---

## Inventory Handling

- CJ Dropshipping inventory can be checked programmatically
- Products can be automatically disabled when out of stock
- No daily manual inventory checks required

---

## Running Locally

> Local development setup is intentionally minimal.

1. Clone the repository
2. Create a Python virtual environment
3. Install dependencies
4. Run the Flask app

```bash
python app.py
```
