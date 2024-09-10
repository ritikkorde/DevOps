 Kubernetes /K8s
is an open source platform designed to automate the deployment,scaling and management of containerized application/containers.
Container Orchestration /container management tool- Kubernetes manages clusters of containers,ensuring they run efficiently across multiple machine.
Features of K8s
- Container orchestration 
- automated scaling
- Self -Healing
- service Discovery & Load balancing
- Storage Orchestration: Kubernetes allows you to automatically mount the storage system of your choice, whether from local storage, cloud providers, or network storage systems.
- Automated Rollouts & Rollbacks: Kubernetes can manage the deployment of new versions of applications without downtime, and roll back to previous versions if something goes wrong.

A Kubernetes cluster is a group of nodes that run containerized applications and are managed by the Kubernetes control plane

https://medium.com/cloud-native-daily/a-comprehensive-kubernetes-overview-unleash-the-power-of-kubernetes-dc3e2e3d5630

#Architecture of kubernetes 

in this architecture kubernetes has two main plane one is control plane and another is worker plane
1) the control plane is responsible for managing the kubernetes cluster
2) it make decision about the cluster,such as scheduling and monitoring the cluster state.

the main component of the control plane is 
- API Server 
- kube scheduler
- controller manager
- etcd

API server
- The API server is the front end of the kubernetes control plane
- it is basically resposible for communication between control plane and worker plane
and also updates the cluster state in etcd.

kube schedule
- the scheduler assign the pods to nodes based on resources availability
- it handle pod creation and management

controller manager 
- it is resposible for running controller processess.
- controller are resposible for maintaing the desired state of pods

etcd
- it store all metadata of cluster in key value format
- like configuration and state information

Worker plane
- the worker plane consist of worker node that run containerized application
- each worker node has essential component that communicate with the control plane

Kubelet
- kubelet is the agent running on each node that ensure container are running in a pod.
- it communicate with the control plane and receive instruction about which pods to run on the node.

kube proxy 
- kube  proxy maintain network rules on nodes ,assigning ip adress and configuring load balancer.
- allowing communication between pods and services within the cluster

Container runtime engine
- this is the software resposible for running the container
- and manage container image on node 

Pods 
- pods are the smallest deployable units
- the group of one or more conatainer with shared storage and network resources and specification how to run the containers



same version of cluster and  ectl and kubectl


deployment used for stateless application
statefullset are used for stateful application
  by defualt objects communicate services through headless services

Object of K8s
1. Deployment
Purpose: To manage stateless applications.
How It Works: A Deployment ensures that a specified number of pod replicas are running at all times. If a pod crashes or is deleted, the Deployment controller will automatically create a new pod to replace it.
Use Case: Ideal for scalable, stateless applications like web servers, where the state doesn't need to be preserved across restarts.
https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
https://kubernetes.io/docs/tasks/run-application/run-stateless-application-deployment/

2. StatefulSet
Purpose: To manage stateful applications.
How It Works: Unlike Deployments, StatefulSets ensure that each pod has a unique, stable identity and persistent storage. Pods in a StatefulSet are created and destroyed in a specific order, and each pod gets a stable network identity and storage that persists across rescheduling.
Use Case: Ideal for applications that require stable, persistent storage and network identities, like databases (e.g., MySQL, MongoDB) or distributed systems.


3. DaemonSet
Purpose: To ensure that a copy of a pod runs on all (or specific) nodes in the cluster.
How It Works: A DaemonSet automatically deploys a pod on every node in the cluster (or a subset of nodes if specified). If new nodes are added to the cluster, the DaemonSet ensures that the pod is also deployed on the new nodes.
Use Case: Ideal for background system services like logging agents, monitoring daemons, or network plugins that need to run on every node.

Summary
Deployment: Use for stateless applications where you need to scale and manage pods easily.

StatefulSet: Use for stateful applications where each pod needs a unique identity and stable storage.

DaemonSet: Use when you need to run a specific pod on every node in the cluster



In Kubernetes, exposing a pod means making it available to the cluster through a service:

#Services
A service groups a set of pod endpoints into a single resource and defines a policy for accessing them.

ClusterIP
The default service type that exposes the service on an internal IP address, making it only accessible from within the cluster.

NodePort
Exposes the service on the same port of each selected node in the cluster, making it accessible from outside the cluster

n Kubernetes, the term "expose" refers to making a service or an application accessible to the network. This can mean exposing the service internally within the cluster or externally to the outside world. When you expose a Kubernetes service, you define how the service will be accessed, whether it's from within the cluster, from other services, or from external users.

Here are the common ways to expose a service in Kubernetes:

ClusterIP: This is the default type. It exposes the service on an internal IP within the cluster. This means the service is only accessible from within the cluster.

NodePort: This type exposes the service on a static port on each node’s IP. The service becomes accessible from outside the cluster using the <NodeIP>:<NodePort> combination.

LoadBalancer: This type exposes the service externally using a cloud provider’s load balancer. It automatically provisions a load balancer for the service and directs traffic to the service through it.

ExternalName: This type maps the service to the contents of an external DNS name, returning a CNAME record with the name.

Headless


    kubectl expose deployment/my-nginx

Labels and selectors--
In Kubernetes, labels and selectors are fundamental concepts used to organize and manage resources like pods, services, and deployments.

Labels
What Are Labels?

Labels are key-value pairs attached to Kubernetes objects like pods, nodes, and services.
They are used to add identifying metadata to objects, which helps to organize and select them based on their characteristics.
Use Cases:

Grouping objects: You can assign labels to group objects with similar roles (e.g., all frontend pods).
Identifying objects: Labels can help identify different environments (e.g., development, staging, production).


In Kubernetes, labels and selectors are fundamental concepts used to organize and manage resources like pods, services, and deployments.

Labels
What Are Labels?

Labels are key-value pairs attached to Kubernetes objects like pods, nodes, and services.
They are used to add identifying metadata to objects, which helps to organize and select them based on their characteristics.
Example:

yaml
Copy code
labels:
  app: my-app
  environment: production
  tier: frontend
Here, app, environment, and tier are keys, and my-app, production, and frontend are their corresponding values.

Use Cases:

Grouping objects: You can assign labels to group objects with similar roles (e.g., all frontend pods).
Identifying objects: Labels can help identify different environments (e.g., development, staging, production).
Selectors
What Are Selectors?

Selectors are queries used to filter Kubernetes objects based on their labels.
They enable you to select a subset of objects with specific labels.
Types of Selectors:

Equality-Based Selectors:
Match objects where a label key has a specific value.
Example: app=my-app will select all objects with the label app: my-app.
Set-Based Selectors:
Match objects where a label key's value is in a list of values.
Example: environment in (production, staging) will select objects with environment: production or environment: staging.
Putting It All Together
Labels are used to tag Kubernetes objects with metadata, while selectors are used to filter and select those objects based on their labels.
For instance, a Kubernetes service might use a selector to route traffic only to pods with a specific label, ensuring that the right instances of an application receive the traffic.
This system of labels and selectors makes it easier to manage and scale applications in Kubernetes by allowing for flexible grouping and querying of resources


Taints And toleration--
In Kubernetes, taints and tolerations work together to control which pods can be scheduled on which nodes. They are used to ensure that certain workloads are placed on specific nodes, or to prevent certain nodes from accepting particular workloads.

Taints
What Are Taints?

Taints are applied to nodes to mark them as unsuitable for most pods. They "taint" the node, meaning that the node will repel any pod that does not tolerate that taint.
A taint consists of a key, a value, and an effect.
Components of a Taint:

Key: A label key that identifies the taint.
Value: A value that provides additional information about the taint.
Effect: The action to be taken by Kubernetes when a pod does not tolerate the taint

- NoSchedule: Pods that don't tolerate the taint won't be scheduled on the node.
- PreferNoSchedule: Kubernetes will try not to schedule pods that don't tolerate the taint, but it's not guaranteed.
- NoExecute: Pods that don't tolerate the taint will be evicted from the node if they are already running there.
Example:

#kubectl taint nodes node1 key=value:NoSchedule
This command taints node1 so that no pods without the corresponding toleration can be scheduled on it.

Tolerations
What Are Tolerations?

Tolerations are applied to pods and allow them to be scheduled on nodes with matching taints.
They "tolerate" the taint, allowing the pod to be scheduled on a tainted node.
Components of a Toleration:

Key: The key of the taint the pod can tolerate.
Operator: Defines the relationship between the key and value (Equal, Exists).
Value: The value of the taint the pod can tolerate (used with Equal operator).
Effect: The effect the pod can tolerate (NoSchedule, PreferNoSchedule, NoExecute).
TolerationSeconds: (Optional) Duration for which the pod can tolerate the taint.
Example:

yaml
Copy code
tolerations:
- key: "key"
  operator: "Equal"
  value: "value"
  effect: "NoSchedule"
This toleration allows a pod to be scheduled on a node with the taint key=value:NoSchedule.

Putting It All Together
Taints are used to mark nodes so that they repel certain pods. For example, you might taint nodes that are reserved for specific workloads like databases or GPU-intensive tasks.
Tolerations are used by pods to indicate that they can be scheduled on nodes with specific taints.
Example Use Case
Imagine you have a node dedicated to running only critical workloads. You might taint this node with critical=true:NoSchedule. Then, only pods that have a toleration for critical=true will be able to run on that node. This ensures that non-critical workloads won't take up resources on the node meant for critical tasks.

This mechanism allows for fine-grained control over where workloads are placed in your Kubernetes cluster, helping to optimize resource usage and maintain reliability

ConfigMap
1. ConfigMaps
Purpose: Store non-sensitive configuration data as key-value pairs that can be used by your Kubernetes applications.
Use Cases:
Store configuration settings (e.g., URLs, environment variables).
Share configuration data across multiple pods without hardcoding them into your containers

ConfigMaps allow you to store non-sensitive configuration data, such as environment variables, configuration files, or command-line arguments, in key-value pairs. These can then be injected into your applications running in Pods.
-ConfigMaps allow you to store non-sensitive configuration data, such as environment variables, configuration files, or command-line arguments, in key-value pairs. These can then be injected into your applications running in Pods.

apiVersion: v1
kind: ConfigMap
metadata:
  name: my-app-config
data:
  DATABASE_URL: "postgres://user:password@db:5432/mydb"
  APP_ENV: "production

2. Secrets:
Purpose: Store sensitive information such as passwords, OAuth tokens, and SSH keys.
Use Cases:
Manage sensitive data that needs to be injected into pods.
Avoid exposing sensitive information in your application code or ConfigMaps.


Secrets are similar to ConfigMaps but are specifically designed to store sensitive data, like passwords, API tokens, or SSH keys. Secrets data is base64 encoded but still requires care in handling.
●	Use case: You want to securely store sensitive information, such as a database password or API key.

RBAC
Purpose: Manage who can access Kubernetes resources and what actions they can perform.
Components:
- Role: Defines a set of permissions within a namespace.
ClusterRole: Defines a set of permissions across the entire cluster.
- RoleBinding: Grants the permissions defined in a Role to a user or group within a specific namespace.
ClusterRoleBinding: Grants the permissions defined in a ClusterRole to a user or group across the entire cluster.
