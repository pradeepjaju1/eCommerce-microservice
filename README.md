# eCommerce-microservice
graph TD
  A[Client (Browser)] --> B[GCP HTTP(S) Load Balancer]
  B --> C[API Gateway / Ingress]
  C --> D[User Service (Cloud Run/GKE)]
  C --> E[Product Service (Cloud Run/GKE)]
  C --> F[Order Service (Cloud Run/GKE)]
  D --> G[Cloud SQL / Firestore<br/>(User Data)]
  E --> H[Firestore / Cloud SQL<br/>(Product Data)]
  F --> I[Cloud SQL / Firestore<br/>(Order Data)]
  D --- J[Google Cloud Pub/Sub]
  E --- J
  F --- J
  J --> K[Google Cloud Operations<br/>(Monitoring & Logging)]
  A --> L[Static Frontend<br/>(Cloud Storage)]

