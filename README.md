icub-gazebo
===========

Preliminary files for simulation of the iCub humanoid robot in Gazebo (meshes courtesy of Joseph Salini - UPMC). Note that these models are compatible only with the Gazebo version that use SDF 1.5

Installation
------------
Install [gazebo_yarp_plugins](https://github.com/robotology/gazebo_yarp_plugins)

Clone this repository:
```
git clone https://github.com/robotology/icub-gazebo.git
```


To let Gazebo know the existence of the models, you can add it to the `GAZEBO_MODEL_PATH` enviroment variable. You can add a line to the `.bashrc` file in your home:
```
if [ -z "$GAZEBO_MODEL_PATH" ]; then
    export GAZEBO_MODEL_PATH=/home/user/path/to/icub-gazebo
else
    export GAZEBO_MODEL_PATH=${GAZEBO_MODEL_PATH}:/home/user/path/to/icub-gazebo
fi
```

Usage
-----
As the iCub Gazebo models uses [Yarp](http://yarp.it), remember to start it before starting the simulation, using the following command in a console:
```
yarpserver
```

Then, run Gazebo with the world file included in the world directory:
```
gazebo ./icub-gazebo/world/icub.world
```
or simply drag and drop the `iCub (no hands)` or `iCub with hands` models from the Insert tab in Gazebo.
The same instructions work also for the icub_legs model.

Model generation
----------------
The model store in this repo are actually the result of a process of extraction of kinematics parameters, inertial parameters and meshes from the original CAD files of the iCub robot. There are currently two ways of generating this models:

* The legacy generation system based on kinematics and dynamics parameters hardcoded in the legacy iDyn library, combined with meshes manually extracted from the CAD models, available at https://github.com/robotology-playground/icub-model-generator . This process is used to generate the models for the iCub version 1 model, that is available as `icub` in this repository.
* The new generation system that converts from actual Creo CAD models of the iCub, described in http://wiki.icub.org/wiki/Creo_Mechanism_to_URDF . This system is currently under testing, and will be used for iCub 2.5 and all the following version of iCub. If you have an iCub and you want to know if a precise model for your system can be extracted from CAD models, please [open an new issue in the `icub-support` repository](https://github.com/robotology/icub-support/issues/new). At the moment, no model generated with this new system is available in this repository.
