# 🚌 BookMyBus — Online Bus Ticket Booking System

[![Java](https://img.shields.io/badge/Java-17-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.x-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)](https://spring.io/projects/spring-boot)
[![React](https://img.shields.io/badge/React-18-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://react.dev/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-005C84?style=for-the-badge&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![JWT](https://img.shields.io/badge/JWT-Auth-000000?style=for-the-badge&logo=JSON%20web%20tokens)](https://jwt.io/)
[![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)

> A full-stack bus ticket booking platform with real-time seat availability, secure JWT authentication, and clean layered architecture.

---

## 📋 Table of Contents
- [Features](#features)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [API Endpoints](#api-endpoints)
- [Database Schema](#database-schema)
- [Screenshots](#screenshots)

---

## ✨ Features

- 🔐 **JWT Authentication** — Secure login/register with token-based auth
- 🔍 **Bus Search** — Search buses by source, destination, and date
- 💺 **Seat Selection** — Real-time seat availability with interactive seat map
- 🎟️ **Ticket Booking** — Book, view, and cancel tickets with booking history
- 👤 **User Management** — Profile management and booking history
- 🛡️ **Role-based Access** — Separate Admin and Passenger roles
- 📱 **Responsive UI** — React frontend with mobile-friendly design

---

## 🏗️ Architecture

```
bookmybus/
├── backend/                        # Spring Boot Application
│   ├── src/main/java/com/bookmybus/
│   │   ├── controller/             # REST Controllers
│   │   │   ├── AuthController.java
│   │   │   ├── BusController.java
│   │   │   ├── BookingController.java
│   │   │   └── UserController.java
│   │   ├── service/                # Business Logic Layer
│   │   │   ├── AuthService.java
│   │   │   ├── BusService.java
│   │   │   └── BookingService.java
│   │   ├── repository/             # Data Access Layer (JPA)
│   │   ├── model/                  # Entity Classes
│   │   │   ├── User.java
│   │   │   ├── Bus.java
│   │   │   ├── Route.java
│   │   │   ├── Seat.java
│   │   │   └── Booking.java
│   │   ├── dto/                    # Request/Response DTOs
│   │   ├── security/               # JWT Config & Filters
│   │   └── exception/              # Global Exception Handling
│   └── src/main/resources/
│       └── application.properties
│
└── frontend/                       # React Application
    ├── src/
    │   ├── components/
    │   ├── pages/
    │   ├── services/               # Axios API calls
    │   └── context/                # Auth Context
    └── package.json
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | Java 17, Spring Boot 3.x |
| ORM | Spring Data JPA / Hibernate |
| Security | Spring Security + JWT |
| Frontend | React 18, Axios, React Router |
| Database | MySQL 8.0 |
| Build Tool | Maven |
| Container | Docker |
| API Testing | Postman |

---

## 🚀 Getting Started

### Prerequisites
- Java 17+
- Node.js 18+
- MySQL 8.0
- Maven 3.8+

### Backend Setup
```bash
# Clone the repository
git clone https://github.com/Amanrai1480/BookMyBus.git
cd BookMyBus/backend

# Configure database in application.properties
spring.datasource.url=jdbc:mysql://localhost:3306/bookmybus_db
spring.datasource.username=your_username
spring.datasource.password=your_password

# Run the application
mvn spring-boot:run
```

### Frontend Setup
```bash
cd BookMyBus/frontend
npm install
npm start
```

### With Docker
```bash
docker-compose up --build
```

---

## 📡 API Endpoints

### Authentication
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register new user |
| POST | `/api/auth/login` | Login and get JWT token |

### Bus
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/buses/search?from=&to=&date=` | Search available buses |
| GET | `/api/buses/{busId}/seats` | Get seat availability |
| POST | `/api/admin/buses` | Add new bus (Admin) |

### Booking
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/bookings` | Create a booking |
| GET | `/api/bookings/user/{userId}` | Get user's bookings |
| DELETE | `/api/bookings/{bookingId}` | Cancel a booking |

---

## 🗄️ Database Schema

```sql
-- Core Tables
Users          (id, name, email, password, role, phone, created_at)
Buses          (id, bus_number, bus_name, type, total_seats, operator)
Routes         (id, source, destination, departure_time, arrival_time, fare)
Bus_Route      (bus_id, route_id, journey_date)
Seats          (id, bus_id, seat_number, is_available)
Bookings       (id, user_id, bus_id, route_id, seat_numbers,
                journey_date, total_fare, status, booked_at)
```

---

## 🤝 Contributing
Pull requests are welcome. For major changes, please open an issue first.

## 📄 License
[MIT](LICENSE)
