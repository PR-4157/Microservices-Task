# Microservices Kubernetes Deployment using Minikube

## Project Overview

This project demonstrates deployment of a microservices-based Node.js application on Kubernetes using Minikube.

The application contains four services:

- User Service (Port 3000)
- Product Service (Port 3001)
- Order Service (Port 3002)
- Gateway Service (Port 3003)

The deployment includes:

- Kubernetes Deployments
- Kubernetes Services
- Resource management
- Health probes
- Inter-service communication
- Optional Ingress configuration
  
---

# Project Structure

submission/
├── deployments/
│   ├── user-service.yaml
│   ├── product-service.yaml
│   ├── order-service.yaml
│   └── gateway-service.yaml
├── services/
│   ├── user-service.yaml
│   ├── product-service.yaml
│   ├── order-service.yaml
│   └── gateway-service.yaml
├── ingress/
│   └── ingress.yaml
├── screenshots/
│   ├── pods.png
│   ├── logs.png
│   └── service-test.png
└── README.md

---

# Prerequisites

Install the following tools before starting:

- Docker
- Kubernetes CLI (kubectl)
- Minikube

Official Websites:

- Kubernetes: https://kubernetes.io/
- Minikube: https://minikube.sigs.k8s.io/
- Docker: https://www.docker.com/

---

# Step 1: Start Minikube

Start Minikube cluster:

```bash
minikube start
<img width="615" height="391" alt="Screenshot 2026-05-18 at 7 41 59 PM" src="https://github.com/user-attachments/assets/aefeb837-0bec-4dc0-988d-8d70bbd1779d" />

Check cluster status:
kubectl cluster-info

Verify nodes:
kubectl get nodes
<img width="602" height="111" alt="Screenshot 2026-05-18 at 8 41 50 PM" src="https://github.com/user-attachments/assets/2ef411b3-a67f-462e-81e0-b28b1a6fc6ef" />


# Step 2: Deploy Microservices
Apply deployment files:
kubectl apply -f deployments/
<img width="600" height="89" alt="Screenshot 2026-05-19 at 6 18 23 PM" src="https://github.com/user-attachments/assets/77493ec8-7b70-4d7a-82ff-4fd0daa35bcf" />

Apply service files:
kubectl apply -f services/
<img width="599" height="98" alt="Screenshot 2026-05-19 at 6 13 47 PM" src="https://github.com/user-attachments/assets/23e83d91-1737-4cae-869a-8afe8d841503" />

Verify deployments:
kubectl get deployments
<img width="595" height="113" alt="Screenshot 2026-05-19 at 6 14 22 PM" src="https://github.com/user-attachments/assets/e10fa6a4-98d2-4b12-866b-9dbcd2dde51b" />

Verify pods:
kubectl get pods
<img width="585" height="111" alt="Screenshot 2026-05-18 at 8 41 50 PM" src="https://github.com/user-attachments/assets/cfa61c38-f063-4818-a8ca-b9f87437676b" />

Verify services:
kubectl get services
<img width="601" height="102" alt="Screenshot 2026-05-18 at 8 41 57 PM" src="https://github.com/user-attachments/assets/23ba4404-d43a-41b7-b1a9-4c8b87631c8b" />

# Step 3: Validate Inter - Service Communication
Check logs from gateway service:
kubectl logs gateway-service-756c54dd79-sn8nk
<img width="599" height="100" alt="Screenshot 2026-05-18 at 8 42 43 PM" src="https://github.com/user-attachments/assets/98cccae9-5781-401c-bdac-3e5f51a2740f" />

Test service communication inside cluster:
kubectl exec -it <gateway-pod-name> -- sh
<img width="593" height="85" alt="Screenshot 2026-05-18 at 8 41 58 PM" src="https://github.com/user-attachments/assets/05988097-178a-4748-9de8-e0c20407d652" />

Use curl:
curl http://user-service:3000
curl http://product-service:3001
curl http://order-service:3002
<img width="605" height="123" alt="Screenshot 2026-05-18 at 8 42 49 PM" src="https://github.com/user-attachments/assets/5c5efcc5-1093-4db1-9032-54439e013667" />


# Step 4: Port Forward Testing
Expose Gateway Service locally:
kubectl port-forward service/gateway-service 8080:3003
<img width="593" height="87" alt="Screenshot 2026-05-19 at 6 31 51 PM" src="https://github.com/user-attachments/assets/4b1479c4-9fbc-470a-9706-ca9fd3265c03" />

Or test using curl:
curl http://localhost:8080
<img width="573" height="82" alt="Screenshot 2026-05-19 at 6 31 35 PM" src="https://github.com/user-attachments/assets/87b33003-16bc-4d71-a670-b8ae601577d1" />

---

# Summary

This project successfully demonstrates deployment of a containerized microservices application on Kubernetes using Minikube. All four Node.js services were deployed using Kubernetes Deployment and Service manifests with proper configuration including resource limits, environment variables, liveness probes, and readiness probes.

Cluster-level communication between services was verified successfully using Kubernetes networking and service discovery features. The application was tested using `kubectl port-forward`, service DNS names, and pod logs.

The project also demonstrates practical understanding of:

- Kubernetes Deployments
- ClusterIP Services
- Pod communication
- Resource management
- Health monitoring
- Minikube local cluster setup
- Kubernetes debugging and troubleshooting

Optional ingress configuration was also implemented for external routing and path-based access management.

---

# Conclusion

This assessment provided hands-on experience in deploying and managing microservices applications using Kubernetes and Minikube. The project helped in understanding real-world container orchestration concepts such as deployment automation, service discovery, scaling, networking, and application health management.

By completing this project, the following objectives were achieved:

- Successful deployment of all microservices
- Proper inter-service communication
- Kubernetes resource configuration
- Application testing and validation
- Ingress-based routing implementation (optional)

Overall, this project demonstrates foundational Kubernetes administration and microservices deployment skills required for modern cloud-native application environments.

---

# Final Output

The Kubernetes cluster was successfully configured using Minikube, and all application components were deployed and verified successfully.

Final validation included:

- All pods running in healthy state
- Services accessible within cluster
- Gateway service responding correctly
- Logs confirming successful communication
- Port forwarding tested successfully
- Optional ingress routing configured and validated

The project structure, deployment files, screenshots, and documentation were organized as per the assignment requirements.

