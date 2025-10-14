# 🏠 Homelab

## Introduction

This repository is home to all the configurations and notes that bring my homelab to life.

The homelab is both a playground and a classroom. As someone aspiring to become a Cloud Native Engineer, it’s where I roll up my sleeves, test new ideas, and push myself to learn by doing. 
Self-hosting my own applications makes the experience even more rewarding—I’m not just running code, I’m responsible for everything from deployment to ongoing maintenance.
That means thinking ahead about backups, staying mindful of security, planning for scalability, and making sure everything is easy to manage. In short, my homelab isn’t just a setup—it’s my personal training ground for building, breaking, and improving.

## Cluster Provisioning, Architecture and Hardware

I use [Talos Linux](https://www.talos.dev/) to set up my machines. I prefer Talos because it is lightweight and minimal, and provides production grade security right out of the box. 

I am currently using a 3 nodes cluster, One Controlplane and two worker nodes.
I plan to add 2 other nodes, one would be a secondary Controlplane for HA, and the other one would be a third worker node.

### Nodes

I use a combination of mini pc's since they are small and cheap to buy when you get them refurbished from a reseller.

LENOVO THINKCENTRE M900 TINY i5-6400T/16GB/240GB SSD

DELL OPTIPLEX 3020 MICRO i3-4160T/8GB/240GB SSD

DELL OPTIPLEX 3020 MICRO i3-4160T/8GB/240GB SSD

## Installed Apps & Tools

### Apps

End User Applications
<table>
    <tr>
        <th>Logo</th>
        <th>Name</th>
        <th>Description</th>
    </tr>
    <tr>
        <td><img width="32" src="https://linkding.link/_astro/logo.DkvM5cgj.svg"></td>
        <td><a href="https://linkding.link/">Linkding</a></td>
        <td>A self-hosted bookmark manager</td>
    </tr>
    <tr>
        <td><img width="32" src="https://avatars.githubusercontent.com/u/122929872?s=48&v=4"></td>
        <td><a href="https://github.com/gethomepage/homepage">Homepage</a></td>
        <td>My customized portal to my homelab & internet</td>
    </tr>
    <tr>
        <td><img width="32" src="https://cdn.jsdelivr.net/gh/homarr-labs/dashboard-icons/svg/postgresql.svg"></td>
        <td><a href="https://github.com/gethomepage/homepage">Pgadmin</a></td>
        <td>A web based administration tool for the PostgreSQL</td>
    </tr>
</table>


### Infrastructure

Everything needed to run my cluster & deploy my applications
<table>
    <tr>
        <th>Logo</th>
        <th>Name</th>
        <th>Description</th>
    </tr>
    <tr>
        <td><img width="32" src="https://cdn.jsdelivr.net/gh/walkxcode/dashboard-icons/svg/cert-manager.svg"></td>
        <td><a href="https://cert-manager.io/">Cert Manager</a></td>
        <td>X.509 certificate management for Kubernetes.</td>
    </tr>
    <tr>
        <td><img width="32" src="https://cdn.jsdelivr.net/gh/homarr-labs/dashboard-icons/svg/cilium.svg"></td>
        <td><a href="https://cilium.io/">Cilium</a></td>
        <td>My CNI of choice. eBPF-based Networking, Observability, Security</td>
    </tr>
    <tr>
        <td><img width="32" src="https://cdn.jsdelivr.net/gh/walkxcode/dashboard-icons/png/cloudflare-zero-trust.png"></td>
        <td><a href="https://developers.cloudflare.com/cloudflare-one/">Cloudflare Zero Trust</a></td>
        <td>A secure way to connect your resources to Cloudflare without a publicly routable IP address.</td>
    </tr>
    <tr>
        <td><img width="32" src="https://www.hashicorp.com/_next/static/media/vault_on-dark.97792f64.svg"></td>
        <td><a href="https://www.hashicorp.com/en/products/vault">HashiCorp Vault</a></td>
        <td>Used for secrets management</td>
    </tr>
    <tr>
        <td><img width="32" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTmugUYJPzZLFhcwNyERJRDRXo7NOdVpcIZmkYoYQD8YiNMcaTr0uNvkmdn82cctyoWBKQ"></td>
        <td><a href="https://external-secrets.io/latest/">External Secrets Operator</a></td>
        <td>Used to sync my secrets from HashiCorp Vault</td>
    </tr>
    <tr>
        <td><img width="32" src="https://cdn.jsdelivr.net/gh/homarr-labs/dashboard-icons/svg/postgresql.svg"></td>
        <td><a href="https://cloudnative-pg.io/">CloudNativePG</a></td>
        <td>Kubernetes operator for running PostgreSQL clusters</td>
    </tr>
    <tr>
        <td><img width="32" src="https://avatars.githubusercontent.com/u/33608853?s=48&v=4"></td>
        <td><a href="https://github.com/emberstack/kubernetes-reflector">Reflector</a></td>
        <td>Monitors secrets  and configmaps changes, and reflect changes to mirror resources in the same or other namespaces.</td>
    </tr>
    <tr>
        <td><img width="32" src="https://cdn.jsdelivr.net/gh/homarr-labs/dashboard-icons/svg/flux-cd.svg"></td>
        <td><a href="https://fluxcd.io/">Flux CD</a></td>
        <td>My GitOps solution of choice.</td>
    </tr>
    <tr>
        <td><img width="32" src="https://cdn.jsdelivr.net/gh/walkxcode/dashboard-icons/svg/grafana.svg"></td>
        <td><a href="https://grafana.com/">Grafana</a></td>
        <td>The open observability platform.</td>
    </tr>
    <tr>
        <td><img width="32" src="https://cdn.jsdelivr.net/gh/walkxcode/dashboard-icons/svg/prometheus.svg"></td>
        <td><a href="https://prometheus.io/">Prometheus</a></td>
        <td>An open-source monitoring system with a dimensional data model, flexible query language, efficient time series database and modern alerting approach.</td>
    </tr>
    <tr>
        <td><img width="32" src="https://piraeus.io/img/logo.png"></td>
        <td><a href="https://piraeus.io/">Piraeus Datastore</a></td>
        <td>Cloud native distributed block storage for Kubernetes</td>
    </tr>
</table>

## Networking

I use [Cilium](https://cilium.io/) as my CNI. I use Cilium LoadBalancer with IPAM to assign IP addresses to my LoadBalancer services and use Cilium as an ingress controller. This way, I don't need to install and maintain a seperate ingress controller like Traefik, or a LoadBlancer like MetalLB, which I used in the past.
