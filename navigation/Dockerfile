FROM ros:kinetic

SHELL ["/bin/bash", "-c"]

RUN apt-get update && apt-get install -y ros-kinetic-tf ros-kinetic-move-base \
    ros-kinetic-costmap-converter ros-kinetic-interactive-markers \
    ros-kinetic-tf-conversions ros-kinetic-libg2o ros-kinetic-rosbridge-server \
    ros-kinetic-map-server ros-kinetic-tf2-web-republisher ros-kinetic-global-planner

RUN mkdir catkin_ws && mkdir catkin_ws/src
WORKDIR catkin_ws/src

ADD https://api.github.com/repos/guilhembn/mummer_navigation/git/refs/heads/master \
    https://api.github.com/repos/guilhembn/tf_hanp/git/refs/heads/master \
    https://api.github.com/repos/guilhembn/laas_navigation/git/refs/heads/master \
    https://api.github.com/repos/guilhembn/hateb_local_planner/git/refs/heads/time-to-goal \
    https://api.github.com/repos/LAAS-HRI/perspectives_msgs/git/refs/heads/master /tmp/    

RUN git clone  https://github.com/guilhembn/mummer_navigation && \
    git clone  https://github.com/guilhembn/tf_hanp.git && \
    git clone  https://github.com/guilhembn/laas_navigation.git && \
    git clone -b time-to-goal https://github.com/guilhembn/hateb_local_planner.git teb_local_planner && \
    git clone -b time-to-goal https://github.com/harmishhk/hanp_msgs.git && \
    git clone https://github.com/harmishhk/hanp_prediction.git && \
    git clone https://github.com/LAAS-HRI/perspectives_msgs.git

RUN source /opt/ros/kinetic/setup.bash && pwd && ls && cd .. && catkin_make

COPY ./pynaoqi_sdk/pynaoqi-python2.7-2.5.5.5-linux64.tar.gz /tmp/pynaoqi-python2.7-2.5.5.5-linux64.tar.gz
COPY ./pynaoqi_sdk/setup_pynaoqi.bash ../

RUN cd /opt && tar xzvf /tmp/pynaoqi-python2.7-2.5.5.5-linux64.tar.gz

WORKDIR ../

CMD source /opt/ros/kinetic/setup.bash && source devel/setup.bash && source setup_pynaoqi.bash && roslaunch mummer_navigation mummer_navigation.launch
