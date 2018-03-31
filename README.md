# mummer_integration
Contains the dockerfiles and the wiki for mummer first integration

## Installation instructions

First, install docker ([instructions here](https://docs.docker.com/install/linux/docker-ce/ubuntu/))

Then, clone the repository :

```
git clone https://github.com/LAAS-HRI/mummer_integration.git
```
And build the dockerfiles with :

```
cd mummer_integration
docker build --tag laas:navigation ./navigation/
docker build --tag laas:planning ./planning/
docker build --tag laas:situation_assessment ./situation_assessment/
docker build --tag laas:onthology ./onthology/
docker build --tag laas:supervision ./supervision/
docker build --tag laas:full ./full/
```

## Setup and explanations of the packages

The [wiki home](https://github.com/LAAS-HRI/mummer_integration/wiki) will introduce you the global architecture and then each component will be described respectively :

[**Navigation**](https://github.com/LAAS-HRI/mummer_integration/wiki/Navigation)

[**Ontology**](https://github.com/LAAS-HRI/mummer_integration/wiki/Onthology)

[**Planning**](https://github.com/LAAS-HRI/mummer_integration/wiki/Planning)

[**Situation assessment**](https://github.com/LAAS-HRI/mummer_integration/wiki/Situation-assessment)

[**Supervision**](https://github.com/LAAS-HRI/mummer_integration/wiki/Supervision)

Finally, the experimentation setup and the material that can be used will be described briefly :  

[**Experiment setup**](https://github.com/LAAS-HRI/mummer_integration/wiki/Experiment-setup)

* [Global Setup (Mall simulation)]()
* [Motion capture system]()
* [Eye tracking system]()