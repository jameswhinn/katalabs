## Create a Deployment 

In this step we will create a new deployment. We will use the official **nginx** web server image available in Docker Hub.

``kubectl create deployment nginx --image=nginx``{{execute}}

Let's verify our deployment was created successfully:

``kubectl get deployments``{{execute}}

If it is successfully created, we should get output similar to below:

```
master $ kubectl get deployments
NAME      DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
nginx     1         1         1            1           10s
```

Let's dig deeper into the deployment we created:

``kubectl describe deployment nginx``{{execute}}

The ```describe deployment``` command retrieves the details of our newly created deployment. It shows details like name, namespace, selectors and many others.