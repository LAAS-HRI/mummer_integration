FROM ros:kinetic

SHELL ["/bin/bash", "-c"]

RUN apt-get update && apt-get install -y ros-kinetic-tf ros-kinetic-move-base \
    ros-kinetic-costmap-converter ros-kinetic-interactive-markers \
    ros-kinetic-tf-conversions ros-kinetic-libg2o ros-kinetic-rosbridge-server \
    ros-kinetic-map-server ros-kinetic-tf2-web-republisher ros-kinetic-global-planner

RUN mkdir catkin_ws && mkdir catkin_ws/src
WORKDIR catkin_ws/src

RUN git clone  https://github.com/guilhembn/mummer_navigation && \
    git clone  https://github.com/guilhembn/tf_hanp.git && \
    git clone  https://github.com/guilhembn/laas_navigation.git && \
    git clone -b time-to-goal https://github.com/guilhembn/hateb_local_planner.git teb_local_planner && \
    git clone -b time-to-goal https://github.com/harmishhk/hanp_msgs.git && \
    git clone https://github.com/harmishhk/hanp_prediction.git && \
    git clone https://github.com/LAAS-HRI/perspectives_msgs.git

RUN source /opt/ros/kinetic/setup.bash && pwd && ls && cd .. && catkin_make

WORKDIR ../

CMD source /opt/ros/kinetic/setup.bash && source devel/setup.bash && roslaunch mummer_navigation mummer_navigation.launch
