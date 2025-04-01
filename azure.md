# Connecting to Your Azure Kubernetes Cluster

This documentation explains how to connect to your Azure Kubernetes Service (AKS) cluster using the Azure CLI and kubectl.

## 1. Install the Azure CLI

Download and install the Azure CLI for your operating system.  
For detailed instructions, refer to the [Azure CLI installation documentation](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli).

## 2. Log In to Your Microsoft Azure Account

Open your terminal and run the following commands:

### 2.1. Log in with Azure CLI

```bash
az login --al
```

### 2.2. Set Your Azure Subscription
Replace <subscription-id> with your actual subscription ID:

```bash 
az account set --subscription <subscription-id>
```


### 2.3. Get AKS Credentials
Replace <resource-group> with your resource group name and <aks-cluster-name> with your AKS cluster name. The command retrieves the cluster credentials and updates your kubeconfig file:

```bash
az aks get-credentials --resource-group <resource-group> --name <aks-cluster-name> --overwrite-existing
```

### 3. Install kubectl
If you haven't already installed kubectl, you can install it using Homebrew (for macOS):

```bash
brew install kubectl
```

### 4. Verify Your Connection to the Cluster
Check the deployments in a specific namespace. Replace <namespace> with your namespace:

```bash
kubectl get deployments --namespace <namespace>
```

### 5. Debugging and Inspecting Pods
#### 5.1. View Logs from a Pod

Replace <namespace> with your namespace. For example, if your pod name is debug:

```bash
kubectl logs debug -n <namespace>
```

#### 5.2. Describe a Pod for Detailed Information
To get detailed information about a pod (e.g., debug), run:

```bash
kubectl describe pod debug -n <namespace>
```
If you need to describe another pod (for example, one with a name starting with prod), run:

```bash
kubectl describe pod <pod-name> -n <namespace>
```
Replace <pod-name> with the actual pod name.