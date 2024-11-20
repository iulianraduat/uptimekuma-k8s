# uptimekuma-k8s

Uptime Kuma as k8s deployment

## Install

In the folder were you have all .yaml files run the following command:

```
kubectl apply -f uptimekuma-deployment.yaml
```

If it does not work for minikube then try:

```
minikube kubectl apply -f uptimekuma-deployment.yaml
```

If it does not work for microk8s then try:

```
microk8s kubectl apply -f uptimekuma-deployment.yaml
```

You should see in the `default` namespace defined for kubernetes all the new objects.
The corresponding service is called `uptimekuma`.

If you want to use it in a different namespace then just add "-n &lt;namespace&gt;" as argument to kubectl call.

You need to use a proxy in front of it (like nginx) to redirect to the exposed port on k8s node.
To find the mapped ports for port 80 just check the "Internal Endpoints" of the service "uptimekuma"
or run `kubectl get svc` from the shell of the server running the cluster.
