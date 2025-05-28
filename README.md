## DAY-1
Screenshot or log of Docker image being pushed
![image](https://github.com/user-attachments/assets/118ea481-3792-410f-bed1-0bf66370daaa)

## Why is Docker useful in building and deploying microservices for a real-world product (like an e-commerce or banking app)?
Isolation: Each microservice runs in its own container, with its own dependencies, ensuring no conflicts.
Portability: Docker containers can run on any system that supports Docker, making it easy to move workloads across environments.
Fast Deployment: Containers start quickly and are lightweight, which reduces time to deploy updates or scale services.
Microservice Architecture: For real-world applications like e-commerce or banking, where different components (e.g., payment, user auth, product catalog) need to work independently but communicate with each other, Docker makes it easy to develop, update, and deploy them independently.

## What is the difference between a Docker image and a container in the context of scaling a web application?
A Docker image is a read-only blueprint that contains the application code, runtime, libraries, and environment needed to run an application. Think of it as a snapshot or template.
A Docker container is a running instance of that image. It is the actual execution of the code described in the image.
In the context of scaling, You build one image and use it to spin up multiple containers to handle increased traffic, for example, if a web app is experiencing high load, you can deploy 10 containers from the same image to balance the traffic and ensure availability.

## How does Kubernetes complement Docker when running a product at scale (e.g., hundreds of containers)?
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

## DAY-3
## How would you expose an internal microservice (e.g., user-auth) differently than a public-facing frontend in a Kubernetes-based product?
Internal microservices (like user-auth) are usually not exposed to the internet directly, in place of this they:
Use ClusterIP services so they are only reachable within the cluster.
## Why might a product use Ingress instead of directly exposing each microservice via LoadBalancer?
Using Ingress instead of multiple LoadBalancers supports:
Cost Efficiency: Cloud providers charge for each LoadBalancer service.
Ingress uses one LoadBalancer to expose multiple services, saving cost.
TLS/HTTPS Termination:
Ingress can handle SSL/TLS certificates, enabling secure connections to all services.

## Screenshot of working endpoint via Ingress (use Minikube ingress if on local)
![image](https://github.com/user-attachments/assets/26f13029-b367-4818-95a5-ec433f74acf7)

## DAY-4 
## Screenshot of Helm install and upgrade commands
![image](https://github.com/user-attachments/assets/52ea2858-e159-45bb-8149-8c8198759a61)
![image](https://github.com/user-attachments/assets/a5de6661-54ed-4dbc-bf9c-f745afcf3d49)
## Why is Helm important for managing configuration across different environments in a real-world product (e.g., dev, staging, prod)?
Helm let us define reusable templates and use different values.yaml files for each environment (dev, staging, prod). In short, instead of maintaining multiple yaml files for each environment, Helm allow us to create one chart and use different values-*.yaml files for each environment.
In real-world scenarios, different environments often require different configurations like, change replica count, image tag, resource limits etc. 
## How does Helm simplify deployment rollback during a production incident?
Helm keeps a history of all releases. If a deployment fails, we can quickly roll back to a previous stable version by simple command 'helm rollback <release-name>'. This makes incident recovery faster and safer.




