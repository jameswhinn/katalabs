Now we have a running pod in the **team-a** namespace, we are going to update the pod. To do that we need to apply pod-update.yaml.

First let's examine the file:

``cat manifests/update-pod.yaml``{{execute}}

The changes are as follows:

1. Pod labels have been added in the metadata section

2. The container image has been updated in the containers section

3. Pod ports has been added in the containers section

Now apply the changes:

``kubectl apply -f manifests/update-pod.yaml``{{execute}}

## OOPS!!

That didn't work! Why?

The error:

```
The Pod "team-a-webserver" is invalid: spec: Forbidden: pod updates may not change fields other than `spec.containers[*].image`, `spec.initContainers[*].image`, `spec.activeDeadlineSeconds` or `spec.tolerations` (only additions to existing tolerations)
```

Ok, let's review the [Kubernetes API docs](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.15/#container-v1-core) and we can find the following statement in containers ports specification:

![alt text](https://raw.githubusercontent.com/jameswhinn/katalabs/master/assets/apiRef.png "Port Ref")

In Kubernetes, there are some fields which can't be updated. The Kubernetes API Reference advises us of the API restrictions and the exact object specifications which are available.

In order to update those limited settings, we must delete the object and recreate it. We could bypass these situations with the "deployment" object which we will cover in other scenario.

## Update, round two

First let's delete the pod:

``kubectl delete pod team-a-webserver -n team-a``{{execute}}

Then apply the updated yaml file:

``kubectl apply -f manifests/update-pod.yaml``{{execute}}

Now verify it worked:

``kubectl describe pod team-a-webserver -n team-a``{{execute}}

As you can see, our pod is running with the new image, port specification and labels we defined in our file.

## Clean up

Now let's clean up the objects we have created:

**Delete Pod**

``kubectl delete pod team-a-webserver -n team-a``{{execute}}

**Delete Namespace**

``kubectl delete namespace team-a``{{execute}}