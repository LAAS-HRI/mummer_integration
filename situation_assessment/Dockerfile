FROM ros:kinetic
# place here your application's setup specifics

RUN echo "Install Underworlds dependencies..."

RUN apt-get update && apt-get install -y \
    python-pyassimp \
    python-opengl \
    python-pygame \
    ros-kinetic-ar-track-alvar \
    && rm -rf /var/lib/apt/lists/

RUN pip install argcomplete

RUN pip install grpcio

RUN echo "Install Underworlds from official repository..."

RUN mkdir ~/situation_assessment_deps/ && cd ~/situation_assessment_deps/

RUN git clone https://github.com/underworlds-robot/underworlds.git
RUN cd underworlds && python setup.py install

RUN echo "Install Perspectives dependencies..."

RUN cd .. && git clone https://github.com/bulletphysics/bullet3
RUN cd bullet3 && python setup.py install
RUN pip install pybullet

RUN pip install lxml

RUN echo "Create catkin workspace..."

RUN cd && mkdir -p catkin_ws/src
RUN cd catkin_ws && catkin_init_workspace

CMD [ "roslaunch", "perspectives mummer.launch" ]
