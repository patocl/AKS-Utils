# Kubernetes and minikube

## Minikube overview

If you want more information pleasae visit <https://minikube.sigs.k8s.io>

### What is it?

minikube implements a local Kubernetes cluster on macOS, Linux, and Windows.

minikube’s primary goals are to be the best tool for local Kubernetes application development and to support all Kubernetes features that fit.

minikube runs the latest stable release of Kubernetes, with support for standard Kubernetes features like:

* LoadBalancer - using minikube tunnel
* Multi-cluster - using minikube start -p ```<name>```
* NodePorts - using minikube service
* Persistent Volumes
* Ingress
* RBAC
* Dashboard - minikube dashboard
* Container runtimes - start --container-runtime
* Configure apiserver and kubelet options via command-line flags

As well as developer-friendly features:

* Addons - a marketplace for developers to share configurations for running services on minikube
* GPU support - for machine learning
* Filesystem mounts
* Automatic failure analysis

### Why do I want it?

If you would like to develop Kubernetes applications:

* locally
* offline
* using the latest version of Kubernetes

Then minikube is for you.

* What is it good for? Developing local Kubernetes applications
* What is it not good for? Production Kubernetes deployments
* What is it not yet good for? Environments which do not allow VM’s
* Where should I go next?

## Prerequisites on Windows

* Windows 10 Enterprise, Pro, or Education (system requirements)
* Hyper-V enabled
* An active Hyper-V switch
* 4GB of RAM

## installing on windows

Review this <https://minikube.sigs.k8s.io/docs/start/windows> if need more help.

I used chocolatey in my case

Installing chocolatey on powershell, should be recomendable u start new powershell as administrator

``` powershell
PS> Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

installing minikube

``` powershell
PS> choco install minikube
```

### creating a new switch adapter network on Hyper-V

Run this commands on powershell to create a new network adapter

``` powershell
PS> New-VMSwitch -name ExternalSwitch -NetAdapterName <network-adapter-name> -AllowManagementOS $true
```

Asociate the interface to minikube, if network interface have a name with spaces use "network-adapter-name"

``` powershell
PS> minikube config set hyperv-virtual-switch <network-adapter-name>
```

### Install and start minikube

The first time when you execute the next command could be a bit slowly, and it's could take me 5~7 minutes depend on your system and internet speed, because minikube the first time that run, need to downloads and configure sort of things

``` powershell
PS> minikube start --vm-driver=hyperv
```

output

``` text
* minikube v1.3.1 on Microsoft Windows 10 Pro 10.0.18362 Build 18362
* Creating hyperv VM (CPUs=2, Memory=2000MB, Disk=20000MB) ...
* Preparing Kubernetes v1.15.2 on Docker 18.09.8 ...
* Downloading kubeadm v1.15.2
* Downloading kubelet v1.15.2
* Pulling images ...
* Launching Kubernetes ...
* Waiting for: apiserver proxy etcd scheduler controller dns
* Done! kubectl is now configured to use "minikube"
```

### Verifying the installation minikube

When run the next command and if the installation not give any error, you could see that kubectl it's attached to the minikube

``` powershell
PS>kubectl version
```

Output

``` powershell
Client Version: version.Info{Major:"1", Minor:"15", GitVersion:"v1.15.3", GitCommit:"2d3c76f9091b6bec110a5e63777c332469e0cba2", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:54Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"15", GitVersion:"v1.15.2", GitCommit:"f6278300bebbb750328ac16ee6dd3aa7d3549568", GitTreeState:"clean", BuildDate:"2019-08-05T09:15:22Z", GoVersion:"go1.12.5", Compiler:"gc", Platform:"linux/amd64"}
```

The next command will show all the pods that are running on Kubernetes Services (minikube's magic)

``` powershell
kubectl get po -A
```

output for could be something like that

NAMESPACE | NAME | READY | STATUS | RESTARTS | AGE
----------|------|-------|--------|----------|----
kube-system | coredns-5c98db65d4-88s9b | 1/1 | Running | 0 | 4m28s
kube-system | coredns-5c98db65d4-hs85q | 1/1 | Running | 0 | 4m28s
kube-system | etcd-minikube | 1/1 | Running | 0 | 3m34s
kube-system | kube-addon-manager-minikube | 1/1 | Running | 0 | 3m19s
kube-system | kube-apiserver-minikube | 1/1 | Running | 0 | 3m27s
kube-system | kube-controller-manager-minikube | 1/1 | Running | 0 | 3m16s
kube-system | kube-proxy-57hk6 | 1/1 | Running | 0 | 4m28s
kube-system | kube-scheduler-minikube | 1/1 | Running | 0 | 3m25s
kube-system | storage-provisioner | 1/1 | Running | 0 | 4m22s

### setting enviroments variables

``` powershell
PS> minikube docker-env
```

output

``` powershell
$Env:DOCKER_TLS_VERIFY = "1"
$Env:DOCKER_HOST = "tcp://192.168.0.30:2376"
$Env:DOCKER_CERT_PATH = "C:\Users\patoc\.minikube\certs"
# Run this command to configure your shell:
# & minikube docker-env | Invoke-Expression
PS C:\> & minikube docker-env | Invoke-Expression
```

Run the commented text **powershell & minikube docker-env | Invoke-Expression**

``` powershell
PS> & minikube docker-env | Invoke-Expression
```

note: don't forgot & character :D, after run this command you couldn't see any output

### To start and stop a minikube virtual machine

``` powershell
PS> minikube start
```

``` powershell
PS> & minikube stop
```

### Dealing with minikube and real cluster on cloud

Minikube configure your PC to tun locally, and change the context to be local for any command like kubectl, etc.

To switch between context

Listing the context

``` powershell
PS> kubectl config get-contexts
CURRENT   NAME                        CLUSTER                     AUTHINFO                                                NAMESPACE
          daplatform0101l-mllab-aks   daplatform0101l-mllab-aks   clusterUser_z0euw1ldmrsg054_daplatform0101l-mllab-aks
*         minikube                    minikube                    minikube
```

Switch to other context

``` powershell
PS> config use-context CONTEXT_NAME
```

### A faster shortcut to the standard kubectl commands is to use **kubectx**

You must install package first

``` powershell
PS> choco install kubectx-ps
```

*List contexts: kubectx
    *Equivalent to kubectl config get-contexts
*Switch context (to foo): kubectx foo
    *Equivalent to kubectl config use-context foo

## Unistalling minikube

This will remove the virtual machine, but not delete the minikube app

``` powershell
PS> minikube delete
```

## Some aditional commands

Show dashboard

``` powershell
PS> minikube dashboard
```

Show the external IP associated to minikube

``` powershell
PS> minikube ip
```

Show minikube status

``` powershell
Ps> minikube status
```
