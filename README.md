<div align="right">
  <img src="https://img.shields.io/badge/Date-2026--03--10-blue?style=for-the-badge" alt="Date" />
  <img src="https://img.shields.io/badge/Status-Active-success?style=for-the-badge" alt="Status" />
  <img src="https://img.shields.io/badge/Tier-Master-gold?style=for-the-badge" alt="Tier" />
</div>

# Thirsty-lang Microservices Architecture 💧⚙️

Production-ready microservices framework with service discovery, load balancing, and inter-service communication.

## Services Included

- **User Service** - Authentication & user management
- **Product Service** - Catalog & inventory
- **Order Service** - Order processing & fulfillment
- **Payment Service** - Payment processing with armor security
- **Notification Service** - Email/SMS notifications
- **API Gateway** - Unified entry point

## Features

- Service discovery with Consul
- Load balancing  
- Circuit breakers with defend
- Distributed tracing
- Centralized logging
- Health checks
- Docker & Kubernetes deployment

## Quick Start

```bash
docker-compose up
```

Access:

- API Gateway: <http://localhost:8000>
- User Service: <http://localhost:8001>
- Product Service: <http://localhost:8002>

## Inter-Service Communication

```thirsty
glass ServiceClient {
  glass async call(service, endpoint, data) {
    shield serviceProtection {
      drink url = await serviceDiscovery.find(service)
      
      cascade {
        drink response = await httpPost(url + endpoint, data)
        return response
      } spillage error {
        defend {
          circuitBreaker: parched,
          retry: 3,
          fallback: glass() { return cachedResponse() }
        }
      }
    }
  }
}
```

## License

MIT
