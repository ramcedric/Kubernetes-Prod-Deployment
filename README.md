# Kubernetes-Prod-Deployment

This repository contains the Kubernetes deployment YAML files for deploying an Nginx application in various environments (development, staging, production).

## Files

- **`app-deployment-template.yaml`**: A generic deployment template that can be used for different environments.
- **`prod-deployment.yaml`**: Production deployment configuration with 3 replicas.

## Usage

### Step 1: Create the Kubernetes Namespace

Before applying any deployment, make sure the relevant namespace exists. For **production**, create the namespace using:

```bash
kubectl create namespace production
```

### Step 2: Deploy the application

```bash
kubectl apply -f prod-deployment.yaml
```
### Step 3: Expose the application

```bash
kubectl expose deployment nginx-app \
  --type=NodePort \
  --name=nginx-service \
  --port=80 \
  --target-port=80 \
  --namespace=production
```

### Step 4: Verify the Deployment

```bash
kubectl get pods -n production
kubectl get svc -n production
```
```bash
kubectl exec -it <pod-name> -n production -- /bin/bash
echo $APP_ENV
echo $DB_PASSWORD
```


### Summary

This `README.md` file provides:
- Instructions on setting up and deploying the Nginx app in the **production** environment.
