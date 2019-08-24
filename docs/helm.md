# Helm the package manager for Kubernetes

## Installing Helm

I used chocolatey to install helm

``` powershell
PS> choco install kubernetes-helm
```

``` powershell
PS> helm version
```

``` powershell
PS> helm init
Creating C:\Users\username\.helm
Creating C:\Users\username\.helm\repository
Creating C:\Users\username\.helm\repository\cache
Creating C:\Users\username\.helm\repository\local
Creating C:\Users\username\.helm\plugins
Creating C:\Users\username\.helm\starters
Creating C:\Users\username\.helm\cache\archive
Creating C:\Users\username\.helm\repository\repositories.yaml
Adding stable repo with URL: https://kubernetes-charts.storage.googleapis.com
Adding local repo with URL: http://127.0.0.1:8879/charts
$HELM_HOME has been configured at C:\Users\patoc\.helm.

Tiller (the Helm server-side component) has been installed into your Kubernetes Cluster.

Please note: by default, Tiller is deployed with an insecure 'allow unauthenticated users' policy.
To prevent this, run `helm init` with the --tiller-tls-verify flag.
For more information on securing your installation see: https://docs.helm.sh/using_helm/#securing-your-helm-installation
```

``` powershell
PS> helm version
Client: &version.Version{SemVer:"v2.14.3", GitCommit:"0e7f3b6637f7af8fcfddb3d2941fcc7cbebb0085", GitTreeState:"clean"}
Server: &version.Version{SemVer:"v2.14.3", GitCommit:"0e7f3b6637f7af8fcfddb3d2941fcc7cbebb0085", GitTreeState:"clean"}
```

``` powershell
PS> helm repo update
Hang tight while we grab the latest from your chart repositories...
...Skip local chart repository
...Successfully got an update from the "stable" chart repository
Update Complete.
```

``` powershell
PS> helm ls
```
