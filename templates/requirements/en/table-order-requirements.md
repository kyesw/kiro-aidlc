# Table Order Service Requirements

> 🗑️ **Note**: Lines marked with `🗑️` should be deleted after you finish writing. Removing guide text before passing to the AI will produce more accurate results.

## 1. Project Overview

### 1.1 Service Vision
A table-order platform that provides customers with a convenient ordering experience and restaurant operators with an efficient management environment through a digital ordering system.

### 1.2 Core Value Proposition

**Customer Perspective**
- Instant ordering with zero wait time
- Intuitive and easy-to-use interface

**Restaurant Operator Perspective**
- Reduced labor costs and increased operational efficiency
- Real-time order management and monitoring

**Market Differentiation**
- Flexible architecture adaptable to various business types
- Intuitive admin tools

---

## 2. Service Architecture

### 2.1 Key Components
- **Customer Interface**: Web UI for ordering at the table (runs in browser)
- **Admin Interface**: Management dashboard for restaurant operators
- **Server System**: Order processing and data management
- **Data Store**: Storage for restaurant, menu, and order data

---

## 3. Core Feature Requirements

> 🗑️ The more specific you write, the more accurately the AI will implement it. If you write something vague, the AI will ask clarifying questions — that's a great experience too!

---

### 3.1 Customer Features

> 🗑️ Think about the entire process of a customer ordering at a table.
> 🗑️ (Hints: How to display the menu? How to place an order? Shopping cart? Order confirmation? Recommendations/popular items? Multi-language?)

#### (Feature Name)
> (One-line description)
- 
- 

#### (Feature Name)
> (One-line description)
- 
- 

#### (Feature Name)
> (One-line description)
- 
- 

---

### 3.2 Admin Features

> 🗑️ Think about how a restaurant operator receives and manages orders.
> 🗑️ (Hints: How should orders be displayed? Menu registration/editing? Table management? Sold-out handling? Real-time notifications?)

#### (Feature Name)
> (One-line description)
- 
- 

#### (Feature Name)
> (One-line description)
- 
- 

#### (Feature Name)
> (One-line description)
- 
- 

---

### 3.3 Business/Marketing Features (Optional)

> 🗑️ Add features that help with revenue or customer acquisition.
> 🗑️ (Hints: Sales analytics? Popular menu analysis? Promotions/discounts? Time-based recommendations?)

#### (Feature Name)
> (One-line description)
- 
- 

---

> 🗑️ **Example** — For reference only. Format is flexible.
>
> 🗑️ ```
> 🗑️ #### Shopping Cart
> 🗑️ > Customers can add multiple items and place a single order
> 🗑️ - Shows quantity and price when items are added
> 🗑️ - Quantity can be increased or decreased
> 🗑️ - Total is calculated in real-time
> 🗑️ - Cart persists after page refresh
> 🗑️ ```

---

## Appendix: Glossary

| Term | Simple Explanation |
|------|-------------------|
| API | How the server and the screen exchange data |
| Real-time | Screen updates automatically without refreshing |
| Session | The time period from when a customer sits down until they leave |
| Auth | The process of verifying identity (login) |
| SSE | Technology that lets the server push data to the screen automatically |
