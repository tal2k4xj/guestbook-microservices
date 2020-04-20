## Guestbook Example

This example shows how to build a simple multi-tier web application using
Kubernetes and Docker. The application consists of a web front end, Redis
master for storage, and replicated set of Redis slaves, all for which we will
create Kubernetes deployments, pods, and services.

There are two versions of this application. Version 1 (in the `v1` directory)
is the simple application itself, while version 2 (in the `v2` directory)
extends the application by adding additional features that leverage the Watson
Tone Analyzer service. It is recommended that if you are new to this example
then you look at just the `v1` version of the application. Other IBM demos
will make use of the `v2` version, such as
[Istio101](https://github.com/IBM/istio101).

Please see the corresponding `README.md` files in each directory for more
information.


### Notes

 * As you read the correspoding `README.md` files, you will see `kubectl` commands that describes deployed resources. The output of these commands can be slightly vary depending on the version of your kubectl.
 * The guestbook applications uses Kubernetes service type `LoadBalancer` to expose the service onto an external IP address. If you are using `Minikube`, keep in mind that no real external load balancer is created. You
 can still access the service with the node port that is assigned to load balancer on `Minikube`.

# Deploy with Docker

## Prerequisite

Install Docker desktop : https://docs.docker.com/install/

Or follow this guide to use Virtualbox: https://itsfoss.com/install-linux-in-virtualbox/

## Lab

```
git clone https://github.com/tal2k4xj/guestbook-microservices.git
```

```
docker build ./guestbook-microservices/v1/guestbook/ -t guestbook-v1
```

```
docker images
```

```
docker run -d -p 3000:3000 guestbook-v1
```

```
docker container ls
```

```
docker build ./guestbook-microservices/v2/guestbook/ -t guestbook-v2
```

```
docker run -d -p 3001:3000 guestbook-v2
```

# Deploy with Kubernetes

## Prerequisite

Register to IBM Cloud: https://ibm.biz/BdqZVG

Get feature code and insert to your IBM Cloud account: http://tlvfeaturecode.mybluemix.net/ (code = israeldev)

Create kubernetes service (Free cluster): https://cloud.ibm.com/kubernetes/catalog/create

## Lab

1) Go to: https://cloud.ibm.com/kubernetes/clusters
2) Find your cluster and click on it
3) Click on the "Actions" at the top right corner
4) Select "Web terminal" and choose to install it
5) Wait a minute and do steps 3 and 4 again
6) Now you are ready to work with kubernetes using online terminal and kubectl
7) Go to this link to start the hands-on workshop: https://github.com/IBM/kube101/tree/master/workshop/Lab1#1-deploy-your-application
