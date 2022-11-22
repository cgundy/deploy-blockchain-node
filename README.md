# deploy-blockchain-node

Used `kompose convert` to generate K8 files from docker-compose.

## Instructions to run Kubernetes
1. Start Kubernetes in Docker desktop
1. Check that Kubernetes is running `kubectl get services`
1. Start the pods 
```
    kubectl apply -f polkadot-deployment.yaml
    kubectl apply -f polkadot-ingress.yaml
    kubectl apply -f polkadot-service.yaml
    kubectl apply -f polkadot-claim0-persistentvolumeclaim.yaml
```
1. Check that service is running `kubectl get services`

Open questons:
- Is there a better way to start up all the Kubernetes pods?
- How to connect each endpoint to the ingress? (I followed [this tutorial](https://devopscube.com/kubernetes-ingress-tutorial/)) Is this even the right approach for setting up an ingress?
- Is each Kubernetes node running its own blockchain or are they somehow synced?
- Unsure how to connect nginx controller to ingress ([this tutorial](https://devopscube.com/setup-ingress-kubernetes-nginx-controller/) looks very complicated.) Can the nginx controller be deployed with Kubernetes as well or is it separate?

Further considerations:
- Use Helm templates (?) as an alternative to K8 manifest files to manage deployments for different environments (see example in `/templates`)
