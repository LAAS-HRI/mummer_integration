FROM ros:kinetic
# place here your application's setup specifics

SHELL ["/bin/bash", "-c"]

# Install dependencies
RUN apt-get update && apt-get install -y python-pyassimp python-opengl python-pygame ros-kinetic-ar-track-alvar python-pip

RUN pip install --upgrade pip && python -m pip install lxml argcomplete grpcio

# Install Underworlds from official repository...
RUN git clone https://github.com/underworlds-robot/underworlds.git && cd underworlds && python setup.py install

# Install python bullet SDK
RUN git clone https://github.com/bulletphysics/bullet3 && cd bullet3 && python setup.py install

# Create ROS workspace
RUN mkdir -p catkin_ws/src
WORKDIR catkin_ws/src

#ADD https://api.github.com/repos/LAAS-HRI/laas_models/git/refs/heads/master \
#    https://api.github.com/repos/LAAS-HRI/perspectives_msgs/git/refs/heads/master \
#    https://api.github.com/repos/underworlds-robot/env_provider/git/refs/heads/master \
#    https://api.github.com/repos/underworlds-robot/robot_monitor/git/refs/heads/master \
#    https://api.github.com/repos/underworlds-robot/perspective_filter/git/refs/heads/master \
#    https://api.github.com/repos/underworlds-robot/allocentric_monitor/git/refs/heads/master \
#    https://api.github.com/repos/underworlds-robot/ar_object_provider/git/refs/heads/master \
#    https://api.github.com/repos/underworlds-robot/physics_filter/git/refs/heads/master \
#    https://api.github.com/repos/LAAS-HRI/multimodal_human_monitor/git/refs/heads/master \
#    https://api.github.com/repos/LAAS-HRI/perspectives/git/refs/heads/master /tmp/

RUN git clone https://github.com/LAAS-HRI/laas_models.git && \
    git clone https://github.com/LAAS-HRI/perspectives_msgs.git && \
    git clone https://github.com/underworlds-robot/env_provider.git && \
    git clone https://github.com/underworlds-robot/robot_monitor.git && \
    git clone https://github.com/underworlds-robot/perspective_filter.git && \
    git clone https://github.com/underworlds-robot/allocentric_monitor.git && \
    git clone https://github.com/underworlds-robot/ar_object_provider.git && \
    git clone https://github.com/underworlds-robot/physics_filter.git && \
    git clone https://github.com/LAAS-HRI/head_manager.git && \
    git clone https://github.com/LAAS-HRI/deictic_gestures.git && \
    git clone https://github.com/LAAS-HRI/speech_wrapper.git && \
    git clone https://github.com/LAAS-HRI/multimodal_human_monitor.git && \
    git clone https://github.com/LAAS-HRI/perspectives.git

RUN source /opt/ros/kinetic/setup.bash && cd .. && catkin_make && source ./devel/setup.bash

CMD uwds start && source /opt/ros/kinetic/setup.bash && source ../devel/setup.bash && roslaunch perspectives mummer_no_gui.launch
