# Database Schema Design

The Smart Clinic uses a **hybrid** approach:
- **MySQL** for structured/relational data (patients, doctors, appointments, admin).
- **MongoDB** for flexible documents (e.g., prescriptions). :contentReference[oaicite:0]{index=0}

---

## MySQL Database Design

> Keys: PK = Primary Key, FK = Foreign Key. Use `InnoDB` so FKs are enforced. :contentReference[oaicite:1]{index=1}

### Table: patients
- `patient_id`: INT, **PK**, AUTO_INCREMENT  
- `first_name`: VARCHAR(50), **NOT NULL**  
- `last_name`: VARCHAR(50), **NOT NULL**  
- `email`: VARCHAR(100), **NOT NULL**, **UNIQUE**  
- `phone`: VARCHAR(20), NULL  
- `date_of_birth`: DATE, **NOT NULL**

### Table: doctors
- `doctor_id`: INT, **PK**, AUTO_INCREMENT  
- `first_name`: VARCHAR(50), **NOT NULL**  
- `last_name`: VARCHAR(50), **NOT NULL**  
- `specialization`: VARCHAR(100), **NOT NULL**  
- `email`: VARCHAR(100), **NOT NULL**, **UNIQUE**  
- `phone`: VARCHAR(20), NULL

### Table: appointments
- `appointment_id`: INT, **PK**, AUTO_INCREMENT  
- `patient_id`: INT, **FK** → patients(`patient_id`), **NOT NULL**  
- `doctor_id`: INT, **FK** → doctors(`doctor_id`), **NOT NULL**  
- `appointment_time`: DATETIME, **NOT NULL**  
- `status`: TINYINT, **NOT NULL**, DEFAULT 0  _-- 0=Scheduled, 1=Completed, 2=Cancelled_  
- Constraint hint: add unique `(doctor_id, appointment_time)` if you want to prevent overlap. :contentReference[oaicite:2]{index=2}

### Table: admin
- `admin_id`: INT, **PK**, AUTO_INCREMENT  
- `username`: VARCHAR(50), **NOT NULL**, **UNIQUE**  
- `password_hash`: VARCHAR(255), **NOT NULL**  
- `role`: VARCHAR(20), **NOT NULL**, DEFAULT 'admin'

> Notes: Decide delete behavior later (e.g., restrict deleting doctors with future appointments). Keep emails unique for login. :contentReference[oaicite:3]{index=3}

---

## MongoDB Collection Design

Pick **prescriptions** for flexible documents (lists of meds, notes, metadata). :contentReference[oaicite:4]{index=4}

### Collection: `prescriptions`
```json
{
  "_id": "ObjectId(\"651234abcd9012ef34567890\")",
  "patientId": 101,
  "doctorId": 12,
  "appointmentId": 55,
  "dateIssued": "2025-09-14T10:30:00Z",
  "medications": [
    {
      "name": "Amoxicillin",
      "dosage": "500mg",
      "frequency": "3x/day",
      "durationDays": 7,
      "instructions": "After meals"
    },
    {
      "name": "Ibuprofen",
      "dosage": "200mg",
      "frequency": "as needed",
      "durationDays": 5
    }
  ],
  "notes": "Return if symptoms persist.",
  "pharmacy": {
    "name": "CityCare Pharmacy",
    "location": "Main Street 12, Frankfurt"
  },
  "tags": ["infection", "antibiotics"],
  "meta": {
    "createdBy": "doctor",
    "createdAt": "2025-09-14T10:31:00Z",
    "version": 1
  }
}
