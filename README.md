# Homelab ArgoCD Config

The Applications ArgoCD deploys to the homelab k3s cluster.

## GitOps config for the homelab k3s cluster

ArgoCD pulls this repo from its Gitea mirror. The root app, installed by OpenTofu in `homelab-proxmox`, deploys every Application in `argocd/applications/`.

### Applications

- `metallb`: MetalLB in L2 mode
- `metallb-config`: the LoadBalancer address pool (`192.168.1.10`–`.49`)
- `loki-stack`: Loki, Promtail and Prometheus (`.15`)
- `grafana`: Grafana (`.14`), with its admin login from the `grafana-admin` Secret
- `coredns-custom`: sends CoreDNS lookups for `homelab.local` straight to bind9 (`192.168.1.153`)
- `nginx-web-server`: Nginx test app (`.12`)
- `k8status`: service status dashboard (`.11`)

### Pre-commit

Hooks are in `.pre-commit-config.yaml`. Set up once with `pre-commit install`.
