# k8d-services

In Kubernetes (K8s), a Service is used to expose your application (Pods) so that it can be accessed inside or outside the cluster. There are several types of Services, each designed for a specific use case.

🔹 1. ClusterIP (Default Service)

Explanation:
ClusterIP is the default service type in Kubernetes. It exposes the service only within the cluster, meaning it cannot be accessed from outside. It is mainly used for internal communication between microservices. For example, a backend service talking to a database service.

YAML Code Example:

apiVersion: v1
kind: Service
metadata:
  name: my-clusterip-service
spec:
  type: ClusterIP
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080

🔹 2. NodePort Service

Explanation:
NodePort exposes the service on a static port on each node’s IP address. This allows external users to access the service using <NodeIP>:<NodePort>. It is commonly used for testing or small applications but not recommended for production at scale.

YAML Code Example:

apiVersion: v1
kind: Service
metadata:
  name: my-nodeport-service
spec:
  type: NodePort
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
      nodePort: 30007

🔹 3. LoadBalancer Service

Explanation:
LoadBalancer service exposes your application externally using a cloud provider’s load balancer (like AWS, Azure, GCP). It automatically creates an external IP address and distributes traffic across Pods. This is commonly used in production environments.



<img width="1071" height="768" alt="image" src="https://github.com/user-attachments/assets/55a8a798-a86e-4c1c-b2e2-4ca75b1e804d" />



<img width="767" height="787" alt="image" src="https://github.com/user-attachments/assets/dbc5db63-0fc0-417c-9344-d1975e8024c6" />
