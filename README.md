# gitstream-demo

A minimal full-stack demo showcasing inter-service auth and order processing.

## Services

- **Auth** (Python/FastAPI) – port **8000**
- **Billing** (C#/ASP.NET) – internal only
- **Orders** (Java/Spring Boot) – port **8002**
- **Frontend** (Node.js/Express + static HTML/JS) – port **3000**

All services run together via Docker Compose.

## Quick Start

```bash
docker-compose up --build
```

## APIs

1. **Login**
   ```
   POST http://localhost:8000/auth/login
   Body: { "username":"alice","password":"password123" }
   → { "token": "..." }
   ```
2. **Place Order**
   ```
   POST http://localhost:8002/orders
   Headers: Authorization: Bearer <token>
   Body: { "productId":"widget-123","quantity":2 }
   → "Order placed successfully by alice"
   ```
3. **List Orders**
   ```
   GET http://localhost:8002/orders
   Headers: Authorization: Bearer <token>
   → [ { "username":"alice","productId":"widget-123","quantity":2 }, … ]
   ```

That's all! Enjoy the demo.
