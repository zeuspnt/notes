## Common Errors
```
In file included from /extHDD1/workspace/openpose/src/openpose/face/faceExtractorCaffe.cpp:2:0:
/extHDD1/workspace/openpose/3rdparty/caffe/include/caffe/blob.hpp:9:34: fatal error: caffe/proto/caffe.pb.h: No such file or directory
compilation terminated.
src/openpose/face/CMakeFiles/openpose_face.dir/build.make:134: recipe for target 'src/openpose/face/CMakeFiles/openpose_face.dir/faceExtractorCaffe.cpp.o' failed
make[2]: *** [src/openpose/face/CMakeFiles/openpose_face.dir/faceExtractorCaffe.cpp.o] Error 1
make[2]: *** Waiting for unfinished jobs....
[ 16%] Linking CXX shared library libopenpose_3d.so
CMakeFiles/Makefile2:399: recipe for target 'src/openpose/face/CMakeFiles/openpose_face.dir/all' failed
make[1]: *** [src/openpose/face/CMakeFiles/openpose_face.dir/all] Error 2
[ 16%] Built target openpose_3d
[ 17%] Linking CXX shared library libopenpose_calibration.so
[ 17%] Built target openpose_calibration
Makefile:127: recipe for target 'all' failed
make: *** [all] Error 2
```

Fix:
You need to generate caffe.pb.h manually using protoc as follows.

In the directory you installed Caffe to
```
protoc src/caffe/proto/caffe.proto --cpp_out=.
mkdir include/caffe/proto
mv src/caffe/proto/caffe.pb.h include/caffe/proto
```


```bash
CXX src/caffe/solvers/adagrad_solver.cpp
CXX src/caffe/solvers/adam_solver.cpp
CXX src/caffe/solvers/rmsprop_solver.cpp
CXX src/caffe/solvers/nesterov_solver.cpp
CXX src/caffe/net.cpp
AR -o .build_release/lib/libcaffe.a
LD -o .build_release/lib/libcaffe.so.1.0.0
/usr/bin/ld: cannot find -lcblas
/usr/bin/ld: cannot find -latlas
collect2: error: ld returned 1 exit status
Makefile:587: recipe for target '.build_release/lib/libcaffe.so.1.0.0' failed
make: *** [.build_release/lib/libcaffe.so.1.0.0] Error 1

```

fix
sudo apt-get install libatlas-base-dev
```bash

```
