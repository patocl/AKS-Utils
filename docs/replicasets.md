# Replicasets on Kubernetes

## Whats is a Replicaset

Pods are the smallest deployable units of computing that can be created and managed in Kubernetes.

In a pod can contain 1 or multilpes containers, I wan't to enter on too much theory! :D

if you need review more about it please visit <https://kubernetes.io/docs/concepts/workloads/pods/pod/>

## Creating a Replicaset

This are described on YAML file for example, let's view the content of a minimal pod structure
Remember that Pods are not visible outside the Kubernetes! We will expose later

### Let's to create the first Replicaset

``` yaml
apiVersion: v1
kind: Pod
metadata:
  name: webapp
  labels:
    app: webapp
spec:
  containers:
  - name: webapp
    image: richardchesterwood/k8s-fleetman-webapp-angular:release0
```

Save this file like my-first-replicaset.yaml

### Let's to install the replicaset

``` powershell
PS> kubectl apply -f my-first-replicaset.yaml
```

### Review the pod status

``` powershell
PS> kubectl get all
NAME | READY | STATUS | RESTARTS | AGE
------- | ------- | ------- | ------- | -------
pod/hello-world | 0/1 | Completed | 0 | 15s

NAME | TYPE | CLUSTER-IP | EXTERNAL-IP | PORT(S) | AGE
-----|------|------------|-------------|---------|----
pod/webapp | 1/1 | Running | 0 | 4m48s

### Check the endpoint of minikube

``` powershell
PS> minikube ip
192.168.0.30
```

``` powershell
PS> kubectl describe webapp

```

### Running a command inside a Pod

``` powershell
PS D:\Projectos\minikube> kubectl exec webapp ls
bin
dev
etc
home
lib
media
mnt
proc
root
run
sbin
srv
sys
tmp
usr
var
```

``` powershell
PS D:\Projectos\minikube> kubectl describe pod webapp
Name:         webapp
Namespace:    default
Priority:     0
Node:         minikube/192.168.0.30
Start Time:   Fri, 23 Aug 2019 22:57:36 +0200
Labels:       <none>
Annotations:  kubectl.kubernetes.io/last-applied-configuration:
                {"apiVersion":"v1","kind":"Pod","metadata":{"annotations":{},"name":"webapp","namespace":"default"},"spec":{"containers":[{"image":"richar...
Status:       Running
IP:           172.17.0.4
Containers:
  webapp:
    Container ID:   docker://c18ff8273a93b8ac20e5855d36e9134d26f46af3dbd5445c943a1b13150f2f69
    Image:          richardchesterwood/k8s-fleetman-webapp-angular:release0
    Image ID:       docker-pullable://richardchesterwood/k8s-fleetman-webapp-angular@sha256:9b98fec20772bd1d7d4c9085048f28af35b31ad3a7b7d3ba395fb512c5c359e6
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Fri, 23 Aug 2019 22:57:41 +0200
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-hdgpp (ro)
Conditions:
  Type              Status
  Initialized       True
  Ready             True
  ContainersReady   True
  PodScheduled      True
Volumes:
  default-token-hdgpp:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  default-token-hdgpp
    Optional:    false
QoS Class:       BestEffort
Node-Selectors:  <none>
Tolerations:     node.kubernetes.io/not-ready:NoExecute for 300s
                 node.kubernetes.io/unreachable:NoExecute for 300s
Events:
  Type    Reason     Age    From               Message
  ----    ------     ----   ----               -------
  Normal  Scheduled  2m37s  default-scheduler  Successfully assigned default/webapp to minikube
  Normal  Pulling    2m36s  kubelet, minikube  Pulling image "richardchesterwood/k8s-fleetman-webapp-angular:release0"
  Normal  Pulled     2m33s  kubelet, minikube  Successfully pulled image "richardchesterwood/k8s-fleetman-webapp-angular:release0"
  Normal  Created    2m32s  kubelet, minikube  Created container webapp
  Normal  Started    2m32s  kubelet, minikube  Started container webapp
```

### Executing commands inside Pod

``` powershell
PS>kubectl -it exec webapp sh
bin    dev    etc    home   lib    media  mnt    proc   root   run    sbin   srv    sys    tmp    usr    var
/ # wget
BusyBox v1.27.2 (2017-12-12 10:41:50 GMT) multi-call binary.

Usage: wget [-c|--continue] [--spider] [-q|--quiet] [-O|--output-document FILE]
        [--header 'header: value'] [-Y|--proxy on/off] [-P DIR]
        [-S|--server-response] [-U|--user-agent AGENT] [-T SEC] URL...

Retrieve files via HTTP or FTP

        --spider        Only check URL existence: $? is 0 if exists
        -c              Continue retrieval of aborted transfer
        -q              Quiet
        -P DIR          Save to DIR (default .)
        -S              Show server response
        -T SEC          Network read timeout is SEC seconds
        -O FILE         Save to FILE ('-' for stdout)
        -U STR          Use STR for User-Agent header
        -Y on/off       Use proxy
/ # wget http://localhost
Connecting to localhost (127.0.0.1:80)
index.html           100% |***********************************************************************|   585   0:00:00 ETA
/ # exit
PS>

