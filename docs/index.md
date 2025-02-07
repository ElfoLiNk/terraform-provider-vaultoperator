---
page_title: "Provider: vaultoperator"
description: |-
  
---

# vaultoperator Provider

This Provider gives access to the `vault operator` operations, although currently only `vault operator init` is implemented.
If you are using HTTPS with a self-signed or untrusted certificate, you can run `export VAULT_SKIP_VERIFY=true` and have the certificate verification errors ignored.

**NOTE! This will put the root token and unseal/recovery keys into your state so use with caution!**


## Example Usage

```terraform
terraform {
  required_providers {
    vaultoperator = {
      version = "0.1.8"
      source  = "rickardgranberg/vaultoperator"
    }
  }
}

provider "vaultoperator" {
  # example configuration here
  vault_url = "http://vault:8200"
  kube_config {
    path       = "~/.kube/config"
    namespace  = "vault"
    service    = "vault"
    localPort  = "8200"
    remotePort = "8200"
  }
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Optional

- **kube_config** (Block List) (see [below for nested schema](#nestedblock--kube_config))
- **request_headers** (Map of String)
- **vault_addr** (String) Vault instance URL
- **vault_url** (String, Deprecated) Vault instance URL

<a id="nestedblock--kube_config"></a>
### Nested Schema for `kube_config`

Optional:

- **local_port** (String) Local forward port
- **namespace** (String) Kubernetes namespace where HC Vault is run
- **path** (String) Full path to a Kubernetes config
- **remote_port** (String) Remote service port to forward
- **service** (String) Kubernetes service name of Vault
