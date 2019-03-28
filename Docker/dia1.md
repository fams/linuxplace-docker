name: splash
layout: true
class: center, middle, inverse

---
count:false
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

# Agenda

### Dia 1
 - Por que usar Containers?
 - Instalando Docker
 - Docker Containers
 - Docker Images
 - Criando uma imagem
 - Deep Dive

---

# Por que usar Containers?
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

# O que é um container
### Virtualização de Hardware
### Virtualização de Sistema Operacional
.nb-table[
<table>
<tr><td>.half-image[![Container x Instance](/img/container_stack.png)]</td><td> .half-image[![Container x Instance](/img/vm_stack.png)]</td></tr>
</table>
]

---

# Historia dos containers
### 1979: Unix V7 chroot
### 2000: FreeBSD Jails
### 2001: Linux VServer
### 2003: CKRM
### 2004: Solaris Containers
### 2005: Open VZ (Open Virtuzzo)
### 2006: Process Containers (Cgroups)

???
- choot namespace filesystem
- Jails IP no chroot
- VServer (particionamento de recursos)
- CKRM Kernel Resource Manager tentativa de AIX WLM
- Solaris Containers - Bem proximos de um container atual, mas a idéia era instalar todo o sistema para virtualizar competindo com o IBM LPAR
- Open VZ mesma ideia do Solaris
- Cgroups Isolamento de recursos e limites base do docker

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

???
 - Linux Containers. Cgroups, namespaces sem patch
 - CloudFondry Warden, agora fazem parte do OCI.
 - implementação open do gerenciador de containers do google
 - ...
 - Orquestrador vindo do BORG.
 - Open Container Initiative
 - Mainstrea

---

# Docker Cheat Sheet
- https://www.docker.com/sites/default/files/Docker_CheatSheet_08.09.2016_0.pdf

---
# LAB 1 - Instalando Docker

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
http://hub.docker.com

???

---

# Instalando Docker em Linux

### Instalar o docker-machine
```bash
$ sudo base=https://github.com/docker/machine/releases/download/v0.16.0 &&
  curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine &&
  sudo install /tmp/docker-machine /usr/local/bin/docker-machine
```
### Instalar o docker-compose
```bash
$ sudo curl -L https://github.com/docker/compose/releases/download/1.24.0-rc1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
```


---

# Instalando Docker em Linux
```terminal
[root@dockervm tmp]$ sudo docker version
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
--

 ```bash
 $ sudo docker info
 ```
???

 O erro ao rodar o docker a primeira vez vem de não start do docker


---

# Instalando Docker em Linux

- Adicionar o usuario pessoal ao grupo docker

```bash
 $ sudo usermod -aG docker $USER
 $ docker info
 $ docker version
```

---
# Instalando o Docker em MAC
- Download Docker for Mac (DfM)
- Instalação
- Preferências

---
### LAB 2 - RUN

#### Executando um container _interativo_
 - Download da imagem
```bash
$ docker image pull bash
```
 - Executando o container interativo *-it*
```bash
$ docker container run  -it bash
```
- Sair do shell (Ctrl+D ou exit)

```bash
$ docker container ps
$ docker container ps -a
```

---
#LAB 2 - RUN
#### Executando um container _interativo_ e deixando-o vivo

```bash
$ docker container run  -it bash
```
- Ctrl+PQ

```bash
$ docker container ps
$ docker container ps -a
```
--
- Anexando ao container

```bash
$ docker container ls
$ docker container attach $container
```

---
#LAB 2 - RUN
#### Executando um container em segundo plano

```bash
$ docker container run --detach -p8080:80 nginx
```

--
- Não anexar o TTY --detach ou -d
- Exportar a porta do container no host local -p{local}:{container}

---
#LAB 2 - RUN
# Docker image
```bash
$ docker image ls
$ docker image rm
$ docker image pull
$ docker container inspect
```

---

# Entendendo
### Estrutura de linha de commando docker
 - modo antigo : docker &lt;command&gt; (options)

```bash
   $ docker run -it bash
   $ docker pull bash
```

 - modo novo: docker &lt;command&gt; &lt;sub-command&gt; (options)

```bash
  $ docker container run -it bash
  $ docker image pull bash
```

---

# Construindo uma imagem
- BUILD, SHIP, RUN

- Dockerfile (build)
- docker build (build)

--
- docker push (ship)

--
- docker run (run)

---

# Dockerfile
```dockerfile
FROM ubuntu:16.04
LABEL mantainer=fams@linuxplace.com.br
COPY ./Docker/ /var/www/html
EXPOSE 80
RUN apt-get update -y && apt-get install --no-install-recommends python3 -y
WORKDIR  /var/www/html
ENTRYPOINT [ "python3", "-m", "http.server", "80" ]
```

--
#### Dockerfile
 - Descrever a aplicação
 - Ensinar o docker como criar o container

---
# BUILD
```bash
$ docker build . -t curso:latest
$ docker run -d -p 8080:80 curso:latest
```

---
# Comandos de image build
- docker build -t curso:latest .
- -t tag
- . para usar o diretório atual como workdir do build

---

# inspect image
```bash
$ docker image inspect curso
$ dive curso
```

---
# build layers
.full-image-height[![Docker Model](img/build.svg)]

---
# SHIP
- Fazer login no docker hub
- criar o repositório
- publicar seu container

---
# Publish
```bash
$ docker image tag $USERNAME/curso
$ docker image push $USERNAME/curso
```

---
# Comandos Dockerfile
#### Estrutura
 - \#Comment
 - INSTRUCTION arguments

---
# Comandos
- FROM
- COPY & ADD
- LABEL
- ENV
- WORKDIR
- RUN
- CMD
- EXPOSE
- ENTRYPOINT
- USER
- STOPSIGNAL
- VOLUME

---
