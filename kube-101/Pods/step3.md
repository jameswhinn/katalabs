## Kubernetes API Reference

Every Kubernetes object has an API specification and this specification can be written it down in a YAML file.

In this exercise, we will create our first Pod. First of all, we are going to check the [Kubernetes API](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.15/#pod-v1-core) to check the Pod's full specification.

Kubernetes API Reference provides us with all the specifics to configure Kubernetes objects by yaml files.

## Create Pod

Let's take a look at our pod manifest:

``cat manifests/pod.yaml``{{execute}}

As you can see, our pod manifest describes a **webserver** pod consisting of a nginx container image. This image if the official nginx image from Docker Hub public registry.

By using the kubectl cli tool, we authenticate to the Kubernetes API and apply our Pod specification to the Kubernetes Cluster:

``kubectl apply -f manifests/pod.yaml``{{execute}}

Now let's validate our pod deployment. To do this we again query the Kubernetes API:

``kubectl get pods``{{execute}}

Notice that the **webserver** pod is running in the default namespace. This is because we didn't set any namespace in our specification.

##Delete Pod

We can delete pods by using a YAML file or a single command:

``kubectl delete -f manifests/pod.yaml``{{execute}}

or

``kubectl delete pod webserver``{{execute}}

Let's confirm that our **webserver** pod was removed

``kubectl get pods``{{execute}}