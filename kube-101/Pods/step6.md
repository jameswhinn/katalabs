Now let's give it a go without any command prompts!

First we need a namespace:

1. Create namespace: ```lab1```

Now create a pod with the following specification:

1. Pod name == ```kungfujenkins```
2. Pod namespace == ```lab1```
3. Pod must have the following labels ```power=10```, ```agilty=9```, ```speed=3```
4. Use the latest version of official Jenkins image from docker hub
5. ContainerPort == ```8080```
6. Validate deployment
7. Clean up