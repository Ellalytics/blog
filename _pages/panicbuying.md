---
layout: single
title: "PanicBuying System"
permalink: /portfolio/panicbuying/
author_profile: true
---

---

## Overview
The architecture and core modules of an e-commerce system are crucial for its efficiency and scalability, especially when handling Panicbuying. The system design uses a classic three-layer architecture and explores its key components and processes, with a focus on handling Panicbuying.

---
## Core Modules
###  Controller Layer
Handles requests and forwards them to the service layer. 
- **ItemController:** Product-related actions
- **OrderController:** Order management
- **UserController:** User authentication and management

###  Service Layer
Contains business logic to process requests.
- **ItemService:** Product creation, inventory management
- **OrderService:**Order validation, stock deduction, order creation
- **UserService:**User registration, login, and info management
- **PromoService:** Flash sale/Panic buying logic and price handling

###  DAO Layer
Responsible for data operations.
- **ItemDOMapper:** Product-related data
- **OrderDOMapper:** Order data
- **UserDOMapper:** User data
- **PromoDOMapper:** Flash sale data

### Core Business Models
**UserModel**, **ItemModel**, **PromoModel**, **OrderModel**, encapsulate business data and are mapped to the database.

### Data Transfer Objects (VO)
**UserVO**, **ItemVO**, **OrderVO** are used for efficient data transfer to the frontend.

### Core Business Flows
User places an order through OrderController, which verifies the user and product availability, deducts stock, and generates the order.PromoService checks for ongoing activities, applying flash sale prices during order placement.


---
##  Architecture
- **Frontend:** Implements frontend-backend separation for better scalability and maintainability.
- **Backend:** Built with Java and Spring Framework to handle core business logic and API services. 
- **Database:** Uses MySQL for persistent storage and Redis to support high-concurrency scenarios.
- **Inventory Control:**  Implement row locking and Redis pre-deduct for accurate inventory management.
- **Asynchronous Processing:**  Offload time-consuming tasks using message queues.
- **Caching:**  Employs Redis for fast access to frequently requested data, reducing database load and latency.

---

