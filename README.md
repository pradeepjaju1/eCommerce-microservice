```mermaid
graph TD
    A[Client (Browser)] --> B[GCP HTTP(S) Load Balancer]
    B --> C[Kubernetes Ingress Controller]
    C --> D[User Service (GKE Pods, 5x)]
    C --> E[Product Service (GKE Pods, 5x)]
    C --> F[Order Service (GKE Pods, 5x)]
    D --> G[Cloud SQL / Firestore (User Data)]
    E --> H[Firestore / Cloud SQL (Product Data)]
    F --> I[Cloud SQL / Firestore (Order Data)]
    D --- J[Google Cloud Pub/Sub (Event Messaging)]
    E --- J
    F --- J
    J --> K[Google Cloud Ops (Monitoring & Logging)]
    A --> L[Static Frontend (Cloud Storage)]
