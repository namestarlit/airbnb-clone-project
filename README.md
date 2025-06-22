# Airbnb Clone Project

## Overview of the AirBnB Clone

### Objective

The backend for the Airbnb Clone project is designed to provide a robust and scalable foundation for managing user interactions,
property listings, bookings, and payments. This backend will support various functionalities required to mimic the core features
of Airbnb, ensuring a smooth experience for users and hosts.

### Project Goals

1. **User Management**: Implement a secure system for user registration, authentication, and profile management.  
2. **Property Management**: Develop features for property listing creation, updates, and retrieval.  
3. **Booking System**: Create a booking mechanism for users to reserve properties and manage booking details.  
4. **Payment Processing**: Integrate a payment system to handle transactions and record payment details.  
5. **Review System**: Allow users to leave reviews and ratings for properties.  
6. **Data Optimization**: Ensure efficient data retrieval and storage through database optimizations.  


## Team Roles

- **Backend Developer**: Responsible for implementing API endpoints, database schemas, and business logic.  
- **Database Administrator**: Manages database design, indexing, and optimizations.  
- **DevOps Engineer**: Handles deployment, monitoring, and scaling of the backend services.  
- **QA Engineer**: Ensures the backend functionalities are thoroughly tested and meet quality standards.  


## Technology Stack

- **Django**: A high-level Python web framework used for building the RESTful API.  
- **Django REST Framework**: Provides tools for creating and managing RESTful APIs.  
- **PostgreSQL**: A powerful relational database used for data storage.  
- **GraphQL**: Allows for flexible and efficient querying of data.  
- **Celery**: For handling asynchronous tasks such as sending notifications or processing payments.  
- **Redis**: Used for caching and session management.  
- **Docker**: Containerization tool for consistent development and deployment environments.  
- **CI/CD Pipelines**: Automated pipelines for testing and deploying code changes.


## Database Design

This section outlines the core entities and relationships that structure the Airbnb Clone backend.

### Key Entities and Their Fields

#### 1. **User**

Represents both guests and hosts.

| Field           | Description                         |
| --------------- | ----------------------------------- |
| `id`            | Unique identifier for each user     |
| `name`          | Full name of the user               |
| `email`         | Unique email address                |
| `password_hash` | Securely stored password hash       |
| `is_host`       | Boolean indicating if user can host |

**Relationships**:

* A user can own multiple properties.
* A user can book multiple properties.
* A user can leave multiple reviews.
* A user can make multiple payments.

#### 2. **Property**

Represents a place listed by a host.

| Field         | Description                            |
| ------------- | -------------------------------------- |
| `id`          | Unique identifier for the property     |
| `title`       | Name or title of the property          |
| `description` | Detailed description of the property   |
| `location`    | City, state, or address                |
| `price`       | Price per night                        |
| `host_id`     | Foreign key linking to the owning user |

**Relationships**:

* A property is owned by one user (host).
* A property can have multiple bookings.
* A property can have multiple reviews.

#### 3. **Booking**

Represents a reservation made by a guest.

| Field         | Description                                 |
| ------------- | ------------------------------------------- |
| `id`          | Unique identifier for the booking           |
| `user_id`     | Foreign key to the guest making the booking |
| `property_id` | Foreign key to the booked property          |
| `start_date`  | Start date of the booking                   |
| `end_date`    | End date of the booking                     |
| `status`      | Status (e.g., pending, confirmed, canceled) |

**Relationships**:

* A booking is made by one user (guest).
* A booking is for one property.

#### 4. **Review**

Represents user feedback on a property.

| Field         | Description                          |
| ------------- | ------------------------------------ |
| `id`          | Unique identifier for the review     |
| `user_id`     | Foreign key to the reviewer          |
| `property_id` | Foreign key to the reviewed property |
| `rating`      | Numeric rating (e.g., 1 to 5)        |
| `comment`     | Text feedback provided by the user   |

**Relationships**:

* A review is written by one user for one property.

#### 5. **Payment**

Represents a transaction made for a booking.

| Field        | Description                                  |
| ------------ | -------------------------------------------- |
| `id`         | Unique identifier for the payment            |
| `user_id`    | Foreign key to the user who made the payment |
| `booking_id` | Foreign key to the associated booking        |
| `amount`     | Total amount paid                            |
| `status`     | Payment status (e.g., completed, failed)     |

**Relationships**:

* A payment is made by one user.
* A payment is linked to one booking.

### Entity Relationship Summary

* A **User** can own many **Properties**.
* A **User** can make many **Bookings**.
* A **Property** can have many **Bookings** and many **Reviews**.
* A **User** can write many **Reviews**.
* A **Booking** is associated with one **Property**, one **User**, and one **Payment**.
* A **Payment** is linked to a single **Booking** and made by one **User**.


## Feature Breakdown

This section outlines the core features implemented in the Airbnb Clone project, each designed to replicate a functional 
and seamless rental platform experience for both hosts and guests.

#### 1. **User Management**

Handles user registration, login, authentication, and profile updates. It ensures secure access control and allows users to 
operate as guests or hosts depending on their account settings.

#### 2. **Property Management**

Enables hosts to create, update, and delete property listings. Each property includes essential details such as title, description, 
location, price, and availability, forming the backbone of the platform's rental inventory.

#### 3. **Booking System**

Allows guests to book available properties for specific dates. It manages availability checks, booking statuses 
(pending, confirmed, canceled), and prevents overlapping reservations to maintain booking integrity.

#### 4. **Payment Processing**

Facilitates secure transactions between guests and the platform. This feature ensures that bookings are only confirmed once payments 
are successfully completed, maintaining financial accountability.

#### 5. **Review System**

Lets guests provide feedback on properties they’ve stayed at. Reviews include ratings and comments, helping future guests make 
informed decisions and encouraging hosts to maintain high standards.

#### 6. **Data Optimization**

Implements database indexing, query optimization, and caching strategies to improve performance and scalability. This ensures fast 
data retrieval even as the system scales with more users, properties, and bookings.

