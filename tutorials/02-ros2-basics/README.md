# 🚀 Introdução ao ROS2

Este tutorial apresenta os conceitos básicos do **ROS2**, incluindo instalação, estrutura de pacotes e comandos essenciais.

## 📌 O que é ROS2?

O **ROS2** (Robot Operating System 2) é um framework para desenvolvimento de sistemas robóticos, oferecendo suporte a comunicação distribuída, controle de robôs e simulação.

## 🔧 Instalação do ROS2 (Ubuntu 22.04)

### 1️⃣ Configurar repositório e chaves
```bash
sudo apt update && sudo apt install -y curl
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key | sudo apt-key add -
```

### 2️⃣ Adicionar repositório do ROS2
```bash
sudo apt-add-repository universe
sudo apt update
sudo apt install -y ros-humble-desktop
```

### 3️⃣ Configurar ambiente ROS2
```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

## 🏗️ Estrutura do ROS2

No ROS2, o desenvolvimento segue a organização de pacotes dentro de um workspace:

```
ros2_ws/                  # Workspace principal
 ├── src/                 # Diretório para pacotes personalizados
 │   ├── meu_pacote/      # Exemplo de um pacote ROS2
 │   ├── outro_pacote/
 ├── install/             # Pacotes instalados
 ├── build/               # Arquivos de build temporários
 └── log/                 # Logs do ROS2
```

### 4️⃣ Criar um workspace ROS2
```bash
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws
colcon build
source install/setup.bash
```

## 🔧 Comandos Essenciais

### Verificar instalação
```bash
ros2 doctor
```

### Criar um pacote ROS2 (exemplo em Python)
```bash
cd ~/ros2_ws/src
ros2 pkg create --build-type ament_python meu_pacote
```

### Rodar um nó ROS2 (talker)
```bash
ros2 run demo_nodes_cpp talker
```

### Listar tópicos ativos
```bash
ros2 topic list
```

### Inspecionar mensagens de um tópico
```bash
ros2 topic echo /chatter
```

## 📚 Referências

- [Documentação Oficial do ROS2](https://docs.ros.org/en/humble/)
- [Guia de Desenvolvimento ROS2](https://roboticsbackend.com/category/ros2/)

---
