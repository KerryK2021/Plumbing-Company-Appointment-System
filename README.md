# Plumbing-Company-Appointment-System
A repository for Plumbing Company Appointment System Project.

### Domain Model
```mermaid
flowchart 
  USERS --- APPOINTMENTS
  PLUMBERS --- APPOINTMENTS
  APPOINTMENTS --- SERVICES
  APPOINTMENTS --- APPOINTMENT_STATUS
  PAYMENTS --- APPOINTMENTS
  AVAILABILITY --- PLUMBERS
```

### ER Diagram
```mermaid
erDiagram
  users {
        serial id PK
        varchar first_name
        varchar last_name
        varchar email
        varchar phone
        varchar address
        varchar postcode
        varchar username
        varchar password
        serial role_id FK
    }

    appointments {
        serial id PK
        serial user_id FK
        serial plumber_id FK
        serial service_id FK
        date date
        datetime time
        varchar notes
        serial status_id FK
    }

    plumbers {
        serial id PK
        varchar first_name 
        varchar last_name
        varchar email
        varchar phone
        varchar availability
    }

    services {
        serial id PK
        varchar service_name
        varchar description
        varchar price
    }

    appointment_status {
        serial id PK
        varchar status
    }

    payments {
        serial id PK
        serial appointment_id FK
        decimal amount
        varchar payment_method 
        datetime transaction_date
    }

    availablity {
        serial id PK
        serial plumber_id FK
        date date
        time time_slot
        bool available
    }

    users ||--o{ appointments : ""
    plumbers ||--o{ appointments : ""
    services ||--o{ appointments : ""
    appointment_status ||--o{ appointments : ""
    appointments ||--|| payments : ""
    plumbers ||--o{ availablity : ""

```

### API Specification
#### USERS
`GET /users` 
Return a list of all users

Response 200
```json
[
  {
    "id": 1,
    "first_name": "Kerry",
    "last_name": "Kennedy",
    "email": "kerrytkennedy@hotmail.com",
    "phone": "07584916321",
    "address": "78 Wellington Park Drive",
    "postcode": "BT893PT",
    "username": "KerryK0517",
    "password": "password123",
    "role_id" : 1
  },
  {
    "id": 2,
    "first_name": "Joe",
    "last_name": "Bloggs",
    "email": "jbloggs@email.com",
    "phone": "07819372198",
    "address": "123 New Street",
    "postcode": "JBloggs123",
    "password": "newpass1234",
    "role_id" : 2
  }
]
```
---
