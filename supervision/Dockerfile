FROM ros:kinetic
# place here your application's setup specifics

SHELL ["/bin/bash", "-c"]

RUN mkdir -p catkin_ws/src
WORKDIR catkin_ws/src

RUN git clone https://github.com/LAAS-HRI/executive_smach.git && \
    git clone https://github.com/LAAS-HRI/dialogue_as.git && \
    git clone https://github.com/LAAS-HRI/guiding_as

RUN source /opt/ros/kinetic/setup.bash && cd .. && catkin_make && source ./devel/setup.bash

CMD source /opt/ros/kinetic/setup.bash && source ../devel/setup.bash && roslaunch guiding_as show_as.launch