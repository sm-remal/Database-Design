# MERN + MySQL E-Commerce Database Design

## Project Overview

This project is a scalable E-Commerce backend architecture using:

- MySQL 
- MERN Stack 
- Prisma ORM 

Features included:

- Authentication & Authorization
- Product Management
- Orders & Payments
- Comments & Likes
- File Upload System
- Blog/Post System
- Admin Inventory Management

---

# Main Tables

## 1. Users Table

```sql
users
-----
id (PK)
name
email (UNIQUE)
phone
password
role ENUM('admin','customer')
avatar
is_verified
status
created_at
updated_at
```

---

## 2. Products Table

```sql
products
--------
id (PK)
category_id (FK)
name
slug
short_description
description
price
discount_price
stock
sku
thumbnail
brand
status
created_by (FK -> users.id)
created_at
updated_at
```

---

## 3. Product Images Table

```sql
product_images
--------------
id (PK)
product_id (FK)
image_url
created_at
```

---

## 4. Categories Table

```sql
categories
----------
id (PK)
name
slug
parent_id (nullable)
image
created_at
```

---

## 5. Orders Table

```sql
orders
------
id (PK)
user_id (FK)
total_amount
shipping_fee
discount
payment_status ENUM('pending','paid','failed')
order_status ENUM(
  'pending',
  'processing',
  'shipped',
  'delivered',
  'cancelled'
)
shipping_address
billing_address
transaction_id
created_at
updated_at
```

---

## 6. Order Items Table

```sql
order_items
-----------
id (PK)
order_id (FK)
product_id (FK)
quantity
price
subtotal
```

---

## 7. Payments Table

```sql
payments
--------
id (PK)
order_id (FK)
user_id (FK)
method ENUM('sslcommerz','stripe','cod')
transaction_id
amount
status
paid_at
created_at
```

---

# Authentication Tables

## 8. OTP Verification Table

```sql
otp_verifications
-----------------
id (PK)
user_id (FK)
otp
type ENUM('email','phone')
expires_at
created_at
```

---

## 9. Refresh Tokens Table

```sql
refresh_tokens
--------------
id (PK)
user_id (FK)
token
expires_at
created_at
```

---

# Social Features

## 10. Comments Table

```sql
comments
--------
id (PK)
user_id (FK)
product_id (nullable FK)
post_id (nullable FK)
comment
created_at
```

---

## 11. Likes / Wishlist Table

```sql
likes
-----
id (PK)
user_id (FK)
product_id (nullable FK)
post_id (nullable FK)
created_at
```

---

# Blog/Post System

## 12. Posts Table

```sql
posts
-----
id (PK)
user_id (FK)
title
slug
thumbnail
content
status
created_at
updated_at
```

---

# File Upload System

## 13. Uploads Table

```sql
uploads
-------
id (PK)
user_id (FK)
file_name
file_url
file_type
size
created_at
```

---

# Database Relationships

```text
User -> Orders
User -> Comments
User -> Likes
User -> Posts

Category -> Products

Product -> Product Images
Product -> Comments
Product -> Order Items

Order -> Order Items
Order -> Payment
```

---

# Recommended Tech Stack

## Backend

- Node.js
- Express.js
- Prisma ORM
- MySQL

## Frontend

- React
- Redux Toolkit / Zustand
- TanStack Query

## Authentication

- JWT Access Token
- Refresh Token
- bcrypt password hashing

## File Upload

- Cloudinary
- Multer

## Payment Gateways

### Bangladesh

- SSLCommerz
- bKash
- Nagad

---

# Recommended Folder Structure

```txt
src/
 ├── modules/
 │    ├── auth/
 │    ├── users/
 │    ├── products/
 │    ├── orders/
 │    ├── payments/
 │    ├── comments/
 │    └── posts/
 │
 ├── prisma/
 ├── middlewares/
 ├── utils/
 └── routes/
```

---

# Important Features

## Inventory Management

```sql
stock
low_stock_alert
```

---

## Soft Delete

```sql
deleted_at
```

---

## SEO Fields

```sql
meta_title
meta_description
```

---

# Recommended Extra Tables

- carts
- coupons
- shipping_methods
- notifications
- reviews
- addresses
- activity_logs

---

# Best ORM Choice

Recommended ORM for this project:

- Prisma ORM ✅
- Sequelize
- TypeORM

---

# Next Steps

You can now create:

1. ER Diagram
2. Prisma Schema
3. REST API Structure
4. Authentication Flow
5. Role Permission System
6. Admin Dashboard

---

# Author

Generated with ChatGPT for MERN + MySQL E-Commerce Architecture.
