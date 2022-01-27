---
tags: demo
---

# Sock Shop GitOps Deployment

Sock Shop is a well known Demonstration application that has been used for demoing containerized workloads before Kubernetes was a thing.  


**1.  Fork the GitHub Repo:**

You can reference base repo directly, but then you will need to make sure that your project namespace is "sock shop".  By forking the repo to your own account, you can then make changes to the count of replicas in nthe deployments:
https://github.com/microservices-demo/microservices-demo

**2. Creat Project in Kommander**

You can give it any name you like, but make sure to set the namespace as `sock-shop`


**3. Create Kommander CD Deployment**

Configure a GitOps Deployment with the following variables.  All Others can be left Blank
* ID: `Whatever You Want`
* URL: `https://github.com/yourUserID/microservices-demo`
* Brach: `master`
* Path:  `/deploy/kubernetes/mannifests`
![](https://i.imgur.com/FOb2tl9.png)


**4. View Workload Deployment**

Go to the Kubernetes dashboard for the the specific cluster
```
NAME                            READY   STATUS    RESTARTS   AGE
carts-b4d4ffb5c-c2ntj           1/1     Running   0          17m
carts-db-6c6c68b747-dsrwk       1/1     Running   0          17m
catalogue-759cc6b86-xks7p       1/1     Running   0          17m
catalogue-db-96f6f6b4c-2rp4r    1/1     Running   0          17m
front-end-5c89db9f57-scwgt      1/1     Running   0          17m
orders-7664c64d75-9rswj         1/1     Running   0          17m
orders-db-659949975f-nw2bf      1/1     Running   0          17m
payment-7bcdbf45c9-9gbhx        1/1     Running   0          17m
queue-master-5f6d6d4796-844mr   1/1     Running   0          17m
rabbitmq-5bcbb547d7-pkjff       2/2     Running   0          17m
session-db-7cf97f8d4f-44wwk     1/1     Running   0          17m
shipping-7f7999ffb7-xc9sl       1/1     Running   0          17m
user-68df64db9c-92mzx           1/1     Running   0          17m
user-db-6df7444fc-q2tr9         1/1     Running   0          17m
```


**5. Modify Deploymet**
* Modify the one of the deployment yamls (front-end)
* watch as FLUX Reconciles the deployment.
* This could take 5 minutes for the flux deployment to happen


**TO BE DONE**
* Expose the Front-End through Traeffik instead of the default nodeport
