## Getting Caffe
```git clone https://github.com/BVLC/caffe```

You will now find the caffe folder in your Home directory.

We have to make a copy of Makefile.config.example, which we generally name as, Makefile.config to which we can make changes based on our system settings.

```cd caffe
cp Makefile.config.example Makefile.config
```
Making Changes In Makefile.config
Make sure you are still in the caffe directory, then use this command to open Makefile.config

```gedit Makefile.config```

Note- The following line numbers may vary.
On line 8, uncomment ```CPU_ONLY := 1```

On Line 21, uncomment OPENCV_VERSION := 3 if you're using OpenCV 3 or above. If you aren't sure, try this in another terminal

```$ python
>>> import cv2
>>> cv2.__version__
'3.0.0' 
```

On line 25, uncomment ```CUSTOM_CXX := g++```

On line 50, set ```BLAS := open``` if you've installed OpenBLAS, or let it be the default ```BLAS := atlas``` if you've installed Atlas.

On line 94, change

```INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include```

to

```INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include  /usr/include/hdf5/serial ```

On line 95, change
```LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib```

to

```LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib  /usr/lib/x86_64-linux-gnu/hdf5/serial```

or

```LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib /usr/lib/x86_64-linux-gnu /usr/lib/x86_64-linux-gnu/hdf5/serial```

This should resolve hdf5 errors when running make

Now within the caffe directory, run the following one after the other

```make all
make test
make runtest
```


These should run smoothly without any errors. If you do however, encounter errors, refer the ones at the end of this post or elsewhere to resolve them.

Make sure to REMOVE BUILD every time you resolve an error, and run those three commands again to rebuild.

This is VERY IMPORTANT, otherwise the errors will persist.

To remove build,

```rm -rf ./build*/```

Once all three run without errors, while in the caffe directory, type

```make pycaffe```

This will build a python wrapper. You will also find a python folder within the caffe folder now.

To use caffe within python, export its path as

```export PYTHONPATH=~/Home/_username_/caffe/python:$PYTHONPATH```

Replace _username_ with the your username in the system.

Once you've done this, run the python terminal and import caffe

```
>>> import caffe
>>>
```
This, should work. If it throws a 'module not found' error, check if it has been appended in pythonpath properly by typing

```>>> import sys
>>> sys.path
['', '/home/nikita/caffe/python', '/home/nikita', '/usr/lib/python2.7', '/usr/lib/python2.7/plat-x86_64-linux-gnu', '/usr/lib
/python2.7/lib-tk', '/usr/lib/python2.7/lib-old', '/usr/lib/python2.7/lib-dynload', '/home/nikita/.local/lib/python2.7/site-
packages']
```

## Install Caffe with Intel CPU (MKL - Math Kernel Library)

```
Intel MKL: http://software.intel.com/en-us/intel-mkl
Install MKL.
Set up MKL environment (Details: Linux, OS X). Example: source /opt/intel/mkl/bin/mklvars.sh intel64
Set BLAS := mkl in Makefile.config
```

### Error when run make runtest:

```
.build_release/tools/caffe: error while loading shared libraries: libmkl_rt.so: cannot open shared object file: No such file or directory
Makefile:537: recipe for target 'runtest' failed
```
F
```
export LD_LIBRARY_PATH="/opt/intel/mkl/lib/intel64"
```


```bash
make pycaffe

CXX/LD -o python/caffe/_caffe.so python/caffe/_caffe.cpp
python/caffe/_caffe.cpp:10:10: fatal error: numpy/arrayobject.h: No such file or directory
 #include <numpy/arrayobject.h>
          ^~~~~~~~~~~~~~~~~~~~~
compilation terminated.
Makefile:522: recipe for target 'python/caffe/_caffe.so' failed
make: *** [python/caffe/_caffe.so] Error 1
```

# fix

python2 

```bash
sudo apt-get install python-numpy
```

python3

```bash
sudo apt-get install python3-numpy
```
