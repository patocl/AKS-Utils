# Services in Kubertenes

## Whats is a Service

An abstract way to expose an application running on a set of Pods as a network service.

if you need review more about it please visit <https://kubernetes.io/docs/concepts/services-networking/service/>

it's very importan the label and selector match same on pod and service properly
For example label for pod it's app:webapp service selector is app:webapp, with that Kubernetes can match a service with a pod.

Minikube Ip it's the IP where services could be called, for this example must to include the por 30080

minikube has a restriction, and just can run services from port 30000 or higher

## Creating a Service

This are described on YAML file like a Pod, for example, let's view the content of a minimal service structure

### Let's to create the first service

``` yaml
apiVersion: v1
kind: Service
metadata:
  name: fleetman-webapp

spec:
  # This defines which pods are going to be represented by this Service
  # The service becomes a network endpoint for either other services
  # or maybe external users to connect to (eg browser)
  selector:
    app: webapp
    release: "0-5"

  ports:
    - name: http
      port: 80
      nodePort: 30080

  type: NodePort
```

Save this file webapp-service.yaml

### Let's to install the service

``` powershell
PS> kubectl apply -f webapp-service.yaml
```

### Save this file like webapp-service.yaml

``` powershell
PS> kubectl get all
PS D:\Projectos\minikube> kubectl get all
NAME              READY   STATUS      RESTARTS   AGE
pod/webapp        1/1     Running     0          31m

NAME                      TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
service/fleetman-webapp   NodePort    10.107.133.239   <none>        80:30080/TCP   5m4s
service/kubernetes        ClusterIP   10.96.0.1        <none>        443/TCP        159m
```

### Identifying the Ip for our Kubernetes Cluster

in my case is

``` powershell
PS D:\Projectos\minikube> minikube ip
192.168.0.30
```

### Checking Service on any Browser

Open any browser and request in my case and navite to <http://192.168.0.30:30080>
