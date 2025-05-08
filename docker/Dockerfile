FROM osrf/ros:humble-desktop-full

RUN apt update && apt install -y \
    nano \
    git \  
    ros-humble-gazebo-ros-pkgs \
    ros-humble-cartographer \
    ros-humble-cartographer-ros \
    ros-humble-navigation2 \
    ros-humble-nav2-bringup \
    ros-humble-dynamixel-sdk \
    ros-humble-hls-lfcd-lds-driver \
    ros-humble-moveit-ros-move-group \
    ros-humble-moveit-kinematics \
    ros-humble-moveit-planners \
    ros-humble-moveit-simple-controller-manager \
    ros-humble-joint-state-publisher \
    ros-humble-joint-state-publisher-gui \
    ros-humble-moveit-ros-visualization \
    ros-humble-moveit-ros-warehouse \
    ros-humble-warehouse-ros* \
    ros-humble-srdfdom \
    ros-humble-ros2-control \
    ros-humble-ros2-controllers \
    ros-humble-gripper-controllers \
    ros-humble-tf-transformations \
    ros-humble-hardware-interface \
    ros-humble-control-msgs \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --upgrade\
    numpy==1.26.4 \
    scipy==1.10.1 \
    tensorflow==2.19.0 \
    keras==3.9.2 \
    pyqtgraph

RUN mkdir -p /root/turtlebot3_ws/src && cd /root/turtlebot3_ws/src && \
    git clone -b humble-devel https://github.com/pmec-atwork/turtlebot3.git && \
    git clone https://github.com/pmec-atwork/turtlebot3_simulations && \
    git clone https://github.com/pmec-atwork/turtlebot3_msgs.git && \
    git clone https://github.com/pmec-atwork/turtlebot3_machine_learning.git && \
    git clone https://github.com/ROBOTIS-GIT/turtlebot3_autorace.git && \
    cd .. && \
    /bin/bash -c "source /opt/ros/humble/setup.bash && colcon build --symlink-install"

ENV TURTLEBOT3_MODEL=waffle

RUN echo "source /opt/ros/humble/setup.bash" >> /root/.bashrc && \
    echo "source /root/turtlebot3_ws/install/setup.bash" >> /root/.bashrc && \
    echo "source /usr/share/gazebo/setup.bash" >> /root/.bashrc