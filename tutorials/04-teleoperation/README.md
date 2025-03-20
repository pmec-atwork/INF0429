# 🎮 Teleoperação do TurtleBot3

Este tutorial ensina como **controlar manualmente** o **TurtleBot3** utilizando os pacotes padrão do ROS2.

> **Importante:** Todos os comandos devem ser executados **dentro do container Docker**.

---

## 📦 1️⃣ Configuração Inicial

### **Passo 1: Iniciar o Container**
Caso ainda não esteja rodando:
```bash
./run.sh turtlebot3_ros2:latest
```
Caso precise abrir um novo terminal dentro do container:
```bash
docker exec -it turtlebot3_container bash
```

### **Passo 2: Definir o Modelo do TurtleBot3**
O modelo padrão é **`waffle`**, mas pode ser alterado antes da execução:
```bash
export TURTLEBOT3_MODEL=burger  # Opções: burger, waffle, waffle_pi
```

---

## 🚀 2️⃣ Controlando o TurtleBot3 via Teleoperação

O pacote `turtlebot3_teleop` fornece um nó padrão para enviar comandos de movimentação ao robô.

### **Opção 1: Teleoperação via Teclado**
Para controlar o TurtleBot3 com o teclado, execute:
```bash
ros2 run turtlebot3_teleop teleop_keyboard
```
Isso abrirá uma interface de controle via terminal:

```
Control Your TurtleBot3!
---------------------------
Moving around:
        w
   a    s    d
        x

w/x : aumentar/diminuir velocidade linear
a/d : girar para esquerda/direita
s   : parar o robô

CTRL+C para sair
```

### **Opção 2: Enviar Comandos Manualmente**
Se quiser enviar comandos diretamente para o robô sem usar o teclado interativo, publique mensagens no tópico `/cmd_vel`:

```bash
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist "{linear: {x: 0.2, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 0.5}}"
```

Esse comando faz o TurtleBot3 andar para frente enquanto gira.

---

## 📊 3️⃣ Monitoramento de Tópicos Durante a Teleoperação

Para verificar os tópicos ativos enquanto o robô está se movendo:
```bash
ros2 topic list
```

Para monitorar os comandos de velocidade enviados pelo `teleop`:
```bash
ros2 topic echo /cmd_vel
```

---

## 📚 Referências

- [TurtleBot3 - Teleoperation](https://emanual.robotis.com/docs/en/platform/turtlebot3/basic_operation/#topic-monitor)

---
