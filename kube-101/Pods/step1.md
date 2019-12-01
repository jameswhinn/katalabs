**Namespaces** in Kubernetes provide us with the ability to isolate Pods into seperate workloads. This gives us many capabilities, such as being able to set up resourse constraints on workloads and establishing clear security boundaries. For example, we could leverage Namespaces to provide development environments to multiple product teams within the same physical Kubernetes cluster.

## Discover Namespaces

Let's observe our custers namespaces:

`kubectl get namespace`{{execute}}

By default in Kubernetes 1.14 onwards, there are 4 namespaces provisioned with every new cluster. These namespaces can be seen in the output of the above command and in the diagram below :

![alt text](https://raw.githubusercontent.com/jameswhinn/katalabs/master/assets/namespaces.png "Default namespaces")

(**Note** In Kubernetes 1.13 the kube-node-lease namespace will exist only if the NodeLease feature gate is enabled)

## default

As the name suggests, this is the default namespace created for us when we deploy a Kubernetes cluster. Any object we deploy to the cluster, without explicitly defining a namespace, will be created in the **default* namespace. As we have a newly provisioned cluster, we will have no pods currently scheduled here.

``kubectl get pods -n default``{{execute}}

## kube-system

This namespace houses objects created by Kubernetes which are resposible for the inner workings and magic of Kubernetes.

``kubectl get pods -n kube-system``{{execute}}

Without the pods in this namespace, our cluster would not function.

**NOTE:** When using various cloud providers and managed sevices, you will see various other pods here too. These pods are specific to the providers implementation.

## kube-public

This namespace contains a configmap which contains the [bootstrapping and certificate](https://kubernetes.io/docs/reference/access-authn-authz/bootstrap-tokens/) information of the Kubernetes cluster:

``kubectl get pods -n kube-public``{{execute}}

## kube-node-lease