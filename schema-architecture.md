## Section 1: Architecture Summary
The Smart Clinic Management System is built on a **three-tier architecture**: **Presentation Layer**, **Application Layer**, and **Data Layer**. The system supports both **Thymeleaf-based dashboards** (for Admin and Doctor) and **RESTful modules** (for Patients and Appointments). Requests from the frontend flow through **Spring Boot controllers** — Thymeleaf Controllers for HTML dashboards and REST Controllers for JSON APIs. Both controller types delegate logic to a centralized **Service Layer**, which coordinates data access across **two databases**:  
- **MySQL** (via JPA entities and repositories) for structured relational data such as Patients, Doctors, Appointments, and Admin.  
- **MongoDB** (via documents and repositories) for flexible, document-oriented data like Prescriptions.  

This hybrid design enables scalability, data flexibility, and support for multiple types of clients.

---

## Section 2: Numbered Flow (Request → Response)

### A. Dashboard (Thymeleaf + MySQL)
1. **User action:** Admin or Doctor requests a dashboard page (e.g., `/adminDashboard`, `/doctorDashboard`).  
2. **Thymeleaf Controller:** The request is routed to a **Thymeleaf controller** in the Spring Boot app.  
3. **Service Layer:** The controller calls the **Service Layer** for business logic.  
4. **MySQL Repository:** The service queries a **MySQL repository**.  
5. **MySQL Database:** The repository fetches **JPA entities** (`Patient`, `Doctor`, `Appointment`, `Admin`) from the relational database.  
6. **Data return:** Entities are returned to the service layer.  
7. **Rendering:** The controller passes the data into a **Thymeleaf template**, which is rendered as HTML and sent back to the browser.  

---

### B. REST API (JSON + MongoDB/MySQL)
1. **User action:** Patient or external client sends a REST request (e.g., `POST /api/v1/appointments` or `GET /api/v1/prescriptions`).  
2. **REST Controller:** Spring Boot routes the request to the appropriate **REST controller**.  
3. **Service Layer:** The controller calls the **Service Layer**, which applies validations and rules.  
4. **Dual data access:**  
   - For relational data (Appointments, Patients, Doctors, Admin), the service calls **MySQL repositories**, which fetch from the MySQL database.  
   - For document data (Prescriptions), the service calls **MongoDB repositories**, which fetch from the MongoDB database.  
5. **Data processing:** The service composes responses, combining data from MySQL entities and MongoDB documents if needed.  
6. **Response:** The REST controller serializes the result into **JSON** and sends it back to the client.  

---

✅ This document mirrors the reference diagram:  
- Dashboards → Thymeleaf Controllers → Service → MySQL  
- REST Modules → REST Controllers → Service → MySQL + MongoDB  

