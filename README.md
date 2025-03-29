                          +------------------------+
                          |   Client (Browser)     |
                          |   e.g., Chrome, Mobile |
                          +-----------+------------+
                                      │
                                      ▼
                          +------------------------+
                          |  GCP HTTP(S) Load      |
                          |     Balancer           |
                          | (SSL Termination,      |
                          | Global Traffic Routing)|
                          +-----------+------------+
                                      │
                                      ▼
                          +------------------------+
                          | Kubernetes Ingress     |
                          | Controller (NGINX,     |
                          |   Apigee, Cloud        |
                          |   Endpoints)           |
                          +-----------+------------+
                                      │
           ┌──────────────────────────┼────────────────────────────┐
           │                          │                            │
           ▼                          ▼                            ▼
 +-----------------+         +-------------------+         +-----------------+
 | User Service    |         | Product Service   |         | Order Service   |
 | (GKE Pods)      |         | (GKE Pods)        |         | (GKE Pods)      |
 |  Replicas: 5    |         |  Replicas: 5      |         |  Replicas: 5    |
 +-------+---------+         +---------+---------+         +-------+---------+
         │                             │                           │
         ▼                             ▼                           ▼
+-----------------+         +-------------------+         +-----------------+
| Cloud SQL or    |         | Firestore /       |         | Cloud SQL or    |
| Firestore       |         | Cloud SQL         |         | Firestore       |
| (User Data)     |         | (Product Data)    |         | (Order Data)    |
+-----------------+         +-------------------+         +-----------------+
                                      │
                                      ▼
                          +------------------------+
                          | Google Cloud Pub/Sub   |
                          | (Event-Driven Messaging|
                          |  for Async Processes)  |
                          +-----------+------------+
                                      │
                                      ▼
                          +------------------------+
                          | Google Cloud Ops       |
                          | (Monitoring, Logging,  |
                          |  Alerting & Tracing)   |
                          +------------------------+

                +-------------------------+
                | Static Frontend         |
                | (Hosted on Cloud Storage|
                |  - HTML/CSS/JS Assets)  |
                +-------------------------+
