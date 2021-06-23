# Kubernetes Security

## Policy Enforcement

> a kubernetes videobírója

2021. Junius - Papp Lajos

---

# lalyos

- mar az ovodaban in balna volt a jelem (1998)
- Cofounder of SequenceIQ (docker + bigdata + felho)
- long time dev (java/golang)
- trainer/consultant (hire me!)
- docker meetup bp organizer
- k8s meetup frequent speaker

---

# Topics

-  Cloud Native Security Overview: 4 layers
-  Pick a couple
-  Policy Enforcement

---

## Cloud Native ???

mit adtak nekunk a romaiak ( Docker )?
- solving: "it was running on my machine" (tm)
- packaging format (tar.gz of layers)
- containerd + runc
- microservices [12factor.net](https://12factor.net/)

- k8s: run containers on a lot of servers

---

## Cloud Native Security - 4C

![](https://d33wubrfki0l68.cloudfront.net/50846f7aa12f39c374f4e5ace769efe26a92f7d7/8fe83/images/docs/4c.png)

---

## Cloud Layer (1) - Infrastructure

- API Server network access
- Node network access
- Access to etcd (relational DB)
- etcd encryption

---

## Cluster Layer (2)

- Authentication (integration: OIDC,LDAP, SAML,Kerberos)
- RBAC Authorization, use toos: [audit-2-rbac](https://github.com/liggitt/audit2rbac) - 
- more RBAC: http://rbac.dev/
- App Secret management
- Pod Security Policy
- Network policies
- TLS for ingress

---

## Container Layer (3)

- Container Vulnerability Scanning - during build
- Image signing
- Unprivileged users - avoid root
- Alternative Runtimes - [cncf landscape](https://landscape.cncf.io/card-mode?category=container-runtime&grouping=category)

---

## Code Layer (4)

- use TLS/HTTP - service mesh can help
- limit port ranges
- static code analysis [OWASP Source Analysis](https://owasp.org/www-community/Source_Code_Analysis_Tools)
- dynamic probing - automated CSRF, XSS, SQL inject (Zed Attack Proxy - ZAP)[https://owasp.org/www-project-zap/]

---

## Cluster Layer - Secrets

- bitnami [sealed secrets](https://github.com/bitnami-labs/sealed-secrets) - private key in cluster
- [SOPS](https://github.com/isindir/sops-secrets-operator) - private key in AWS/GCP/Azure
- Hashicorp [Vault](https://www.vaultproject.io/docs/platform/k8s) - use an operator: [bank-vaults by BanzaCloud](https://banzaicloud.com/docs/bank-vaults/operator/)

---

## Container Layer -  Runtimes

Docker = dockerd + containerd + runc

k8s = CRI (containerd/crio) + runc/kata/firecracker/gvisor/wasm ...

- [Firecracker](https://firecracker-microvm.github.io/) - Amazon microVM (lambda/fargate)
- [gVisor](https://gvisor.dev/) -  Linux system calls implemented (go) in userspace - opensourced by Google (cloudRun/cloudFn/appe)
- [KataContainers](https://katacontainers.io/) - lightweight VM

---

## Policy Enforcement - best practices

There are industry wide best practices:
- dont use ":latest" images
- restrict image registries
- use probes (readiness/liveness)
- readonly root FS
- drop all capabilities
- require labels (owner,appname)
- disallow NodePort

---

## Policies - how to enforce them

- email word doc to all devs
- "please sign it on paper"
- Instead: use a policy/rule engine

---

## Policies - CNCF landscape

- [OPA](https://www.openpolicyagent.org/)
- [Kyverno](https://kyverno.io/)
- ...
- Full list: [cncf landscape: Security and Complience](https://landscape.cncf.io/card-mode?category=security-compliance&grouping=category)

---

## Policy Enforcement - OPA

- OPA: https://www.openpolicyagent.org/
  - generic (non k8s specific)
  - own Domain Specific Lang (rego)
  - steep learning curve
  - complex

---

## Policy Enforcement - Kyverno

- Kyverno: https://kyverno.io/
  - k8s specific policy engine
  - no DSL: plain yaml
  - easy to read (DN-RTFM)
  - easy to learn
  - [predefined policies](https://kyverno.io/policies/) for best practices

---

## Admission Controller

- Builtin: DefaultIng, DefaultStorageCl, LimitRanger, NamespaceLifeCyc, ResourceQuota, ServiceAcc, ...

![](https://banzaicloud.com/img/blog/admission-webhooks/webhooks.png)

---

## Policies - Kyverno

- require Limits and Requests
- add network policy (deny all ing/egr)
- add quota to each NS
- add labels (mesh)
- replace image registry: docker.io -> registry.mycorp.com
- require probes (readiness/liveness)
- readonly root FS
- disallow default NS

---

## Keep in touch

- http://hwsw.lalyo.sh/