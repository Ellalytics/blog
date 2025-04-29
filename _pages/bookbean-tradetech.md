---
layout: single
title:  "BookBean TradeTech"
permalink: /portfolio/bookBean-tradetech/
author_profile: true
---

## **System Overview**
- Retrieve book details via **Google Books API** using ISBN or title
- Mark books for donation or wishlist via selection buttons
- Initiate trades via Email and notification system
- Earn **book beans** (points) through book uploads and successful trades
- Discover new books through **personalized recommendations**
- Follow users, bookmark books, and leave **ratings and reviews**
<img src="/blog/assets/images/bookbean.png" alt="bookbean_my_donations">

---

## **Tech Stack**
- **Frontend:** Google Books API, HTML/CSS/JavaScript
- **Backend:** Flask-based RESTful APIs, SQLAlchemy
- **Database:** Sharded MySQL, application-level transaction management
- **Caching:** Redis for storing frequently accessed data 
- **Deploy:** AWS, Nginx and Gunicorn to enhance concurrency and scalability
- **Security:** Access, parameter validation, authentication, points validation


## **Core Features**

### **1. Book Retrieved with Google Books API**
Instead of manually entering book details, users can:
- Search by **ISBN** or book title
- Automatically retrieve book information using the **Google Books API**
- Select the **"donate"** checkbox if they wish to offer the book for free

I built a Book class that encapsulates related operations.
- Encapsulation: Centralizes book search logic for better organization
- Extensibility: Add features (pagination, sorting) without major changes
- OOP Design: Facilitates maintainability and code reuse
- Data Abstraction: Simplifies access to search results via properties like first
- Separation of Concerns: Abstracts API request handling from the core logic

```python
class Book:
    def __init__(self):
        self.total = 0
        self.books = []

    def search_by_keyword(self, q, page=1):
        per_page = current_app.config['PER_PAGE']
        start = self.calculate_start(page, per_page)
        url = self.keyword_url.format(q)
        result = HTTP.get(url)
        self.__fill_collection(result)

    def search_by_isbn(self, q):
        url = self.isbn_url.format(q)
        result = HTTP.get(url, return_json=True)
        self.__fill_single(result)

    def __fill_single(self, data):
        if data and data['items']:
            self.total = 1
            self.books.append(data['items'][0])

    def __fill_collection(self, data):
        self.total = data['totalItems']
        self.books = data['items']

    def calculate_start(self, page, per_page):
        start = (page - 1) * per_page
        return start

    @property
    def first(self):
        return self.books[0] if self.total >= 1 else None

```

---

###  **2. Asynchronous Email System for Book Trading**

- **Flask-Mail + SMTP** 
- **Thread-based Asynchronous Processing** 
- **HTML & Plain-Text Templates** 

---

###  **3. Book Beans & Transactions**
- **Book Beans Rewards:** 
    - Donating a book: `+5` beans; Completing a trade: `+30` beans  
- **Book Beans Deductions:**
    - Initiating a trade request: `-30` beans (to prevent spamming)
- **Book Beans Deductions:**
    - Valid review submitted: `+5` beans  

<a href="/blog/E-commerce/BookBean-Points/" class="btn btn--primary">Learn more</a>


---

###  **4. Book Recommendation**
- Based on previous trades, search history, and saved books.
- Use Collaborative Filtering to recommend books liked by similar users.

<a href="/blog/E-commerce/BookBean-Points/" class="btn btn--primary">Learn more</a>

---

###  **5. Book Reviews & Ratings**
- **Star Ratings:** Users can rate books from 1 to 5 stars.

- **Text Reviews:** Users can write detailed reviews about their experience.

- **Review Moderation:** Basic NLP checks to ensure quality.
