## DAY-1
Screenshot or log of Docker image being pushed
![image](https://github.com/user-attachments/assets/118ea481-3792-410f-bed1-0bf66370daaa)

Why is Docker useful in building and deploying microservices for a real-world product (like an e-commerce or banking app)?
Isolation: Each microservice runs in its own container, with its own dependencies, ensuring no conflicts.
Portability: Docker containers can run on any system that supports Docker, making it easy to move workloads across environments.
Fast Deployment: Containers start quickly and are lightweight, which reduces time to deploy updates or scale services.
Microservice Architecture: For real-world applications like e-commerce or banking, where different components (e.g., payment, user auth, product catalog) need to work independently but communicate with each other, Docker makes it easy to develop, update, and deploy them independently.

What is the difference between a Docker image and a container in the context of scaling a web application?
A Docker image is a read-only blueprint that contains the application code, runtime, libraries, and environment needed to run an application. Think of it as a snapshot or template.
A Docker container is a running instance of that image. It is the actual execution of the code described in the image.

How does Kubernetes complement Docker when running a product at scale (e.g., hundreds of containers)?
Kubernetes complements Docker by providing orchestration features that are critical when managing containers at scale:
Automated Deployment and Scaling: Kubernetes can automatically scale the number of containers based on CPU usage or other metrics.
Rolling Updates and Rollbacks: You can update your application without downtime and revert changes if something goes wrong.
Load Balancing: It distributes traffic evenly across multiple container instances.



## DAY-2
## Explanation in README.md about affinity rules applied
By using requiredDuringSchedulingIgnoredDuringExecution, which means:
a). The pod must be scheduled on a node that matches the condition.
b). If no matching node is found, the pod won't be scheduled.

key: disktype — this is a node label key.
operator: In — matches if the node's label value is one of the listed values.
values: [ssd] — pod will only schedule on nodes labeled with disktype=ssd.
![image](https://github.com/user-attachments/assets/868560d9-f9ce-4793-8f6f-e8f3410c09fc)

## Why do we set requests and limits for CPU/memory in a production-grade product?
Stable performance: Resource requests reserve the minimum required CPU/Memory to ensure containers run reliably without being starved.
Efficient scheduling: Kubernetes uses the request values to make informed decisions about where to place pods.
Fair resource sharing: Resource limits prevent any one container from consuming too much, protecting other workloads on the same node.

## When would a product team apply node affinity in Kubernetes?
Workload isolation: Run specific services only on nodes labeled for them (e.g., high-memory or GPU nodes).
Compliance/security: Ensure sensitive workloads run only on secure, audited nodes.
Performance tuning: Assign latency-sensitive workloads to high-performance nodes.

## Screenshot or logs showing the running pod and node placement
![image](https://github.com/user-attachments/assets/ec8a39e9-6d1e-4750-b176-a6f9e5594c8e)

