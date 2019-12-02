In the previous section we deployed a pod within the default namespace. In this section we will deploy a webserver pod within the **team-a** namespace we created earlier in this scenario.

Let's take a look at manifests/pod-with-namespace.yaml

``cat manifests/pod-with-namespace.yaml``{{execute}}

You can see we've added an additional piece of metadata declaring the namespace which is to be used for scheduling of the pod. We have specified the **team-a** namespace.

Let's apply the configuration and deploy the pod:

``kubectl apply -f manifests/pod-with-namespace.yaml``{{execute}}

Now verify the pod was deployed to the **team-a** namespace:

``kubectl get pods -n team-a``{{execute}}

Awesome!! The **team-a-webserver** has successfully ben scheduled to the **team-a** namespace.