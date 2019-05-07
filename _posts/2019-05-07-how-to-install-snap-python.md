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

This environment may be in `~/anaconda3/envs/SNAP/` or somewhere similar.

Then we enter this new environment with commands as follows:

```
conda activate SNAP
```

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

Copy `build` directory into `site-packages` directory of Python 3.4 environment we created in step 1. It maybe `~/anaconda3/envs/SNAP/lib/python3.4/site-packages` or somewhere similar. 

### 4. Install SNAP

Download and install SNAP from [ESA](http://step.esa.int/main/download/).

Note that there is **Select Python** step during installation as the following screenshot shows. **Select the checkbox** of *Configure SNAP for use with Python*. Python executable can be found by command:

```
which python
```

The path should be somewhere like `~/anaconda3/envs/SNAP/bin/python`. 

![My helpful screenshot](/assets/images/snap_installation_select_python.png =360x)

### 5. Configure snap-python

The steps of installation of snap-python are [here](https://github.com/senbox-org/snap-engine/tree/master/snap-python/src/main/resources). But it maybe out-of-date. It says that `snappy` can be installed as follows:
```
export SNAP_HOME=<path to your SNAP 5 installation>
cd $SNAP_HOME/modules/snap-python-5.0/snappy
python3 setup.py install --user
```
But there is **no** directory named as `snap-python-x.x` or something similar in `$SNAP_HOME/modules/`. 

Instead, as the installation guide showed in last screenshot, `snappy` is in the directory `~/.snap/snap-python`.

First, get into the directory `jpy-master` (where we download jpy from GitHub) and type commands:

```
cp dist/*.whl ~/.snap/snap-python/snappy
```

Next, set up snappy like this:

```
~/Applications/snap/bin/snappy-conf ~/anaconda/envs/SNAP/bin/python
```

OS X may tell us it needed a legacy java and send us a [webpage](https://support.apple.com/kb/DL1572) where we can download it.

Then install `snappy` as follows:

```
cd ~/.snap/snap-python/snappy
python setup.py install --user
```

Last but not least, we need test whether snap-python is configured correctly like this:

```
python
import snappy
```

If there is no error message, we have successfully installed SNAP and configured snap-python.

*Have fun!*
