Now we have a running pod in the **team-a** namespace, we are going to update the pod. To do that we need to apply pod-update.yaml.

First let's examine the file:

``cat manifests/update-pod.yaml``{{execute}}

The changes are as follows:

1. Pod labels have been added in the metadata section

2. The container image has been updated in the containers section

3. Pod ports has been added in the containers section

Now apply the changes:

``kubectl apply -f pod-update.yaml``{{execute}}

##OOPS!!

That didn't work! Why?

The error:

```
The Pod "team-a-webserver" is invalid: spec: Forbidden: pod updates may not change fields other than `spec.containers[*].image`, `spec.initContainers[*].image`, `spec.activeDeadlineSeconds` or `spec.tolerations` (only additions to existing tolerations)
```

Ok, let's review the [Kubernetes API docs](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.15/#container-v1-core) and we can find the following statement in containers ports specification:

![alt text](https://raw.githubusercontent.com/jameswhinn/katalabs/master/assets/apiRef.png "Port Ref")