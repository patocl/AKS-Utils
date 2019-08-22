# kubectl Commands

Kubectl is a command line interface for running commands against Kubernetes clusters. kubectl looks for a file named config in the $HOME/.kube directory. You can specify other kubeconfig files by setting the KUBECONFIG environment variable or by setting the --kubeconfig flag.

kubectl from Kubernetes docs Page <https://kubernetes.io/docs/reference/kubectl/overview/>

## Useful links to get cheat sheets

- kubectl Cheat Sheet <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>
- Nice Pdf 1 page <https://documentcloud.adobe.com/link/track?uri=urn%3Aaaid%3Ascds%3AUS%3A5f7379e6-8331-4b90-ac64-691190c06ad3>

## Install kubectl on windows

Exists alot places that explain this tool for Kubernetes Services, so I don't want t repeat myself, if you want to know how install see this video please
<https://www.youtube.com/watch?v=5-LHcpkRA58> that's explain how to install it and Minikube too :D

Instructions from Microsoft
<https://docs.microsoft.com/en-us/azure/aks/kubernetes-walkthrough#connect-to-the-cluster>

## Connect to the cluster

To manage a Kubernetes cluster, you use kubectl, the Kubernetes command-line client. If you use Azure Cloud Shell, kubectl is already installed. To install kubectl locally, use the az aks install-cli command:

``` bash
>az aks install-cli
```

To configure kubectl to connect to your Kubernetes cluster, use the az aks get-credentials command. This command downloads credentials and configures the Kubernetes CLI to use them.

``` bash
>az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
```

To verify the connection to your cluster, use the kubectl get command to return a list of the cluster nodes.

``` bash
>kubectl get nodes
```

The following example output shows the single node created in the previous steps. Make sure that the status of the node is Ready:

| NAME | STATUS | ROLES | AGE | VERSION
|---|---|---|---|---
| aks-nodepool1-31718369-0 | Ready | agent | 6m44s | v1.12.8

## To deploy an Application

Deploy the application using the kubectl apply command and specify the name of your YAML manifest:

``` bash
kubectl apply -f azure-vote.yml
```

The result of it is

``` bash
deployment "azure-vote-back" created
service "azure-vote-back" created
deployment "azure-vote-front" created
service "azure-vote-front" created
```

## Test the application

When the application runs, a Kubernetes service exposes the application front end to the internet. This process can take a few minutes to complete.

To monitor progress, use the kubectl get service command with the --watch argument.

``` bash
kubectl get service azure-vote-front --watch
```

Output

| NAME | TYPE | CLUSTER-IP | EXTERNAL-IP | PORT(S) | AGE
|---|---|---|---|---|---
| azure-vote-front | LoadBalancer | 10.0.37.27 | ```<pending>``` | 80:30572/TCP | 6s

## Tips

I like to use powershell to use kubectl, so use this command if u want to alias it by a shorten name

``` bash
PS>Set-Alias -Name k Value kubectl
```

Examples of usage

``` bash
PS>k get nodes

PS>k config view

PS> k apply -f ./somepfile.yml

PS>k get pods --all-namespaces
```
