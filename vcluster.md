# VCluster

## Virtual K8S Clusters

> "látszólagos fürt" 
> a rezsicsökkentett fölhő

2022. Október - Papp Lajos

---

 0. What does it mean?
 1. Use-cases
 2. How does it work ?
 3. Under the hood

---

# lalyos

- mar az ovodaban in balna volt a jelem
- Cofounder of SequenceIQ (docker + bigdata + felho)
- BanzaiCloud in early times
- long time dev (java/golang) (since 1998)
- trainer/consultant (hire me!)

---

# VCluster

> A virtual k8s cluster which runs 
> in a namespace of a hosting cluster

---

![](https://i.imgur.com/BMdtNdc.png =700x)

---

## Issues with k8s?

---

## Issues with k8s?

- [dev] You got restricted acces

---

## Issues with k8s?

- [dev] You got restricted acces
- [dev] Don't want to chage existing apps

---

## Issues with k8s?

- [dev] You got restricted acces
- [dev] Don't want to chage existing apps
- [ops] Want less clusters to maintain

---

## Real clusters

![](https://i.imgur.com/cK5vWVN.png)

---

## Virtual Clusters

![](https://i.imgur.com/GDpFYHf.png =700x)

---

## Issues with k8s?

- [dev] You got restricted acces
- [dev] Don't want to chage existing apps
- [ops] Want less clusters to maintain
- [ops] Want Restrict acces by namspace

---

## Issues with k8s?

- [dev] You got restricted acces
- [dev] Don't want to chage existing apps
- [ops] Want less clusters to maintain
- [ops] Want Restrict acces by namspace
- [ops] Parallely run different versoins of ...

---

## Issues with k8s?

- [dev] You got restricted acces
- [dev] Don't want to chage existing apps
- [ops] Want less clusters to maintain
- [ops] Want Restrict acces by namspace
- [ops] Parallely run different versoins of ...
- ... more ...

---

- cloud provider APIServer customization ???
- Stop under-utilized clusters
- save costs (megvedjuk a magyar ...)
- Everybody gets a cluster

---

![](https://i.imgur.com/UMxeTSl.png)

---

![](https://i.imgur.com/grGq3gO.png)

---

![](https://i.imgur.com/hCG25AO.png)

---

# Usage

- vcluster cli
-   collect CIDR addr
-   generate KUBECONFIG
- helm

> RBAC: be able to start a pod

---

# Exposing

- internal only
- NodePort
- Loadbalancer
- Ingress

---

## Accessing a VCluster


 $ > `vcluster connect my-vcluster`
 
 > generates KUBECONFIG yaml

---

# How?

Vcluster has its own ctrl-plane
- APIServer
- Controller mgr
- Storage (etcd/kine)
- Scheduler ???

---

![](https://i.imgur.com/wjHfscU.png)


---

# How k8s works normally:

[training slides - thanks jpetazzo](https://lisa-2019-10.container.training/tutorial.yml.html#27)


---

![](https://i.imgur.com/nuot9BC.png)

---

## KINE

Part/Subproject of K3S.io

## Kine Is Not Etcd

> Run Kubernetes on MySQL, Postgres, sqlite, dqlite, not etcd.

> sqlite + litestream + s3 => dirt cheap, 

---

# Scheduler

By default you delegate it to the host cluster. But...

- Labeling nodes inside has no effect
- Draining or tainting nodes inside 
- You cannot use custom schedulers inside 

> vcluster supports running a scheduler inside

---

## DNS - Network

![](https://i.imgur.com/2LJy1bY.png)

service mapping is configurable

---

## Nodes

supports multiple sync modes:

- Fake Nodes (def)
- Real Nodes
- Real Nodes All 
- Real Nodes Label Selector

> daemonsets?

---

## Synched Resources

pods, services, configmaps, secrets, events (other way), PVCs, Ingresses

> configurable

> sdk for custom resource syncers plugins (depl,sts,ns)

---

# Extra Features

- Pausing & Resuming
- High Availability
- Distro choise: k3s/k0s/vanillia k8s
- Backup & Restore (Velero) 

---

# DinD / KinK

![](https://i.imgur.com/DIOVPcl.png =700x)

---


## Keep in touch

- http://hwsw.lalyo.sh/