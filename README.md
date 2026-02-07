# MedMarket – Online Pharmacy Backend API

This repository contains the **backend API** of **MedMarket**, a prototype of a digital pharmacy built during a full-stack development internship in the IT division of the Ministry of Health. :contentReference[oaicite:0]{index=0}  

The goal of the project was to design a secure, maintainable backend to support:

- online ordering of pharmaceutical products,
- stock and order management,
- user accounts and roles (customer / administrator),
- integration with a modern front-end built in React.

---

## 🎯 Project Goals

Based on the internship project description, the main objectives were: :contentReference[oaicite:1]{index=1}  

- **Modernise the pharmaceutical supply chain** with an e-commerce platform.
- **Improve accessibility** of medicines for professionals and the public.
- **Guarantee security and regulatory compliance** of online transactions.
- **Automate operational processes** such as stock, orders and payments.
- Provide **full traceability** of products from order to delivery.
- Offer a backend that is **scalable and maintainable** over time.

---

## 👨‍💻 What I Implemented

During this internship I designed and implemented the backend from scratch:

- Initialised the **Node.js / Express** project and package configuration. :contentReference[oaicite:2]{index=2}  
- Designed the **conceptual and logical data models** (users, products, orders, payments, etc.). :contentReference[oaicite:3]{index=3}  
- Built the **MongoDB data layer** with Mongoose models for:
  - users, cities, categories,
  - products and product images,
  - carts and cart items,
  - orders and order items,
  - payments, reviews and favourites. :contentReference[oaicite:4]{index=4}  
- Implemented **RESTful controllers and routes** for all business features:
  - user & auth management,
  - product catalogue,
  - cart / favourites,
  - orders & payments. :contentReference[oaicite:5]{index=5}  
- Added **authentication & authorisation**:
  - JWT-based authentication,
  - role-based access control (admin vs user),
  - ownership checks (a user can only modify their own resources). :contentReference[oaicite:6]{index=6}  
- Created **validation middlewares** using **Joi** to validate request payloads and protect the API from invalid data. :contentReference[oaicite:7]{index=7}  
- Implemented a **centralised error handler middleware** for consistent error responses. :contentReference[oaicite:8]{index=8}  
- Added **data sanitisation** and **CORS** configuration to strengthen security and allow communication with the front-end. :contentReference[oaicite:9]{index=9}  
- Developed **seed scripts** with Faker.js to generate realistic test data (products, cities, etc.). :contentReference[oaicite:10]{index=10}  
- Tested the API endpoints with **Postman**, iterating on the design and fixing issues as the project evolved. :contentReference[oaicite:11]{index=11}  

A separate **React front-end** was developed to consume this API (product catalogue, cart, checkout, etc.), which showcases the full-stack aspect of the internship.

---

## 🧰 Tech Stack

Backend & data:

- **Node.js**, **Express.js** – REST API and HTTP handling :contentReference[oaicite:12]{index=12}  
- **MongoDB**, **Mongoose** – document database and schema modelling :contentReference[oaicite:13]{index=13}  
- **JSON Web Tokens (JWT)** – stateless authentication :contentReference[oaicite:14]{index=14}  
- **Joi** – request validation :contentReference[oaicite:15]{index=15}  
- **Faker.js** – database seeding with realistic fake data :contentReference[oaicite:16]{index=16}  

Tooling & quality:

- **Postman** – API testing :contentReference[oaicite:17]{index=17}  
- **Git / GitHub** – version control and collaboration :contentReference[oaicite:18]{index=18}  

Front-end (developed during the internship, in a separate repository):

- **React** – responsive UI for the pharmacy storefront.
- **CSS / component libraries** – for layout and design.

---

## 📂 Project Structure

Current structure of this backend:

```text
MedMarket/
├── LICENSE
├── README.md
├── index.js                 # Application entry point
│
├── config/
│   └── database.js          # MongoDB connection & configuration
│
├── controllers/             # Business logic for each resource
│   ├── auth-controller.js
│   ├── cart-controller.js
│   ├── cart-item-controller.js
│   ├── category-controller.js
│   ├── city-controller.js
│   ├── favorite-controller.js
│   ├── order-controller.js
│   ├── order-item-controller.js
│   ├── payment-controller.js
│   ├── product-controller.js
│   ├── review-controller.js
│   └── user-controller.js
│
├── middlewares/
│   ├── auth.js              # JWT auth & authorisation
│   ├── error-handler.js     # Centralised error handling
│   └── validators/          # Joi validation schemas
│       ├── auth-validator.js
│       ├── cart-item-validator.js
│       ├── cart-validator.js
│       ├── category-validator.js
│       ├── city-validator.js
│       ├── favorite-validator.js
│       ├── id-validator.js
│       ├── order-item-validator.js
│       ├── order-validator.js
│       ├── payment-validator.js
│       ├── product-validator.js
│       ├── review-validator.js
│       └── user-validator.js
│
├── models/                  # Mongoose schemas
│   ├── cart-item-model.js
│   ├── cart-model.js
│   ├── category-model.js
│   ├── city-model.js
│   ├── favorite-model.js
│   ├── order-item-model.js
│   ├── order-model.js
│   ├── payment-model.js
│   ├── product-model.js
│   ├── review-model.js
│   └── user-model.js
│
├── routes/                  # Route definitions mapping HTTP → controllers
│   ├── auth-router.js
│   ├── cart-item-router.js
│   ├── cart-router.js
│   ├── category-router.js
│   ├── city-router.js
│   ├── favorite-route.js
│   ├── order-item-router.js
│   ├── order-router.js
│   ├── payment-router.js
│   ├── product-router.js
│   ├── review-router.js
│   └── user-router.js
│
├── seeds/                   # Seed scripts (initial data)
│   ├── category-seeder.js
│   ├── city-seeder.js
│   └── product-seeder.js
│
└── utils/
    ├── catch-async-err.js   # Helper to wrap async controllers
    └── joi.js               # Joi configuration & helpers
````

This structure follows the layered architecture described in the internship report (config, models, controllers, routes, middlewares, utils, seeds) to keep the code modular and maintainable. 

---

## ⚙️ Getting Started

### 1. Install dependencies

```bash
npm install
```

### 2. Configure environment variables

Create a `.env` file at the root of the project with at least:

* the MongoDB connection string (used in `config/database.js`),
* the JWT secret key (used in `middlewares/auth.js`),
* any other settings required by your environment.

### 3. Run the API

```bash
node index.js
```

The server will start on the port configured in `index.js` (for example `http://localhost:3000`).

You can then use **Postman** or any HTTP client to call the routes defined in `routes/` for users, products, cart, orders, etc.

---

## 💡 What This Project Demonstrates About My Skills

This project shows that I can:

* Design a **complete data model** (MCD/MLD, UML use cases) and turn it into a working backend. 
* Build a **RESTful API** with Node.js, Express, MongoDB and Mongoose.
* Implement **authentication, authorisation and validation** in a secure way (JWT, role-based access, Joi, sanitisation). 
* Structure a project in clearly separated layers (**config / models / controllers / routes / middlewares / utils / seeds**) for maintainability. 
* Use **Git / GitHub** and tools like **Postman** and **Faker.js** to support development, testing and collaboration. 
* Collaborate with non-technical stakeholders in the health sector and translate functional needs into a concrete, working prototype.

In short, MedMarket is a **full-stack oriented backend project** that highlights my ability to design, implement and document real-world web applications in a professional environment.
