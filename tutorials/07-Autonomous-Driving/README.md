# 🏎️ Direção autonoma no turtlebot3

Este tutorial ensina como usar os pacotes de **direção autônoma** com o TurtleBot3, incluindo **detecção de faixa, semáforos e controle autônomo do robô**.

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
O modelo padrão é **`waffle`**, mas nesse tutorial iremos utilizar o **`burger_cam`**:
```bash
export TURTLEBOT3_MODEL=burger_cam 
```
---

## 🤖2️⃣ Definindo o Modelo do TurtleBot3

Adicione também esta linha ao seu ~/.bashrc, pois o Autorace só é compatível com o modelo burger_cam:
```bash
export TURTLEBOT3_MODEL=burger_cam
```


## 🌍3️⃣ Simulação do Ambiente de Direção
#### Inicie a simulação no Gazebo com um curso pré-definido de acompanhamento de faixa.
```bash
ros2 launch turtlebot3_gazebo turtlebot3_autorace_2020.launch.py
```

#### Em seguida, execute os processos de calibração da câmera, que garantem que as faixas detectadas sejam mapeadas com precisão na perspectiva do robô:
```bash
ros2 launch turtlebot3_autorace_camera intrinsic_camera_calibration.launch.py
```

```bash
ros2 launch turtlebot3_autorace_camera extrinsic_camera_calibration.launch.py
```
Esses passos ativam a calibração intrínseca e extrínseca para corrigir distorções no sinal da câmera.

#### Por fim, inicie o nó de detecção de faixas em modo de calibração para começar a detectar as faixas:
```bash
ros2 launch turtlebot3_autorace_detect detect_lane.launch.py calibration_mode:=True
```

### 📷 Visualizando a Saída da Detecção de Faixas

Para inspecionar as faixas detectadas, abra o rqt:
```bash
rqt
```
Em seguida, navegue até o menu: Plugins > Visualization > Image View
Abra três visualizadores de imagem para exibir os diferentes resultados da detecção de faixas, como:
- /detect/image_lane/compressed
![alt text](images/lane.png) 
- /detect/image_yellow_lane_marker/compressed
![alt text](images/yellow.png) 
- /detect/image_white_lane_marker/compressed
![alt text](images/white.png) 

### 🏎️ Executando o Acompanhamento de Faixas
#### Após a conclusão da calibração, reinicie o nó de detecção de faixas sem a opção de calibração:

```bash
ros2 launch turtlebot3_autorace_detect detect_lane.launch.py
```

#### Em seguida, inicie o nó de controle de acompanhamento de faixas. Ele permite que o TurtleBot3 siga automaticamente as faixas detectadas:
```bash
ros2 launch turtlebot3_autorace_mission control_lane.launch.py
```
### 3️⃣🚦 Detecção de Placas de Trânsito

#### Iniciando o Nó de Detecção de Placas
Para detectar placas de trânsito, inicie o nó de detecção com o seguinte comando:
```bash
ros2 launch turtlebot3_gazebo turtlebot3_autorace_2020.launch.py
```

#### Rodando o teleop do turtlebot3
```bash
ros2 run turtelbot3_teleop teleop_keyboard
```

#### Visualizando as Placas Detectadas
Abra o rqt para inspecionar as placas de trânsito detectadas:
```bash
rqt
```
No menu, vá para: Plugins > Visualization > Image View. Adicione um visualizador de imagem para exibir o tópico:
- `/detect/image_traffic_sign/compressed`

#### Configurando o Reconhecimento de Placas
Rode a calibração de câmera
```bash
ros2 launch turtlebot3_autorace_camera intrinsic_camera_calibration.launch.py
```
```bash
ros2 launch turtlebot3_autorace_camera extrinsic_camera_calibration.launch.py

```
#### Iniciando o reconhecimento da missão determinada
```bash
ros2 launch turtlebot3_autorace_detect detect_sign.launch.py mission:={SELECT_MISSION}

```

Defina a missão substituindo `{SELECT_MISSION}` por uma das alternativas a seguir: intersection, construction, parking, level_crossing, tunnel

#### Visualizando o teste
Para a visualização da detecção use o rqt e observe a câmera enquanto controla o turtlebot3 pelo teleop

exemplo: 
![alt text](images/detection_sign.png)

