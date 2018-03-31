FROM ros:kinetic
# place here your application's setup specifics

RUN echo "Install Underworlds dependencies..."

RUN apt-get update && apt-get install -y \
    python-pyassimp \
    python-opengl \
    python-pygame \
    && rm -rf /var/lib/apt/lists/

RUN echo "Install Underworlds from official repository..."

RUN mkdir ~/situation_assessment_deps/ && cd ~/situation_assessment_deps/

RUN git clone https://github.com/underworlds-robot/underworlds.git
RUN cd underworlds && python setup.py install

RUN echo "Install perspectives dependencies..."



CMD [ "roslaunch", "perspectives mummer.launch" ]
