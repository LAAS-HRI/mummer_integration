FROM ros:kinetic
# place here your application's setup specifics

SHELL ["/bin/bash", "-c"]

RUN apt-get update && apt-get install ros-kinetic-qt-build && apt-get install -y ros-kinetic-opencv3

# Create & init catkin workspace
RUN source /opt/ros/kinetic/setup.bash && cd && mkdir -p catkin_ws/src && cd ~/catkin_ws/ && catkin_make && source ./devel/setup.bash
RUN mkdir src && cd ./src/ && mkdir ontology && cd ./ontology && git clone https://github.com/sarthou/ontologenius.git
RUN git clone https://github.com/LAAS-HRI/semantic-route-description.git

RUN cd ~/catkin_ws && source ./devel/setup.bash && catkin_make

RUN cd ~/catkin_ws/devel/lib/ && mkdir python2.7 && cd python2.7 && mkdir site-packages && export PYTHONPATH=~/catkin_ws/devel/lib/python2.7/site-packages:$PYTHONPATH && echo $PYTHONPATH
#RUN mkdir ~/ontology_deps/ && cd ~/ontology_deps/ && git clone git://github.com/kennethreitz/requests.git && cd requests && python setup.py install --prefix=~/catkin_ws/devel

#CMD [ "roslaunch", "perspectives mummer.launch" ]
