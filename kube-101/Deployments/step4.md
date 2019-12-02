In this section we will scale deployment up to three replicas. 


First let's check the existing deployment:

``kubectl get deployment nginx``{{execute}}

You can output similar to following.

```
NAME    READY   UP-TO-DATE   AVAILABLE   AGE
nginx   1/1     1            1           12
```

The output shows that the deployment created has only one replica.

Now we want to scale our deployment to have 3 replicas. 

``kubectl scale deployment nginx --replicas=3``{{execute}} 

We should see output telling us ``` deployment.extensions/nginx scaled ``` indicating that scaling done successfully.

We can recheck the scaled deployment: 

``kubectl get deployment nginx``{{execute}}

You can see output similar to following.

```
NAME    READY   UP-TO-DATE   AVAILABLE   AGE
nginx   3/3     3            3           12m
```

The output shows that our deployment is scaled to 3 replicas successfully and all of them are ready to serve.

