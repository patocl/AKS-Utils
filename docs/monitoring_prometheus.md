# Monitoring Kubernetes with Prometheus and Grafana

# What is Prometheus?

Prometheus is an open-source systems monitoring and alerting toolkit originally built at SoundCloud. Since its inception in 2012, many companies and organizations have adopted Prometheus, and the project has a very active developer and user community. It is now a standalone open source project and maintained independently of any company. To emphasize this, and to clarify the project's governance structure, Prometheus joined the Cloud Native Computing Foundation in 2016 as the second hosted project, after Kubernetes.

visit <https://prometheus.io/docs/introduction/overview/>

# What is Grafana?

It's a the analytics platform for all your metrics.

Grafana allows you to query, visualize, alert on and understand your metrics no matter where they are stored. Create, explore, and share dashboards with your team and foster a data driven culture.

visit <https://grafana.com>

## Choosing the charts

Prometheus and Grafana could be installed with some charts and helm
<https://github.com/helm/charts/tree/master/stable>

A nice chart chart that I found it's **prometheus-operator** that have all the componentes and perfom the installation of Prometheus and Grafana all in one, an totally configured.

review <https://github.com/helm/charts/tree/master/stable/prometheus-operator>

## Installing Prometheus and Grafana

``` powershell
PS> helm install --name monitoring --namespace monitoring stable/prometheus-operator
NAME:   monitoring
LAST DEPLOYED: Sat Aug 24 01:42:48 2019
NAMESPACE: monitoring
STATUS: DEPLOYED

RESOURCES:
==> v1/Alertmanager
NAME                                     AGE
monitoring-prometheus-oper-alertmanager  51s

==> v1/ClusterRole
NAME                                       AGE
monitoring-grafana-clusterrole             51s
monitoring-prometheus-oper-alertmanager    51s
monitoring-prometheus-oper-operator        51s
monitoring-prometheus-oper-operator-psp    51s
monitoring-prometheus-oper-prometheus      51s
monitoring-prometheus-oper-prometheus-psp  51s
psp-monitoring-kube-state-metrics          51s

==> v1/ClusterRoleBinding
NAME                                       AGE
monitoring-grafana-clusterrolebinding      51s
monitoring-prometheus-oper-alertmanager    51s
monitoring-prometheus-oper-operator        51s
monitoring-prometheus-oper-operator-psp    51s
monitoring-prometheus-oper-prometheus      51s
monitoring-prometheus-oper-prometheus-psp  51s
psp-monitoring-kube-state-metrics          51s

==> v1/ConfigMap
NAME                                                          DATA  AGE
monitoring-grafana                                            1     52s
monitoring-grafana-config-dashboards                          1     52s
monitoring-grafana-test                                       1     52s
monitoring-prometheus-oper-apiserver                          1     52s
monitoring-prometheus-oper-controller-manager                 1     52s
monitoring-prometheus-oper-etcd                               1     52s
monitoring-prometheus-oper-grafana-datasource                 1     52s
monitoring-prometheus-oper-k8s-cluster-rsrc-use               1     52s
monitoring-prometheus-oper-k8s-coredns                        1     52s
monitoring-prometheus-oper-k8s-node-rsrc-use                  1     52s
monitoring-prometheus-oper-k8s-resources-cluster              1     52s
monitoring-prometheus-oper-k8s-resources-namespace            1     52s
monitoring-prometheus-oper-k8s-resources-pod                  1     52s
monitoring-prometheus-oper-k8s-resources-workload             1     52s
monitoring-prometheus-oper-k8s-resources-workloads-namespace  1     52s
monitoring-prometheus-oper-kubelet                            1     52s
monitoring-prometheus-oper-nodes                              1     52s
monitoring-prometheus-oper-persistentvolumesusage             1     52s
monitoring-prometheus-oper-pods                               1     52s
monitoring-prometheus-oper-prometheus                         1     52s
monitoring-prometheus-oper-prometheus-remote-write            1     52s
monitoring-prometheus-oper-proxy                              1     52s
monitoring-prometheus-oper-scheduler                          1     52s
monitoring-prometheus-oper-statefulset                        1     52s

==> v1/Deployment
NAME                                 READY  UP-TO-DATE  AVAILABLE  AGE
monitoring-kube-state-metrics        1/1    1           1          51s
monitoring-prometheus-oper-operator  1/1    1           1          51s

==> v1/Pod(related)
NAME                                                 READY  STATUS   RESTARTS  AGE
monitoring-grafana-7d886886db-ljs7m                  2/2    Running  0         51s
monitoring-kube-state-metrics-7575c9c84f-h4jcr       1/1    Running  0         51s
monitoring-prometheus-node-exporter-mrn8g            1/1    Running  0         51s
monitoring-prometheus-oper-operator-c5f4d4875-kqkhl  2/2    Running  0         51s

==> v1/Prometheus
NAME                                   AGE
monitoring-prometheus-oper-prometheus  51s

==> v1/PrometheusRule
NAME                                                             AGE
monitoring-prometheus-oper-alertmanager.rules                    50s
monitoring-prometheus-oper-etcd                                  49s
monitoring-prometheus-oper-general.rules                         48s
monitoring-prometheus-oper-k8s.rules                             47s
monitoring-prometheus-oper-kube-apiserver.rules                  46s
monitoring-prometheus-oper-kube-prometheus-node-alerting.rules   45s
monitoring-prometheus-oper-kube-prometheus-node-recording.rules  44s
monitoring-prometheus-oper-kube-scheduler.rules                  43s
monitoring-prometheus-oper-kubernetes-absent                     42s
monitoring-prometheus-oper-kubernetes-apps                       41s
monitoring-prometheus-oper-kubernetes-resources                  40s
monitoring-prometheus-oper-kubernetes-storage                    39s
monitoring-prometheus-oper-kubernetes-system                     38s
monitoring-prometheus-oper-node-network                          37s
monitoring-prometheus-oper-node-time                             36s
monitoring-prometheus-oper-node.rules                            35s
monitoring-prometheus-oper-prometheus                            32s
monitoring-prometheus-oper-prometheus-operator                   33s

==> v1/Role
NAME                     AGE
monitoring-grafana-test  51s

==> v1/RoleBinding
NAME                     AGE
monitoring-grafana-test  51s

==> v1/Secret
NAME                                                  TYPE    DATA  AGE
alertmanager-monitoring-prometheus-oper-alertmanager  Opaque  1     52s
monitoring-grafana                                    Opaque  3     52s

==> v1/Service
NAME                                                TYPE       CLUSTER-IP      EXTERNAL-IP  PORT(S)           AGE
monitoring-grafana                                  ClusterIP  10.103.28.235   <none>       80/TCP            51s
monitoring-kube-state-metrics                       ClusterIP  10.109.29.211   <none>       8080/TCP          51s
monitoring-prometheus-node-exporter                 ClusterIP  10.103.241.224  <none>       9100/TCP          51s
monitoring-prometheus-oper-alertmanager             ClusterIP  10.101.244.198  <none>       9093/TCP          51s
monitoring-prometheus-oper-coredns                  ClusterIP  None            <none>       9153/TCP          51s
monitoring-prometheus-oper-kube-controller-manager  ClusterIP  None            <none>       10252/TCP         51s
monitoring-prometheus-oper-kube-etcd                ClusterIP  None            <none>       2379/TCP          51s
monitoring-prometheus-oper-kube-proxy               ClusterIP  None            <none>       10249/TCP         51s
monitoring-prometheus-oper-kube-scheduler           ClusterIP  None            <none>       10251/TCP         51s
monitoring-prometheus-oper-operator                 ClusterIP  10.100.11.96    <none>       8080/TCP,443/TCP  51s
monitoring-prometheus-oper-prometheus               ClusterIP  10.111.244.62   <none>       9090/TCP          51s

==> v1/ServiceAccount
NAME                                     SECRETS  AGE
monitoring-grafana                       1        52s
monitoring-grafana-test                  1        52s
monitoring-kube-state-metrics            1        52s
monitoring-prometheus-node-exporter      1        52s
monitoring-prometheus-oper-alertmanager  1        52s
monitoring-prometheus-oper-operator      1        52s
monitoring-prometheus-oper-prometheus    1        51s

==> v1/ServiceMonitor
NAME                                                AGE
monitoring-prometheus-oper-alertmanager             32s
monitoring-prometheus-oper-apiserver                32s
monitoring-prometheus-oper-coredns                  32s
monitoring-prometheus-oper-grafana                  32s
monitoring-prometheus-oper-kube-controller-manager  32s
monitoring-prometheus-oper-kube-etcd                32s
monitoring-prometheus-oper-kube-proxy               32s
monitoring-prometheus-oper-kube-scheduler           32s
monitoring-prometheus-oper-kube-state-metrics       32s
monitoring-prometheus-oper-kubelet                  32s
monitoring-prometheus-oper-node-exporter            32s
monitoring-prometheus-oper-operator                 32s
monitoring-prometheus-oper-prometheus               32s

==> v1beta1/ClusterRole
NAME                                     AGE
monitoring-kube-state-metrics            51s
psp-monitoring-prometheus-node-exporter  51s

==> v1beta1/ClusterRoleBinding
NAME                                     AGE
monitoring-kube-state-metrics            51s
psp-monitoring-prometheus-node-exporter  51s

==> v1beta1/DaemonSet
NAME                                 DESIRED  CURRENT  READY  UP-TO-DATE  AVAILABLE  NODE SELECTOR  AGE
monitoring-prometheus-node-exporter  1        1        1      1           1          <none>         51s

==> v1beta1/MutatingWebhookConfiguration
NAME                                  AGE
monitoring-prometheus-oper-admission  51s

==> v1beta1/PodSecurityPolicy
NAME                                     PRIV   CAPS      SELINUX           RUNASUSER  FSGROUP    SUPGROUP  READONLYROOTFS  VOLUMES
monitoring-grafana                       false  RunAsAny  RunAsAny          RunAsAny   RunAsAny   false     configMap,emptyDir,projected,secret,downwardAPI,persistentVolumeClaim
monitoring-grafana-test                  false  RunAsAny  RunAsAny          RunAsAny   RunAsAny   false     configMap,downwardAPI,emptyDir,projected,secret
monitoring-kube-state-metrics            false  RunAsAny  MustRunAsNonRoot  MustRunAs  MustRunAs  false     secret
monitoring-prometheus-node-exporter      false  RunAsAny  RunAsAny          MustRunAs  MustRunAs  false     configMap,emptyDir,projected,secret,downwardAPI,persistentVolumeClaim,hostPath
monitoring-prometheus-oper-alertmanager  false  RunAsAny  RunAsAny          MustRunAs  MustRunAs  false     configMap,emptyDir,projected,secret,downwardAPI,persistentVolumeClaim
monitoring-prometheus-oper-operator      false  RunAsAny  RunAsAny          MustRunAs  MustRunAs  false     configMap,emptyDir,projected,secret,downwardAPI,persistentVolumeClaim
monitoring-prometheus-oper-prometheus    false  RunAsAny  RunAsAny          MustRunAs  MustRunAs  false     configMap,emptyDir,projected,secret,downwardAPI,persistentVolumeClaim

==> v1beta1/Role
NAME                AGE
monitoring-grafana  51s

==> v1beta1/RoleBinding
NAME                AGE
monitoring-grafana  51s

==> v1beta1/ValidatingWebhookConfiguration
NAME                                  AGE
monitoring-prometheus-oper-admission  32s

==> v1beta2/Deployment
NAME                READY  UP-TO-DATE  AVAILABLE  AGE
monitoring-grafana  1/1    1           1          51s


NOTES:
The Prometheus Operator has been installed. Check its status by running:
  kubectl --namespace monitoring get pods -l "release=monitoring"

Visit https://github.com/coreos/prometheus-operator for instructions on how
to create & configure Alertmanager and Prometheus instances using the Operator.
```

## Postconfiguration
