# Azure Key Vault To Kubernetes

## Overview

This project offer two components for handling Azure Key Vault Secrets in Kubernetes:

Azure Key Vault Controller
Azure Key Vault Env Injector
The Azure Key Vault Controller (Controller for short) is for synchronizing Secrets, Certificates and Keys from Azure Key Vault to native Secret's in Kubernetes.

The Azure Key Vault Env Injector (Env Injector for short) is a Kubernetes Mutating Webhook that transparently injects Azure Key Vault secrets as environment variables into programs running in containers, without touching disk or in any other way expose the actual secret content outside the program.

The motivation behind this project was:

Avoid a direct program dependency on Azure Key Vault for getting secrets, and adhere to the 12 Factor App principle for configuration (https://12factor.net/config)
Make it simple, secure and low risk to transfer Azure Key Vault secrets into Kubernetes as native Kubernetes secrets
Securely and transparently be able to inject Azure Key Vault secrets as environment variables to applications, without having to use native Kubernetes secrets
All of these goals are met.

If you want more info related to this Controller review <https://github.com/patocl/azure-key-vault-to-kubernetes>

Note

hmmm.... **By default the Controller auto sync secrets every 10 minutes (configurable) and depending on how many secrets are synchronized can cause extra usage costs of Azure Key Vault.**
