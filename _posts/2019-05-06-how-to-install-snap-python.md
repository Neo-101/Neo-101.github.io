---
author: Neo-101
---

This article briefly introduces how to install ESA's SNAP and configure snap-python on Mac and Windows.

# Mac

### 1. Install Anaconda

### 2. Install Java and JDK

### 3. Install jpy

Jpy is a **bi-directional** Python-Java Bridge. Download and follow the guide from [here](https://github.com/bcdev/jpy).

If some error message containing 'mvn' occurs, it may because the absence of Maven. It can be downloaded from [here](https://maven.apache.org/). 

After the installation of jpy, there will be a `build` directory and a `dist` directory in the `jpy-master` directory. 

Copy `build` directory into Anaconda's `site-packages` directory. It maybe `/Users/USERNAME/anaconda3/lib/PYTHON3.X/site-packages` or something else. 
### 4. Install SNAP

Download and install SNAP from [ESA](http://step.esa.int/main/download/).

Note that there is **Select Python** step during installation as the following picture shows. Even the Python version of Anaconda is not supported according to the description, it is recommended to **select the checkbox** of *Configure SNAP for use with Python*. The reason is in next step.

![My helpful screenshot](/assets/images/snap_installation_select_python.png)

### 5. Configure snap-python

The steps of installation of snap-python are [here](https://github.com/senbox-org/snap-engine/tree/master/snap-python/src/main/resources). But it maybe out-of-date. It says that `snappy` can be installed as follows:
```
export SNAP_HOME=<path to your SNAP 5 installation>
cd $SNAP_HOME/modules/snap-python-5.0/snappy
python3 setup.py install --user
```
But there is **no** directory named as `snap-python-x.x` or something similar in `$SNAP_HOME/modules/`. 

Instead, as the installation guide showed in last screenshot, `snappy` is in the directory `/Users/USERNAME/.snap/snap-python`.
