## Kubernetes API Reference

Every Kubernetes object has an API specification and this specification can be written it down in a YAML file.

In this exercise, we will create our first Pod. First of all, we are going to check the [Kubernetes API](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.15/#pod-v1-core) to check the Pod's full specification.

Kubernetes API Reference provides us with all the specifics to configure Kubernetes objects by yaml files.

## Create Pod

Let's take a look at our pod manifest:

``cat manifests/pod.yaml``{{execute}}

As you can see, our pod manifest describes a **webserver** pod consisting of a nginx container image. This image if the official nginx image from Docker Hub public registry.