name: splash
layout: true
class: center, middle, inverse

---

# Docker - Infraestrutura imutavel
![logo-docker](img/docker_logo.png)
# by [@famsbh](http://twitter.com/famsbh)

---
layout: true
name: sessao
class: left, center, inverse
#.logo-linux[![Linuxplace Logo](img/linuxplace-logo-preta.png)]

---
layout: true
name: conteudo
class: left, top
.logo-linux[![Linuxplace Logo](img/linuxplace-logo-preta.png)]

---
template: conteudo

# Porque usar Containers?
### 300% time to market
???
- Agilidade de implantação de novas soluções

--

### 1300% Produtividade de desenvolvimento
???
- Setup de ambiente, sem dependency hell

--

### 60% Produtividade de deployment
???
- infra-estrutura imutavel. Dev e Prod mesmo ambiente

--

### -40% Infraestrutura de TI
???
- reaproveitamenteo de recursos, aumento de densidade

--

### 40% Eficiência operacional
???
- entrega simples, esteira mais uniformizada

--

### 72% Velocidade de resolução de problemas
???
- Compartimentados problemas, mesmo ambiente da producao

--

### https://www.docker.com/roicalculator

---

template: conteudo
# Container é Disruptivo!
### Mainframe para PC (1970-80)

--
### Internet (1990-2000)

--
### Virtualização (2000-2010)

--
### Cloud (2010-)

--
### Container (2016-)

---

# Docker é sobre deployment

.full-image[![Historia do Deployment][deployment_history]]
[deployment_history]: /img/deployment-maturity.png "Historia do Deployment"

???
- Manual de instalação

- Wizard Installshield

- Script (customização da instalação)

- Gerenciamento de configuração

- Um pacote único

- Sem instalação

???

1. Manual
2. Wizard
3. Script
4. Estado Desejado
5. Container
6. Serverless
---

# Docker ?
### Docker inc
- dotCloud PaaS
- docker era tooling interno
- 2013 se torna Docker Inc.

### Docker container runtime
- Docker CE
- Docker EE

### Docker opensource (Moby)
- Upstream for docker

---

# Docker Editions

.conteudo[
| Capabilities | Docker Engine CE | Docker Engine EE | Docker Enterprise |
|--- | --- | --- |---|
|Container engine and built in orchestration, networking, security| ✅ | ✅ |✅ |
|Certified infrastructure, plugins and ISV containers | |✅ | ✅|
|Image management| | |✅|
|Container app management|  |  |✅|
|Image security scanning| | | ✅|
]
???
 CE 4 meses
 EE 12 meses
---

# Lifecycle versions
.full-image[![Life Cycle][lifecycle]]
[lifecycle]: /img/lifecycle.png "Ciclo de Vida Docker CE/EE"

---

# Docker Cheat Sheet
- https://www.docker.com/sites/default/files/Docker_CheatSheet_08.09.2016_0.pdf

---
# O que é um container
### Virtualização de Hardware
### Virtualização de Software
.nb-table[
<table>
<tr><td>.half-image[![Container x Instance](/img/container_stack.png)]</td><td> .half-image[![Container x Instance](/img/vm_stack.png)]</td></tr>
</table>
]

---

# Historia dos containers
### 1979: Unix V7
### 2000: FreeBSD Jails
### 2001: Linux VServer
### 2003: CKRM
### 2004: Solaris Containers
### 2005: Open VZ (Open Virtuzzo)
### 2006: Process Containers (Cgroups)

---
# Historia dos containers

### 2008: LXC
### 2011: Warden
### 2013: LMCTFY
### 2013: Docker
### 2014: Kubernetes
### 2015: CNCF, HELM
### 2017: OCI 1.0
### 2018: K8S Mainstream

---

# Instalando Docker

### Instalando Docker em linux
- Remova o docker da distribuição
 - apt search docker
 - yum search docker
 - apt remove
 - yum remove

- instale o docker

```bash
$ sudo wget -qO- https://get.docker.com/ | sh
```
???

---

# Instalando Docker em Linux
```terminal
[root@dockervm tmp]# docker version
Client:
 Version:           18.09.3
 API version:       1.39
 Go version:        go1.10.8
 Git commit:        774a1f4
 Built:             Thu Feb 28 06:33:21 2019
 OS/Arch:           linux/amd64
 Experimental:      false

Server: Docker Engine - Community
 Engine:
  Version:          18.09.3
  API version:      1.39 (minimum version 1.12)
  Go version:       go1.10.8
  Git commit:       774a1f4
  Built:            Thu Feb 28 06:02:24 2019
  OS/Arch:          linux/amd64
  Experimental:     false
```
--
```bash
$ sudo systemctl start docker
```

---
# Instalando Docker em Linux

### Instalar o docker-machine
```terminal
$ base=https://github.com/docker/machine/releases/download/v0.16.0 &&
  curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine &&
  sudo install /tmp/docker-machine /usr/local/bin/docker-machine
```

---

# LAB 1
- docker image pull
- docker container run bash
- Ctrl+PQ
- docker container ps


---

# LAB1
- docker container run --detach -p8080:80 nginx

---

# Historia do Container

---
# Cgroups

---

# LAB 1

---

# Cgroups

---
# LXC
---

---

# docker-compose

---

# docker-machine

---

# Docker Images

---

# Teoria Images

---

# Lab Images simple

---

## Docker Containers

---

# Teoria Containers

---

# Lab Containers  Simple


---


# Segurança Docker

---

