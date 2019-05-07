---
author: Neo-101
---

This article briefly introduces how to install ESA's SNAP and configure snap-python on Mac and Windows.

# Mac

### 1. Install Anaconda

Anaconda is a good choice to handle different versions of Python and packages conveniently. It can be downloaded from [here](https://www.anaconda.com/distribution/).

Since SNAP only supports Python versions 2.7, 3.3 and 3.4 by the date of this article (2019-05-07), we should create an environment of supported Python version to use SNAP with Python as follows:

```
conda create -n SNAP python=3.4
```

This environment may be in `/Users/<your username>/anaconda3/envs/SNAP/` or somewhere similar.

### 2. Install JDK

SNAP bases on Java. So JDK is needed and it can be downloaded from [here](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

After installation of JDK, set two environment vaiables in configuration file for bash shell. 

In `~/.bash_rc` or `~/.bash_profile`, add two lines as follows:

```
export JDK_HOME="/Library/Java/JavaVirtualMachines/jdk-12.0.1.jdk/Contents/Home"
export JAVA_HOME="/Library/Java/JavaVirtualMachines/jdk-12.0.1.jdk/Contents/Home"
```

The name of JDK's directory may be a little different. but it doesn't matter.

After that, save file and restart bash. The two new environment varaiables can be checked by commands like:

```
echo $JDK_HOME
echo $JAVA_HOME
```

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

So get into the directort `/Users/USERNAME/.snap/snap-python/snappy`, and install `snappy` as follows:

```
python3 setup.py install --user
```

Note that `snappy` may be installed into somewhere like `/Users/USERNAME/.local/lib/python3.7/site-packages/snappy`. But it should bestly be installed into directory `site-packages` under Anaconda. This problem can be solved simply by copy files under somewhere like `/Users/USERNAME/.local/lib/python3.7/site-packages` to `/Users/USERNAME/anaconda3/lib/PYTHON3.X/site-packages`.


