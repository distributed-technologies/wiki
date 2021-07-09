<img src="images/Energinet-logo.png" width="250" style="margin-bottom: 3%">

**Secure compute and communication platform** 
The energy system is the most critical infrastructure needed to uphold basic functions in society, and it is key that it can not be subject to any adversarial attacks. The **SCCP** fuses hardware and software security in a **Trusted Execution Environment** to make sure that everything that is executed has been signed and approved to 
run on the platform and only on the platform, meaning that a signed application will refuse to run anywhere else.  

### Architecture
The platform is essentially a Kubernetes cluster with an operator supporting the GitOps workflow. Following the GitOps workflow, all infrastructure is configured as code in separate git repositories as individual services. The environment itself should be defined based on a single repository in the near future, describing the infrastructure provisioning, enabled system services, and referring hosted applications environment repositories.

### Hosting
The platform is cloud-agnostic, meaning that it will be able to be deployed both in bare metal situations as well as on deployed in any cloud provider thus greatly increasing the stability and scalability of the platform because vendor lock-in is avoided. Avoiding vendor lock-in we reduce the risk caused by cloud providers having an outage, a security event, or simply discontinues services, as a cloud-agnostic platform can seamlessly move to wherever fits its demands. 
Compiling our own Linux operating system, we reduce the dependencies and packages to a minimum, further reducing the potential attack vectors for adversaries. Basically, the only features enabled are the ones that are needed to start up a Kubernetes cluster. 

### Security
Taking the next step in security, the platform is enabling a feature to fuse hardware and software security in a trusted execution environment. In its essence, this means that the hardware will not run any software that does not have the correct digital signatures and the software will not run on any hardware that does not have the correct digital signature.

### Technologies 
All technologies that are used to build the SCCP are open source.

#### [ArgoCD](https://github.com/argoproj/argo-cd/) 
ArgoCD is used as the GitOps tool that continuously delivers changes to the platform based on pull request changes.

#### [Prometheus](https://github.com/prometheus/prometheus)
Prometheus is used as the monitoring time-series database, that continuously scrapes metrics from all containers that expose them.

#### [Grafana](https://github.com/grafana/grafana)
Grafana is used as the monitoring visualization tool, where dashboards provide insights into the metrics.

#### Ceph
Ceph is used through an [open-source Rook operator](https://github.com/rook/rook) as a distributed persistent storage, handling jobs like replication to avoid data loss at machine failure. 

#### [Metallb](https://github.com/metallb/metallb)
MetalLB is used as the software load balancer delegating IPs to services that need a static IP. 

#### [Traefik](https://github.com/traefik/traefik)
Traefik is used as an ingress controller handling ingress events to route communication.

### Roadmap
- [x] Monitoring 
- [x] Ingress 
- [x] Loadbalancer 
- [x] Distributed storage 
- [ ] TEE
- [ ] PKI infrastructure
- [ ] One click build pipeline
