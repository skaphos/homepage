---
title: "Tropis"
weight: 45
portfolio: "Skaphos Platform"
tagline: "Pre-provisioned cluster trust with custody-safe key handling"
status: "Proposed"
statusClass: "status-proposed"
summary: "Tropis pre-provisions kubeadm PKI, auxiliary CAs, and OIDC trust material into pluggable custody backends so cluster bootstrap is fully declarative."
module: "github.com/skaphos/tropis"
---

Tropis pre-provisions Kubernetes cluster trust material — the kubeadm PKI stack, auxiliary client CAs such as break-glass CAs, and OIDC discovery documents for workload identity federation — into pluggable custody backends, so clusters bootstrap declaratively with zero node-to-provisioner secret flow.

The name is the Greek τρόπις — the keel, the first timber laid, on which everything else is built.

## The custody contract

- No private key is ever a Terraform state attribute; resources expose only public material.
- Exported mode generates keys in memory and writes them directly to the backend, for keys nodes must hold.
- Resident mode creates keys non-exportable inside the backend; every signature is a remote, individually audited backend operation.
- Azure Key Vault first, with AWS, GCP, and HashiCorp Vault backends planned.

## Planned components

- Go library for PKI generation, kubeadm artifact assembly, and remote signing.
- Terraform provider whose state schema carries public material only.
- CLI for operational certificate minting, such as short-TTL break-glass client certificates.

## Design boundary

Tropis is independently useful to anyone running kubeadm on Terraform. Meridian uses the same library to seed Cluster API trust secrets from the same backends, but Tropis has no dependency on Meridian.
