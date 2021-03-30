## A Docker az ellen is ved

developer experience is the king

> clickbait hirado: ... nem derul ki

---

# lalyos

- mar az ovodaban in balna volt a jelem (1998)
- Cofounder of SequenceIQ (docker + bigdata + felho)
- long time dev (java/golang)
- trainer/consultant
- docker meetup bp organizer

---

# Kell-e nekem kontenerizalnom?

> Soiler alert: IGEN

---

# Mandatory Dilbert

![dilbert](https://i.imgur.com/oN4cTgu.jpg)

---

# Mit adtak nekunk a romaiak?

  - small image (~100mb)
  - startup time (<100ms)
  - ellastic resource usage (cpu/mem)

> Ameddig a fold kerek mindig lesznek dockerek!

---

# Milyen problemat akarunk megoldani?

- "It was runing on my machine" (tm)

- dev/prod parity

- Complexity has a high price

---

![ever given](https://i.ytimg.com/vi/ZDZWMGh1EwI/maxresdefault.jpg)

---

# Mandatory xkcd

![](https://imgs.xkcd.com/comics/compiling.png)

---

## Context switch

If you have to wait for 2 min
- you will go for a coffe
- read social media
- reply some emails


---

# Shoud I automate/rewrite/change process?

- Anecdote: app runs off memory every day

---

![](https://imgs.xkcd.com/comics/is_it_worth_the_time_2x.png)

---

# WTF is Docker?

- company?
- container runtime (Containerd / runC)
- image format (OCI)
- api (Docker api/Docker daemon)
- developer expreinece:
  - docker run
  - docker compose up

---

 # Docker Developer experience

 - docker run is simple
 - onboarding: (install docker ... done)

 Other projects try to copy the DX

 - nerdctrl run
 - ignite run

---

# Fidesz / Momentum / Jobbik ?

> It depends (tm)

- Windows / Linux(distro?) / OlominiumOS
- Vm / containers
- swarm / aws ecs / k8s (distro?)
- monolith / microservices

---

> azt a problemat oldd meg ami a legjobban faj (SequenceIQ/BanzaiCloud)

---

# A szamitogep azert van hogy segitsen
 ... a fejlesztoknek is

Use case:
- A fejlesztoi gep (8GB) elfustol

---

## Megdobbento: kiderult van mas is mint docker?

- Container that looks like VMs
- VM / microVM based containers
- No containers

---

# Footloose

Container Machines - Containers that look like Virtual Machines

---

# Igazi VM-et akarsz?

- firecracker / ignite
- Firecracker: OS microVM by Amazon (lambda/fargate)
- kvm based alternative to QEMU
- VM : <125 ms startup, and < 5 MiB footprint

---

![firecracker](https://firecracker-microvm.github.io/img/diagram-desktop@3x.png)

---

##  Packaging without containers

Nix ugribugri: reproducible, declarative

- dev-ex: nix-shell (docker run -it)
- NixOS based on Nix packages (multiarch)
- https://search.nixos.org/
- can build minimal docker images

---

# Konkluzio ?

- Szelektiv csomagolas
- cloud / onPrem?
- how big is your cluster

---

## References

- http://bit.ly/docker-kerdoiv
- http://hwsw.lalyo.sh/
- https://hackmd.io/@lalyos/hwswmeetup


