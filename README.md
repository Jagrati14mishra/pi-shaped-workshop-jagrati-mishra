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

