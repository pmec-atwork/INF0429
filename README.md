# INF0429
Este repositório contém um ambiente baseado em **Docker** para desenvolvimento e experimentação com o **TurtleBot3** usando **ROS2**.

## 📂 Estrutura do Repositório

O repositório é organizado da seguinte maneira:

- **`docker/`**: Contém o Dockerfile para criação do ambiente.
- **`labs/`**: Diretório para laboratórios e exercícios práticos.
- **`ros_packages/`**: Pacotes ROS2 customizados utilizados na disciplina.
- **`shared_folder/`**: Diretório compartilhado entre o host e o container.
- **`run.sh`**: Script para iniciar o container.
- **`tutorials/`**: Diretório contendo tutoriais sequenciais.

### 📖 Tutoriais Disponíveis

1. [**01 - Docker Basics**](tutorials/01-docker-basics/README.md) - Introdução ao Docker e comandos essenciais.
2. [**02 - ROS2 Basics**](tutorials/02-ros2-basics/README.md) - Estrutura e comandos básicos do ROS2.
3. [**03 - Simulation**](tutorials/03-simulation/README.md) - Simulação do TurtleBot3 no Gazebo e Fake Node.
4. [**04 - Teleoperation**](tutorials/04-teleoperation/README.md) - Controlando o TurtleBot3 via teleoperação.

---

## 🏗️ Como o Repositório Funciona

Este repositório foi projetado para ser utilizado dentro de um **container Docker**, garantindo um ambiente consistente para todos os usuários. O fluxo de trabalho recomendado é:

1. **Construir a imagem Docker** 
2. **Executar o ambiente** 
3. **Acessar múltiplos terminais**
4. **Explorar os tutoriais** 

Cada tutorial cobre uma parte essencial do ambiente, desde a configuração do Docker até a simulação e controle do TurtleBot3.

---

## 📌 Requisitos

Antes de começar, certifique-se de ter os seguintes pacotes instalados:

- **Docker** ([instalação](https://docs.docker.com/get-docker/))
- **NVIDIA Container Toolkit** (se utilizar GPU)
- **Git** para clonar o repositório

## 🚀 Instalação

### 1. Clonar este repositório
```bash
git clone https://github.com/pmec-atwork/INF0429.git
cd INF0429
```

### 2. Construir a imagem Docker
```bash
docker build -t turtlebot3_ros2 . -f docker/Dockerfile
```

### 3. **Executar o ambiente**
Agora, para rodar o script com um nome de imagem, execute:

```bash
./run.sh turtlebot3_ros2:latest
```

> **Nota:** Se nenhum argumento for passado, o script exibirá um erro e encerrará a execução.

### 4. **Acessar múltiplos terminais**
Caso precise abrir novos terminais dentro do container já em execução, utilize o comando:

```bash
docker exec -it turtlebot3_container bash
```

Isso permite abrir múltiplas sessões interativas dentro do mesmo ambiente do container em execução.

---

