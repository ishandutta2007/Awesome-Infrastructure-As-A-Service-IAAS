# Awesome-Infrastructure-As-A-Service-IAAS

# Top Infrastructure-as-a-Service (IaaS) Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Virtual Machine Provisioning, Cloud Orchestration & Self-Hosted IaaS Platforms*  
**Last updated: October 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Infrastructure-as-a-Service (IaaS)**. These tools provide virtualized compute, storage, and networking resources on demand—either as public cloud services or as self-hosted cloud platforms that let organizations build private and hybrid clouds on their own hardware.

**Examples** include AWS EC2, Google Compute Engine, Microsoft Azure Virtual Machines, Oracle Cloud Infrastructure, DigitalOcean, Hetzner Cloud, OpenStack, Apache CloudStack, Proxmox VE, and OpenNebula (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, avoiding hyperscaler lock-in, and building sovereign cloud infrastructure—ideal for organizations that need data residency, predictable costs, and full control over their virtualization stack. The open-source IaaS landscape is anchored by **OpenStack** (the enterprise standard with Nova as its compute service), **Apache CloudStack** (the mature alternative with a simpler architecture), **Proxmox VE** (the homelab and SMB favorite), and **OpenNebula** (the VMware migration specialist), with **Incus** emerging as the community-governed successor to LXD for system containers and VMs.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[AWS EC2](https://aws.amazon.com/ec2/)**  
  The market-leading public cloud compute service. Broadest instance type selection (general purpose, compute optimized, memory optimized, GPU, ARM Graviton), global region coverage, and deep integration with the AWS ecosystem. Consumption-based pricing with Savings Plans and Spot instances for cost optimization.

- **[Google Compute Engine](https://cloud.google.com/compute)**  
  GCP's VM service with custom machine types, live migration, and sustained use discounts. Tight integration with BigQuery, GKE, and Google's networking infrastructure. Best for GCP-native architectures and workloads benefiting from Google's global network.

- **[Microsoft Azure Virtual Machines](https://azure.microsoft.com/en-us/products/virtual-machines)**  
  Azure's IaaS offering with strong Windows Server and Active Directory integration, hybrid cloud via Azure Arc, and enterprise governance through Azure Policy. Best for organizations already invested in the Microsoft ecosystem.

- **[Oracle Cloud Infrastructure (OCI)](https://www.oracle.com/cloud/)**  
  Oracle's cloud with competitive pricing for compute and strong database integration (Autonomous Database, Exadata). Generous Always Free tier. Best for Oracle database workloads and cost-sensitive general compute.

- **[DigitalOcean Droplets](https://www.digitalocean.com/products/droplets)**  
  Developer-friendly cloud with simple pricing, predictable bandwidth allowances, and a clean UI. Best for small teams, startups, and developers who want straightforward VMs without hyperscaler complexity.

- **[Hetzner Cloud](https://www.hetzner.com/cloud)**  
  European cloud provider with exceptionally low pricing for dedicated-vCPU instances. Data centers in Germany, Finland, and the US. Best for cost-sensitive workloads requiring European data residency.

- **[Vultr](https://www.vultr.com/)**  
  Independent cloud with global region coverage, high-frequency compute options, and bare metal availability. Best for teams seeking an alternative to the hyperscalers with broad geographic reach.

- **[OVHcloud](https://www.ovhcloud.com/)**  
  European cloud provider with dedicated servers, public cloud instances, and private cloud options. Strong on data sovereignty and GDPR compliance. Best for European organizations requiring local infrastructure.

- **[Scaleway](https://www.scaleway.com/)**  
  French cloud provider with GPU instances, ARM-based offerings (Ampere), and bare metal. Best for European teams needing GPU or ARM compute with EU data residency.

## Open-Source GitHub Projects

- **[OpenStack (Nova)](https://github.com/openstack/nova)**  
  **The enterprise IaaS standard.** Nova is the compute service within the broader OpenStack ecosystem, managing VM lifecycle, scheduling, and placement across massive deployments. **OpenStack 2026.1 (Gazpacho)** marks a major architectural shift: Nova's scheduler, API, and metadata services now default to **native threading mode** instead of the legacy eventlet mode, improving concurrency and reliability . The `max_concurrent_builds` default changed from "unlimited" (actually bounded by thread pool) to 1,000 in eventlet mode and 10 native threads in threading mode . **Trade-offs**: significant operational complexity—OpenStack requires expertise across Keystone (identity), Neutron (networking), Cinder (block storage), Glance (images), and more. Best for large enterprises and service providers that need a fully open, API-driven cloud platform and have dedicated platform teams.

- **[Apache CloudStack](https://github.com/apache/cloudstack)**  
  **The mature alternative with simpler operations.** Apache Top-Level Project since 2013, deployed in thousands of organizations . **CloudStack 4.21** (August 2025) added a **CloudStack Extensions Framework** with built-in Proxmox and Hyper-V extensions, **GPU integration with KVM** (technical preview), vTPM support for KVM and VMware, instance lease (automatic stop/deletion), incremental volume snapshots for KVM, and Kubernetes Service (CKS) enhancements . **Strengths**: more opinionated and less fragmented than OpenStack—fewer moving parts, single management server architecture, and a proven track record with service providers. **Trade-offs**: smaller ecosystem and fewer integrations than OpenStack. Best for organizations that want IaaS capabilities without OpenStack's operational weight, especially those with existing Proxmox or VMware infrastructure.

- **[Proxmox VE](https://github.com/proxmox/pve-manager)**  
  **The homelab and SMB favorite.** Open-source virtualization platform combining KVM (VMs) and LXC (containers) with a web-based management interface, built-in backup (via Proxmox Backup Server), high availability, and clustering. **Proxmox VE 9.0** (based on Debian 13) added **VM snapshots on thick-provisioned LVM storages**, HA rules for node and resource affinity, SDN fabrics, and ZFS 2.3.3 with live RAIDZ expansion . **Trade-offs**: clustering is functional but less sophisticated than OpenStack for very large deployments; some enterprise features (like certain backup integrations) require subscriptions. Best for SMBs, homelabs, and organizations that want a capable virtualization platform without cloud-scale complexity.

- **[OpenNebula](https://github.com/OpenNebula/one)**  
  **The VMware migration specialist.** **OpenNebula 7.0 "Phoenix"** (July 2025) was explicitly designed for re-virtualization from VMware, with AI-powered **OneDRS** (a DRS alternative), NetApp iSCSI integration, Veeam backup integration, OVA import, and full backup support for LVM datastores . **AI workload focus**: enhanced PCI passthrough, NVIDIA vGPU support, and a Ray Appliance with vLLM for production inference workloads . **Community Edition** now includes migration packages from 6.10 . **Trade-offs**: smaller ecosystem than OpenStack or CloudStack; some advanced features (NetApp, Veeam) are Enterprise-only. Best for organizations migrating from VMware that want an open-source alternative with strong AI/GPU support and a clear upgrade path.

- **[Incus](https://github.com/lxc/incus)**  
  **The community-governed successor to LXD.** Born from Canonical's 2023 decision to take LXD in-house and relicense it from Apache 2.0 to AGPLv3, Incus is a direct fork led by the original LXD maintainers under the Linux Containers project . **Apache 2.0 licensed**—preserving the permissive licensing that made LXD popular . Manages both system containers and QEMU-based VMs through a unified REST API and CLI. **Strengths**: distribution-agnostic (packaged in Debian, Fedora, Arch, Alpine), native OCI container image support, OpenFGA/OpenID Connect integration for enterprise IAM, and live hot-plugging for shared storage and devices . **Debian Trixie deprecated LXD in favor of Incus**, confirming its status as the community standard . Best for teams that want LXD-like container/VM management with community governance and permissive licensing.

### Additional Strong Open-Source Options

- **Harvester (SUSE Rancher)** — Open-source HCI (hyperconverged infrastructure) platform built on Kubernetes, integrating KVM, Longhorn storage, and Rancher management. Best for teams that want VM management alongside container workloads on Kubernetes .
- **oVirt** — Open-source virtualization management platform built on KVM, with a focus on enterprise virtualization management. Best for organizations seeking a Red Hat-supported alternative to VMware.
- **Ganeti** — Cluster virtualization manager from Google, used internally for years. Best for lightweight, scriptable VM management on commodity hardware.
- **Frameworks for building custom systems**: Use **Proxmox VE** for SMB/homelab virtualization with minimal operational overhead. Choose **Apache CloudStack** for service-provider-grade IaaS with simpler operations than OpenStack. Use **OpenStack** when you need a fully open, API-complete cloud platform and have the team to run it. Choose **OpenNebula** when migrating from VMware with GPU/AI requirements. Use **Incus** for container/VM management with permissive licensing.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- **Operational complexity varies enormously**: Proxmox VE can be running in an hour; OpenStack can take weeks to deploy correctly. Match the tool to your team's expertise, not just feature checklists .
- **Licensing matters**: Incus is Apache 2.0; Proxmox VE components are AGPL-3.0; OpenStack is Apache 2.0. LXD's shift to AGPLv3 and Canonical's CLA requirement prompted the Incus fork—verify licensing before committing .
- **CloudStack 4.21 is a regular release, not LTS**: it will only be supported until the next regular or LTS release . Plan upgrade cadence accordingly.

---

**Made for cloud architects, platform engineers, and organizations building private or sovereign infrastructure.**  
Let's make IaaS more open, appropriately scoped, and understandable.
