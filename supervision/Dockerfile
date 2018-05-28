FROM ros:kinetic

SHELL ["/bin/bash", "-c"]

RUN apt-get update && apt-get install -y ros-kinetic-tf ros-kinetic-move-base

RUN mkdir -p catkin_ws/src

WORKDIR /catkin_ws

RUN source /opt/ros/kinetic/setup.bash && catkin_make && source ./devel/setup.bash

WORKDIR /catkin_ws/src

RUN git clone https://github.com/LAAS-HRI/guiding_as
RUN git clone https://github.com/LAAS-HRI/executive_smach
RUN git clone https://github.com/LAAS-HRI/dialogue_as
RUN git clone https://github.com/LAAS-HRI/mummer_integration_msgs

WORKDIR /catkin_ws

RUN source ./devel/setup.bash && catkin_make

CMD source ./devel/setup.bash && roslaunch guiding_as guiding_as.launch

#CMD ["roslaunch", "guiding_as guiding_as.launch"]

