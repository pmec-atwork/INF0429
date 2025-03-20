# 🚀 Introdução ao Docker

Este tutorial apresenta os conceitos básicos do **Docker**, incluindo instalação, comandos essenciais e uso de containers.

## 📌 O que é Docker?

O **Docker** é uma plataforma que permite criar, distribuir e executar aplicações em containers de forma isolada e portátil.

## 🔧 Instalação do Docker

### Linux (Ubuntu)
```bash
sudo apt update
sudo apt install -y docker.io
sudo systemctl enable --now docker
```

### Windows (WSL2)
Siga as instruções oficiais: [Docker for Windows](https://docs.docker.com/desktop/install/windows-install/).

## 🏗️ Comandos Essenciais

### 1️⃣ Verificar versão
```bash
docker --version
```

### 2️⃣ Listar imagens locais
```bash
docker images
```

### 3️⃣ Rodar um container básico (Ubuntu)
```bash
docker run -it ubuntu bash
```

### 4️⃣ Listar containers em execução
```bash
docker ps
```

### 5️⃣ Listar todos os containers (inclusive parados)
```bash
docker ps -a
```

### 6️⃣ Remover um container parado
```bash
docker rm <CONTAINER_ID>
```

### 7️⃣ Remover uma imagem
```bash
docker rmi <IMAGE_ID>
```

## 📚 Referências

- [Documentação Oficial do Docker](https://docs.docker.com/)
- [Docker Cheatsheet](https://github.com/wsargent/docker-cheat-sheet)

---

Se precisar de ajustes ou adicionar mais seções, me avise!