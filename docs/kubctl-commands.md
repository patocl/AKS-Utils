# kubectl Commands

Kubectl is a command line interface for running commands against Kubernetes clusters. kubectl looks for a file named config in the $HOME/.kube directory. You can specify other kubeconfig files by setting the KUBECONFIG environment variable or by setting the --kubeconfig flag.

kubectl from Kubernetes docs Page <https://kubernetes.io/docs/reference/kubectl/overview/>

## Useful links to get cheat sheets

- kubectl Cheat Sheet <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>
- Nice Pdf 1 page <https://documentcloud.adobe.com/link/track?uri=urn%3Aaaid%3Ascds%3AUS%3A5f7379e6-8331-4b90-ac64-691190c06ad3>

## Install kubectl on windows

Exists alot places that explain this tool for Kubernetes Services, so I don't want t repeat myself, if you want to know how install see this video please
<https://www.youtube.com/watch?v=5-LHcpkRA58> that's explain how to install it and Minikube too :D

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
