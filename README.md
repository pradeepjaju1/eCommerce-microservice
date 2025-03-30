# System Architecture Diagram

This diagram illustrates the flow from the client (browser) through the Google Cloud Platform (GCP) services, including load balancing, Kubernetes Ingress, backend services (User, Product, Order), databases, messaging, and monitoring/logging. Additionally, it shows the deployment of static frontend assets on Cloud Storage.

```ascii
                   +----------------------+
                   |  Client (Browser)    |
                   |  (e.g., Chrome)      |
                   +----------+-----------+
                              │
                              ▼
                   +----------------------+
                   | GCP HTTP(S) Load     |
                   | Balancer             |
                   | (SSL, Routing)       |
                   +----------+-----------+
                              │
                              ▼
                   +----------------------+
                   | Kubernetes Ingress   |
                   | Controller           |
                   | (NGINX / Endpoints)  |
                   +----------+-----------+
                              │
           ┌──────────────────┴──────────────────┐
           │                                     │
           ▼                                     ▼
+--------------------+                 +---------------------+
|  User Service      |                 |  Product Service    |
|  (GKE Pods, 5x)    |                 |  (GKE Pods, 5x)     |
+---------+----------+                 +---------+-----------+
          │                                      │
          ▼                                      ▼
+--------------------+                 +---------------------+
| Cloud SQL /        |                 | Firestore /         |
| Firestore (User)   |                 | Cloud SQL (Product) |
+---------+----------+                 +---------+-----------+
           └──────────────────┬──────────────────┘
                              ▼
                   +----------------------+
                   | Order Service        |
                   | (GKE Pods, 5x)       |
                   +----------+-----------+
                              │
                              ▼
                   +----------------------+
                   | Cloud SQL / Firestore|
                   | (Order Data)         |
                   +----------+-----------+
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
                   | (Monitoring & Logging)|
                   +----------------------+

                   +----------------------+
                   | Static Frontend      |
                   | (Cloud Storage)      |
                   |  HTML/CSS/JS Assets  |
                   +----------------------+
