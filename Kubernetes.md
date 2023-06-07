Kubernetes:
Kubernetes is an open-source Container Management tool which automates container deployment, container (de)scaling & container load balancing.
- Written in Golang, it has a huge community becasue it was first developed by Google & later donated to CNCF (Cloud Native Computing Foundation)
- Can group 'n' no of containers into one logical unit for managind & deploying them easily

Kubernetes Actually is:
- Robust & Reliable
- Best solution for scaling up containers
- A container Orchestration platform
- Backed by huge community

Features of Kubernetes:
- Automatic Binpacking
- Service Discovery & Load Balancing
- Storage Orchestration
- Self Healing
- Secret & Configuration Management
- Batch Execution
- Harizontal Scaling
- Automatic Rollbacks & Rollouts

Namespaces:
- Provides a system resource, a layer of abstraction
- Namespaces provides a mechanism for isolating groups of resources within a single cluster. 
- Names of resources need to be unique within a namespace, but not across namespaces. 
- Namespace-based scoping is applicable only for namespaced objects (e.g. Deployments, Services, etc) and not for cluster-wide objects (e.g. StorageClass, Nodes, PersistentVolumes, etc).

