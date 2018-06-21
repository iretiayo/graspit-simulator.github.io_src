GraspIt! Installation - Ubuntu Linux with ROS
---------------------------------------------

GraspIt! can be integrated into a ros workspace via two ros packages:

 - https://github.com/graspit-simulator/graspit_interface
 - https://github.com/graspit-simulator/graspit_commander

The setup requires globally installation of GraspIt!.

GraspIt Setup:
--------------

.. code::

  git clone https://github.com/graspit-simulator/graspit.git
  cd graspit
  mkdir build
  cd build
  cmake ..
  make -j5
  sudo make install

You might need to add /usr/local/lib to the loaded library path as in:

.. code::

  export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH

You will also want to set the GRASPIT environment variable:

.. code::

  export GRASPIT=~/.graspit

On Linux, you can add both of these lines to the bottom of your ~/.bashrc

ROS Setup:
----------

After running the GraspIt! Setup as explained above, the following details how to setup GraspIt! to work with ROS.

.. code::

  //create ros workspace
  mkdir -p graspit_ros_ws/src
  cd graspit_ros_ws/src

  source /opt/ros/indigo/setup.bash
  catkin_init_workspace . 

  //clone packages
  git clone https://github.com/graspit-simulator/graspit_interface.git
  git clone https://github.com/graspit-simulator/graspit_commander.git

  //build workspace
  cd graspit_ros_ws
  catkin_make


Launching graspit_interface:
----------------------------

.. code::

  source devel/setup.bash
  roslaunch graspit_interface graspit_interface.launch


Then you can view available services and topics provided by the graspit_interface via:

.. code::

  rostopic list
  rosservice list
