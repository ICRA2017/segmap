## *SegMap*

[![Travis CI Build Status](https://travis-ci.org/ICRA2017/segmap.svg?branch=reproducible)](https://travis-ci.org/ICRA2017/segmap)

*SegMap* is a map representation based on 3D segments allowing for robot localization, environment reconstruction, and semantics extraction. The *SegMap* code is open-source (BSD License) and has been tested under Ubuntu 14.04 & 16.04 and ROS Indigo & Kinetic. 

Please consult our [paper](https://arxiv.org/pdf/1609.07720v1.pdf), [video](https://www.youtube.com/watch?v=iddCgYbgpjE) and [wiki](https://github.com/ethz-asl/segmatch/wiki) for the algorithm description and for instructions on running demonstrations.

### News

*Note 25.04.2018: We have open sourced the implementation behind our RA-L paper "Incremental Segment Based Localization in 3D Point Clouds"!  See the [paper](https://ieeexplore.ieee.org/document/8283725/) and a [video demonstration](https://youtu.be/cHfs3HLzc2Y). The updated documentation and tutorials are coming soon!* 

__*Note 20.4.2018: This repository has been renamed SegMap, to reflect the latest development presented in our paper "*SegMap: 3D Segment Mapping using Data-Driven Descriptors*". See the [video demonstration](https://youtu.be/CMk4w4eRobg). For clarity: in the instructions below, the name *SegMatch* will still be used to refer the the first iteration of the pipeline presented in the original *SegMatch* [paper](https://arxiv.org/pdf/1609.07720v1.pdf) ([video](https://www.youtube.com/watch?v=iddCgYbgpjE)). The updated documentation and tutorials are coming soon!*__

We recently uploaded a second [video](https://www.youtube.com/watch?v=JJhEkIA1xSE) featuring *SegMatch* in a multi-robot configuration. 

### Compiling *SegMatch*
The following configuration was tested under Ubuntu 14.04 and ROS indigo. Please see the final note if you want to compile under ROS Kinetic.

First install the required system packages:
```
$ sudo apt-get install python-wstool doxygen autoconf
```
Then use wstool for installing catkin dependencies:
```
$ cd ~/catkin_ws/src
$ wstool init
$ wstool merge segmap/dependencies.rosinstall
$ wstool update
```
Finally build the *segmapper* package which will compile all *SegMatch* modules:
```
$ cd ~/catkin_ws
$ catkin build -DCMAKE_BUILD_TYPE=Release segmapper
```
See this link for installing [catkin_tools](http://catkin-tools.readthedocs.io/en/latest/installing.html). Building dependencies will require some time according to which new packages need to be built (eg. Building the `pcl_catkin` package can take up to two hours). Building `pcl_catkin` might fail if you do not have sufficient RAM. It can help to add `-j2` to catkin build in order to limit the parallel jobs and reduce memory usage.

Consult the [wiki](https://github.com/ethz-asl/segmatch/wiki) for instructions on running the demonstrations.

Note: If you are using ROS Kinetic, you might want to run the following command in your catkin workspace prior to building the packages:
```
$ catkin config --merge-devel
```

### Contributing to *SegMatch*

We would be very grateful if you would contribute to the code base by reporting bugs, leaving comments and proposing new features through issues and pull requests. Please see the dedicated [wiki page](https://github.com/ethz-asl/segmatch/wiki/Contributing-to-SegMatch) on this topic and feel free to get in touch at rdube(at)ethz.ch. Thank you!

### Citing *SegMatch*

Thank you for citing our *SegMatch* paper if you use any of this code: 
```
@inproceedings{segmatch2017,
  title={SegMatch: Segment based place recognition in 3D point clouds},
  author={Dub{\'e}, Renaud and Dugas, Daniel and Stumm, Elena and Nieto, Juan and Siegwart, Roland and Cadena, Cesar},
  booktitle={International Conference on Robotics and Automation (ICRA)},
  pages={5266--5272},
  year={2017},
  organization={IEEE}
}
```
