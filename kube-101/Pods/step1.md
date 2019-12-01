**Namespaces** in Kubernetes provide us with the ability to isolate Pods into seperate workloads. This gives us many capabilities, such as being able to set up resourse constraints on workloads and establishing clear security boundaries. For example, we could leverage Namespaces to provide development environments to multiple product teams within the same physical Kubernetes cluster.

## Discover Namespaces

Let's observe our custers namespaces:

`kubectl get namespace`{{execute}}

By default in Kubernetes 1.14 onwards, there are 4 namespaces provisioned with every new cluster. These namespaces can be seen in the output of the above command and in the diagram below :

![alt text](https://raw.githubusercontent.com/jameswhinn/katalabs/master/assets/namespaces.png "Default namespaces")

(**Note** In Kubernetes 1.13 the kube-node-lease namespace will exist only if the NodeLease feature gate is enabled)