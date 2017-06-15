# icub-models
Repository containing models generated by https://github.com/robotology-playground/icub-model-generator . 

## Usage 
The model in the repo can be used either directly from the repo, or by installing them.
While the files can be used directly by pointing your software to their location, they are 
tipically used by software that uses either YARP or ROS. For this reason, the models 
are installed as part of the `iCub` ROS package following the instructions in 
https://github.com/gerkey/ros1_external_use#installing-for-use-by-tools-like-roslaunch 
and following the YARP guidelines on installing configuration files in http://www.yarp.it/yarp_data_dirs.html .
To make sure that this models are found by the software even when they are not installed in 
system directories, tipically the [`YARP_DATA_DIRS`](http://www.yarp.it/yarp_data_dirs.html) and the 
[`ROS_PACKAGE_PATH`](http://wiki.ros.org/ROS/EnvironmentVariables#ROS_PACKAGE_PATH) enviromental variables are modified appropriatly. 


### From the source repo
In case the models are used from the repo, if <icub-models> is the location of the repo, then 
<icub-models>/iCub needs to be appened to the YARP_DATA_DIRS env variable and <icub-models> needs to be appended
to ROS_PACKAGE_PATH env variable. On *nix system, this can be achived by adding to the `.bashrc` or equivalent 
file the following two lines:
~~~
export YARP_DATA_DIRS=${YARP_DATA_DIRS}:<icub-models>/iCub 
export ROS_PACKAGE_PATH=${ROS_PACKAGE_PATH}:<icub-models> 
~~~

### By installing the models 
To install the models, you must use `CMake`. 
The installation can be performed by the following commands:
~~~
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=<prefix> ..
cmake --build . --target install 
~~~
Once you installed to a given prefix, you can modify the `YARP_DATA_DIRS` and `ROS_PACKAGE_PATH` enviromental variables as in the following:
~~~
export YARP_DATA_DIRS=${YARP_DATA_DIRS}:<prefix>/share/iCub 
export ROS_PACKAGE_PATH=${ROS_PACKAGE_PATH}:<prefix> 
~~~
