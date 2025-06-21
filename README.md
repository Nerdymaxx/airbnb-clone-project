# airbnb-clone-project
a clone of airbnb 

this is a clone of the airbnb application built to learn and implement system design architecture.

the tech stack is 

backend-python-django
database-mysql and postgres

version control - git and github

Team Roles:

### 🔧 Backend Developer
Responsible for building the server-side logic, RESTful APIs, and business logic. Ensures smooth data flow between the frontend and the database, handles authentication, and implements core functionalities like bookings and user sessions.

### 🎨 Frontend Developer
Designs and implements the user interface using modern JavaScript frameworks (e.g., React). Ensures the platform is responsive, interactive, and aligned with the UX/UI design goals.

### 🗄️ Database Administrator (DBA)
Designs and manages the project’s database schema. Optimizes queries, ensures data integrity, and handles backups, migrations, and security of stored data.

### 🧪 QA Engineer (Quality Assurance)
Writes and executes test cases to ensure the app works as expected. Identifies bugs, works with developers to fix issues, and ensures the platform meets performance and usability standards.

### 📐 UI/UX Designer
Creates wireframes, mockups, and user flow diagrams. Ensures the application is intuitive, user-friendly, and visually consistent across devices.

### 📁 DevOps Engineer
Handles infrastructure setup, CI/CD pipelines, deployment automation, and monitors application performance in staging or production environments.

### 👥 Project Manager
Coordinates the team, tracks progress, sets deadlines, and ensures that everyone is aligned with the project goals and milestones.

### Database Design

Users- These are people who use the platform.

**Key Fields:**
- `id` (Primary Key)
- `full_name`
- `email`
- `password_hash`
- `role` (e.g., "host" or "guest")
**Relationships:**
- A user can list **multiple properties**.
- A user can make **multiple bookings**.
- A user can write **multiple reviews**.
  
### 🏠 Properties
Represents the spaces available for rent.

**Key Fields:**
- `id` (Primary Key)
- `owner_id` (Foreign Key → Users)
- `title`
- `description`
- `location`
- `price_per_night`

**Relationships:**
- Each property is **owned by a user** (host).
- A property can have **multiple bookings**.
- A property can receive **multiple reviews**.

---

### 📅 Bookings
Represents reservations made by users for specific properties.

**Key Fields:**
- `id` (Primary Key)
- `user_id` (Foreign Key → Users)
- `property_id` (Foreign Key → Properties)
- `check_in_date`
- `check_out_date`
- `total_price`

**Relationships:**
- A booking is made by a **user**.
- A booking is for a **specific property**.

---

### ✍️ Reviews
Represents feedback given by users after staying at a property.

**Key Fields:**
- `id` (Primary Key)
- `user_id` (Foreign Key → Users)
- `property_id` (Foreign Key → Properties)
- `rating` (e.g., 1 to 5)
- `comment`
- `created_at`

**Relationships:**
- A review is written by a **user**.
- A review is associated with a **property**.

---

### 💳 Payments
Tracks payment transactions for bookings.

**Key Fields:**
- `id` (Primary Key)
- `booking_id` (Foreign Key → Bookings)
- `amount`
- `payment_method`
- `status` (e.g., "paid", "pending", "failed")

**Relationships:**
- A payment is linked to a **booking**.

---
## 🚀 Feature Breakdown

This section highlights the core features of the AirBnB Clone project and their roles in delivering a full-stack rental platform experience.

### 👤 User Management
Users can sign up, log in, and manage their profiles. Authentication ensures secure access, while user roles (guest or host) determine available actions within the app.

### 🏠 Property Management
Hosts can list new properties by providing images, descriptions, pricing, and availability. They can also update or delete their listings, ensuring full control over their rental spaces.

### 📅 Booking System
Guests can browse available properties, select check-in/check-out dates, and make bookings. The system prevents double bookings and calculates the total cost based on stay duration.

### 💬 Reviews and Ratings
After a stay, guests can leave feedback and ratings for properties. This helps maintain quality standards and guides other users in choosing the best options.

### 💳 Payment Integration
Secure payment handling allows users to complete transactions during booking. This includes support for different payment methods and transaction status tracking.

### 🔍 Search and Filtering
Users can search for properties by location, date, price, and amenities. This enhances the user experience by helping guests find listings that meet their preferences.

### 🧾 Admin Dashboard (Optional)
An optional admin interface provides insights into platform usage, allowing moderators to manage listings, users, and resolve disputes if needed.

## 🔐 API Security

Security is a core pillar of this project to protect sensitive user data, financial transactions, and ensure the integrity of the platform. Below are key measures implemented to secure the backend APIs.

### ✅ Authentication
All endpoints are secured using token-based authentication (e.g., JWT). This ensures that only registered and verified users can access protected resources like booking and property management features.

**Why it matters**: Prevents unauthorized access to user accounts and private data such as email, booking history, and personal preferences.

---

### 🔓 Authorization
Role-based access control (RBAC) is enforced. For example, only users with the “host” role can create or manage property listings, while only “guests” can make bookings.

**Why it matters**: Ensures users can only perform actions that match their assigned roles, reducing the risk of privilege escalation.

---

### 🚫 Rate Limiting
Rate limiting is used to control how many requests a user or IP address can make in a given time period. This helps prevent abuse and brute-force attacks.

**Why it matters**: Protects the platform from denial-of-service (DoS) attacks and prevents malicious bots from overloading the system.

---

### 🔒 Data Encryption
Sensitive data such as passwords are hashed using algorithms like bcrypt before being stored. HTTPS is enforced for all API communication.

**Why it matters**: Protects user credentials and ensures data in transit is not intercepted or tampered with.

---

### 🛡️ Input Validation & Sanitization
All user inputs are validated and sanitized to prevent injection attacks such as SQL injection or cross-site scripting (XSS).

**Why it matters**: Prevents attackers from exploiting untrusted inputs to gain unauthorized control over the application.

---

### 💳 Secure Payment Handling
Integration with trusted third-party payment gateways ensures secure transaction processing. No sensitive card data is stored directly on the platform.

**Why it matters**: Protects users' financial information and builds trust in the platform’s reliability.
## ⚙️ CI/CD Pipeline

Continuous Integration (CI) and Continuous Deployment (CD) pipelines automate the building, testing, and deployment of applications. This ensures that new changes to the codebase are automatically tested and deployed without manual intervention, reducing errors and speeding up delivery.

### Why CI/CD Matters for This Project
- **Reliability**: Ensures that each new feature or bug fix does not break existing functionality.
- **Speed**: Accelerates development by reducing manual tasks such as testing and deployment.
- **Consistency**: Provides a repeatable process for deploying code to staging and production environments.
- **Feedback**: Offers quick feedback through automated tests and build logs, allowing for faster debugging and improvements.

### Tools to Be Used
- **GitHub Actions**: For automating test runs, linting, and deployment workflows directly from the GitHub repository.
- **Docker**: For containerizing the application to ensure consistent behavior across environments.
- **Heroku / Render / AWS / Netlify**: For hosting and deployment depending on the frontend/backend components.
- **Postman/Newman**: For automated API testing during CI processes.

