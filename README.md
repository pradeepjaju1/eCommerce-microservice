graph TD
    A[Client (Browser)]:::client --> B[GCP HTTP(S) Load Balancer]:::lb
    B --> C[Kubernetes Ingress Controller]:::ingress
    C --> D[User Service<br/>(GKE Pods, 5x)]:::service
    C --> E[Product Service<br/>(GKE Pods, 5x)]:::service
    C --> F[Order Service<br/>(GKE Pods, 5x)]:::service
    D --> G[Cloud SQL / Firestore<br/>(User Data)]:::db
    E --> H[Firestore / Cloud SQL<br/>(Product Data)]:::db
    F --> I[Cloud SQL / Firestore<br/>(Order Data)]:::db
    D --- J[Google Cloud Pub/Sub<br/>(Event Messaging)]:::messaging
    E --- J
    F --- J
    J --> K[Google Cloud Ops<br/>(Monitoring & Logging)]:::ops
    A --> L[Static Frontend<br/>(Cloud Storage)]:::frontend

classDef client fill:#FFD700,stroke:#000,stroke-width:2px;
classDef lb fill:#87CEFA,stroke:#000,stroke-width:2px;
classDef ingress fill:#98FB98,stroke:#000,stroke-width:2px;
classDef service fill:#FFB6C1,stroke:#000,stroke-width:2px;
classDef db fill:#FFA07A,stroke:#000,stroke-width:2px;
classDef messaging fill:#B0E0E6,stroke:#000,stroke-width:2px;
classDef ops fill:#D8BFD8,stroke:#000,stroke-width:2px;
classDef frontend fill:#E6E6FA,stroke:#000,stroke-width:2px;
