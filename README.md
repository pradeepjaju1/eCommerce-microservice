# eCommerce-microservice

                     +----------------------+
                     |  Client (Browser)    |
                     |    (e.g., Chrome)    |
                     +----------+-----------+
                                │
                                ▼
                     +----------------------+
                     | GCP HTTP(S) Load     |
                     |    Balancer          |
                     | (SSL Termination &   |
                     |  Global Routing)     |
                     +----------+-----------+
                                │
                                ▼
                     +----------------------+
                     |  API Gateway /       |
                     |  Ingress Controller  |
                     |   (e.g., NGINX,      |
                     |  Apigee, Cloud       |
                     |  Endpoints)          |
                     +----------+-----------+
                                │
              +-----------------+-----------------+
              │                 │                 │
              ▼                 ▼                 ▼
     +----------------+  +----------------+  +----------------+
     |  User Service  |  | Product Service|  | Order Service  |
     | (Cloud Run or  |  | (Cloud Run or  |  | (Cloud Run or  |
     |      GKE)      |  |      GKE)      |  |      GKE)      |
     +----------------+  +----------------+  +----------------+
              │                 │                 │
              ▼                 ▼                 ▼
     +----------------+  +----------------+  +----------------+
     | Cloud SQL /    |  | Firestore/     |  | Cloud SQL /    |
     | Firestore      |  | Cloud SQL      |  | Firestore      |
     |  (User Data)   |  | (Product Data) |  |  (Order Data)  |
     +----------------+  +----------------+  +----------------+
                                │
                                ▼
                     +----------------------+
                     | Google Cloud Pub/Sub |
                     | (Event Messaging)    |
                     +----------+-----------+
                                │
                                ▼
                     +----------------------+
                     | Google Cloud Ops     |
                     | (Monitoring &        |
                     |  Logging)            |
                     +----------------------+

                     +----------------------+
                     | Static Frontend      |
                     | (Cloud Storage:      |
                     |  HTML/CSS/JS Assets) |
                     +----------------------+
