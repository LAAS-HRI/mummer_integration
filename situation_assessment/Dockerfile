FROM ros:kinetic
# place here your application's setup specifics

RUN apt-get update

# Dependencies to enable opengl rendering in docker

RUN apt-get install -y mesa-utils x11vnc xvfb x11-xserver-utils xinit && mkdir ~/.vnc

RUN x11vnc -storepasswd 1234 ~/.vnc/passwd

# Install Underworlds dependencies...

RUN apt-get install -y python-pyassimp

RUN apt-get install -y python-opengl

RUN apt-get install -y python-pygame

RUN apt-get install -y ros-kinetic-ar-track-alvar

RUN apt-get install -y python-pip

RUN pip install --upgrade pip

RUN pip install argcomplete

RUN pip install grpcio

# Install Underworlds from official repository...

RUN mkdir ~/situation_assessment_deps/ && cd ~/situation_assessment_deps/

RUN git clone https://github.com/underworlds-robot/underworlds.git
RUN cd underworlds && python setup.py install

# Install Perspectives dependencies...

RUN cd .. && git clone https://github.com/bulletphysics/bullet3
RUN cd bullet3 && python setup.py install
RUN pip install pybullet

RUN pip install lxml

# Create & init catkin workspace

RUN source /opt/ros/kinetic/setup.bash && cd && mkdir -p catkin_ws/src && cd ~/catkin_ws/ && catkin_make && source ./devel/setup.bash
RUN cd ./src/ && mkdir situation_assessment && cd ./situation_assessment && git clone https://github.com/LAAS-HRI/laas_models.git
RUN git clone https://github.com/underworlds-robot/env_provider.git
RUN git clone https://github.com/underworlds-robot/robot_monitor.git
RUN git clone https://github.com/underworlds-robot/perspective_filter.git
RUN git clone https://github.com/underworlds-robot/allocentric_monitor.git
RUN git clone https://github.com/underworlds-robot/ar_object_provider.git
RUN git clone https://github.com/underworlds-robot/physics_filter.git
RUN git clone https://github.com/underworlds-robot/multimodal_human_monitor.git
RUN git clone https://github.com/LAAS-HRI/perspectives_msgs.git
RUN git clone https://github.com/LAAS-HRI/perspectives.git
RUN git clone https://github.com/LAAS-HRI/dialoGUI.git
RUN cd .. && catkin_make && source ./devel/setup.bash

RUN uwds start

ENV DISPLAY :0

ENV APP /usr/local/bin/uwds-view base

#CMD [ "roslaunch", "perspectives mummer.launch" ]
