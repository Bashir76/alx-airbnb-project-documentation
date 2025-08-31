# alx-airbnb-project-documentation
Documentation for the Airbnb database project

# Airbnb Clone Backend Documentation

## 1. Backend Features (Architecture Diagram)
This project includes a **Draw.io diagram** that maps the required backend features for the Airbnb Clone.

### Features Covered
- **User Authentication & Authorization**  
  - Signup, login, password hashing  
  - Role-based access (guest, host, admin)  

- **Property Management**  
  - Create, update, delete properties (hosts)  
  - Property search (location, price, availability)  

- **Booking System**  
  - Request booking  
  - Manage availability & booking status (pending, confirmed, canceled)  

- **Payments**  
  - Payment integration (Credit Card, PayPal, Stripe)  
  - Link payments to bookings  

- **Reviews & Ratings**  
  - Guests can review properties after stay  
  - Ratings (1–5) with comments  

- **Messaging System**  
  - User-to-user communication (guest ↔ host)  

📂 File: `airbnb_backend_features.drawio`  
Open it with **Draw.io / diagrams.net** to explore the system design.

---

## 2. Property Booking Workflow (Flowchart)
This is a **flowchart** showing how property booking works in the system.

### Booking Flow
1. User logs in / registers  
2. User searches for properties  
3. User selects property & dates  
4. Booking request created (status = pending)  
5. Payment processed (success → confirmed, failure → canceled)  
6. Confirmation sent to guest & host  
7. After stay, guest can leave a review  

📂 File: `booking_workflow.drawio`  
Open it with **Draw.io / diagrams.net** to view the process flow.

---

## How to Use
1. Download `.drawio` files from the project.  
2. Open them on [diagrams.net](https://app.diagrams.net/).  
3. Edit or expand as needed for development.  

---
