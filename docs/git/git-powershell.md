# Git and Powershell + Azure DevOps

This command should be used on Powerrshell, so open it and run the next commands.

If you want to learn more about Powershell Extensions  looks on <https://docs.microsoft.com/en-us/rest/api/azure/devops/extensionmanagement/installed%20extensions?view=azure-devops-rest-5.0>

## Looking the extension installed

``` bash
az extension list
```

## Installing the azure-devops extension

``` bash
az extension add --name azure-devops
```

## Login on repositories of VSTS

``` bash
az devops login
```

## Setting the default organization URL

``` bash
az devops configure --defaults organization=https://<organization_name>.visualstudio.com
```

## Listing the Repos List

``` bash
az repos list --project=<project_name>
```

## Clonning all repositories on local

### To use SSH Url

``` bash
(az repos list --project=<project_name> -o json | ConvertFrom-Json) | %{ git clone $_.sshUrl }
```

### To use Http Url

``` bash
(az repos list --project=<project_name> -o json | ConvertFrom-Json) | %{ git clone $_.webUrl }
```
