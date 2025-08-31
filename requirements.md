# Technical and Functional Requirements – Airbnb Clone Backend

## Objective
Document the technical and functional requirements for each feature.

## Features Covered
1. User Authentication  
2. Property Management  
3. Booking System  

---

## 1. User Authentication

### Functional Requirements
- Users must be able to **register** with their first name, last name, email, and password.  
- Users must be able to **log in** using their email and password.  
- Passwords must be securely stored using **hashing (bcrypt/argon2)**.  
- The system should provide **JWT tokens** for authenticated sessions.  

### API Endpoints
- `POST /api/auth/register`  
  - Input: `{ first_name, last_name, email, password }`  
  - Output: `{ message: "User registered successfully", user_id, token }`  

- `POST /api/auth/login`  
  - Input: `{ email, password }`  
  - Output: `{ message: "Login successful", token, role }`  

### Validation Rules
- Email must be unique.  
- Password must be at least 8 characters, include letters and numbers.  
- All required fields must be provided.  

### Performance Criteria
- Authentication requests should complete within **200ms** under normal load.  
- System must handle at least **500 concurrent login requests** without degradation.  

---

## 2. Property Management

### Functional Requirements
- Hosts can **create, update, and delete** their property listings.  
- Each property must include name, description, location, and price per night.  
- Guests can **view property details** and search by filters (location, price).  

### API Endpoints
- `POST /api/properties` (Host only)  
  - Input: `{ name, description, location, price_per_night }`  
  - Output: `{ message: "Property created", property_id }`  

- `PUT /api/properties/:id` (Host only)  
  - Input: `{ name?, description?, location?, price_per_night? }`  
  - Output: `{ message: "Property updated" }`  

- `GET /api/properties/:id`  
  - Output: `{ property_id, name, description, location, price_per_night, host }`  

- `GET /api/properties?location=city&price_min=50&price_max=200`  
  - Output: `[ { property_id, name, location, price_per_night }, ... ]`  

### Validation Rules
- Price per night must be a positive number.  
- Location cannot be empty.  
- Hosts can only edit or delete their own properties.  

### Performance Criteria
- Property queries with filters must return results in **<500ms**.  
- Database must support indexing on `location` and `price_per_night`.  

---

## 3. Booking System

### Functional Requirements
- Guests can **book a property** by selecting start and end dates.  
- Bookings must check for **availability** before confirmation.  
- Each booking should calculate **total price** automatically.  
- Guests can **cancel bookings** before start date.  

### API Endpoints
- `POST /api/bookings`  
  - Input: `{ property_id, user_id, start_date, end_date }`  
  - Output: `{ message: "Booking confirmed", booking_id, total_price, status }`  

- `GET /api/bookings/:id`  
  - Output: `{ booking_id, property, guest, start_date, end_date, total_price, status }`  

- `DELETE /api/bookings/:id` (Guest only)  
  - Output: `{ message: "Booking canceled" }`  

### Validation Rules
- Booking dates must not overlap with existing bookings for the same property.  
- Start date must be today or later; end date must be after start date.  
- Only the guest who booked can cancel their booking.  

### Performance Criteria
- Availability checks must respond in **<300ms**.  
- System should handle **1,000 concurrent booking requests** with minimal conflict errors.  

---

## Notes
- Future extensions: Payments, messaging system, and reviews.  
- All APIs follow **REST principles** and return **JSON** responses.  

