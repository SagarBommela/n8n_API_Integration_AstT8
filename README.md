# Topic 8 – Integrating Multiple APIs Together

## Overview

This project demonstrates how to integrate multiple APIs using n8n. The workflow creates a support ticket, generates a transaction ID, identifies the customer, logs ticket details, and prepares a confirmation notification.

## Objectives

- Create support ticket information.
- Generate a unique transaction ID.
- Map customer email to customer ID.
- Log ticket details using an HTTP POST request.
- Send a confirmation notification using data from previous nodes.
- Understand how to use ancestor node expressions in n8n.

## Tools Used

- n8n
- Postman
- JSONPlaceholder API
- Postman Echo API

## Workflow Implementation

### 1. Incoming Support Ticket

**Node:** Incoming Support Ticket

Created sample support ticket details using an Edit Fields node.

- Ticket ID: TCK-8855
- Customer Email: alice@example.com
- Issue: Password reset button is not working.

### 2. Initialize Transaction

**Node:** Initialize Transaction

Generated a transaction ID using an n8n expression.

Also passed the ticket ID, customer email, and issue description to the next node.

### 3. Customer Database Lookup

**Node:** Customer Database Lookup

Used a conditional expression to map the customer email to a customer ID.

- alice@example.com → CUST-7744
- Other emails → CUST-9999

### 4. Log to Database

**Node:** Log to Database

- Method: POST
- API: `https://jsonplaceholder.typicode.com/posts`

Sent the transaction ID, customer ID, ticket ID, issue details, and status to the mock database API.

Also passed the transaction ID using the X-Correlation-ID header.

### 5. Send Notification Alert

**Node:** Send Notification Alert

- Method: POST
- API: `https://postman-echo.com/post`

Created a confirmation notification payload using customer email, ticket ID, and transaction ID from the previous workflow nodes.


Loom video:

https://www.loom.com/share/8b5853b78d0c4d3fad10204c06f5e5d6

 GIT Url:

https://github.com/SagarBommela/n8n_API_Integration_AstT8

