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

```bash
sudo apt-get install libatlas-base-dev
```

# Error

```bash
Linking CXX shared module openpose_python.cpython-36m-x86_64-linux-gnu.so
/usr/bin/ld: ../../src/openpose/libopenpose.a(scaleAndSizeExtractor.cpp.o): relocation R_X86_64_PC32 against symbol `_ZTVN2op21ScaleAndSizeExtractorE' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: final link failed: Bad value
collect2: error: ld returned 1 exit status
python/openpose/CMakeFiles/openpose_python.dir/build.make:151: recipe for target 'python/openpose/openpose_python.cpython-36m-x86_64-linux-gnu.so' failed
make[2]: *** [python/openpose/openpose_python.cpython-36m-x86_64-linux-gnu.so] Error 1
CMakeFiles/Makefile2:1167: recipe for target 'python/openpose/CMakeFiles/openpose_python.dir/all' failed
make[1]: *** [python/openpose/CMakeFiles/openpose_python.dir/all] Error 2
Makefile:129: recipe for target 'all' failed
make: *** [all] Error 2
```

# Fix
 - make pycaffe in caffe after make all


# Error

```bash
LD -o .build_release/lib/libcaffe.so.1.0.0
CXX/LD -o .build_release/tools/extract_features.bin
CXX/LD -o .build_release/tools/compute_image_mean.bin
CXX/LD -o .build_release/tools/caffe.bin
CXX/LD -o .build_release/tools/convert_imageset.bin
CXX/LD -o .build_release/tools/upgrade_net_proto_binary.bin
CXX/LD -o .build_release/tools/upgrade_net_proto_text.bin
CXX/LD -o .build_release/tools/upgrade_solver_proto_text.bin
CXX/LD -o .build_release/examples/siamese/convert_mnist_siamese_data.bin
CXX/LD -o .build_release/examples/cpp_classification/classification.bin
CXX/LD -o .build_release/examples/cifar10/convert_cifar_data.bin
CXX/LD -o .build_release/examples/mnist/convert_mnist_data.bin
.build_release/lib/libcaffe.so: undefined reference to `cv::imread(cv::String const&, int)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imencode(cv::String const&, cv::_InputArray const&, std::vector<unsigned char, std::allocator<unsigned char> >&, std::vector<int, std::allocator<int> > const&)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imdecode(cv::_InputArray const&, int)'
collect2: error: ld returned 1 exit status
Makefile:640: recipe for target '.build_release/tools/upgrade_net_proto_text.bin' failed
make: *** [.build_release/tools/upgrade_net_proto_text.bin] Error 1
make: *** Waiting for unfinished jobs....
.build_release/lib/libcaffe.so: undefined reference to `cv::imread(cv::String const&, int)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imencode(cv::String const&, cv::_InputArray const&, std::vector<unsigned char, std::allocator<unsigned char> >&, std::vector<int, std::allocator<int> > const&)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imdecode(cv::_InputArray const&, int)'
collect2: error: ld returned 1 exit status
Makefile:640: recipe for target '.build_release/tools/convert_imageset.bin' failed
make: *** [.build_release/tools/convert_imageset.bin] Error 1
.build_release/lib/libcaffe.so: undefined reference to `cv::imread(cv::String const&, int)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imencode(cv::String const&, cv::_InputArray const&, std::vector<unsigned char, std::allocator<unsigned char> >&, std::vector<int, std::allocator<int> > const&)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imdecode(cv::_InputArray const&, int)'
collect2: error: ld returned 1 exit status
Makefile:640: recipe for target '.build_release/tools/caffe.bin' failed
make: *** [.build_release/tools/caffe.bin] Error 1
.build_release/lib/libcaffe.so: undefined reference to `cv::imread(cv::String const&, int)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imencode(cv::String const&, cv::_InputArray const&, std::vector<unsigned char, std::allocator<unsigned char> >&, std::vector<int, std::allocator<int> > const&)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imdecode(cv::_InputArray const&, int)'
collect2: error: ld returned 1 exit status
Makefile:640: recipe for target '.build_release/tools/compute_image_mean.bin' failed
make: *** [.build_release/tools/compute_image_mean.bin] Error 1
.build_release/lib/libcaffe.so: undefined reference to `cv::imread(cv::String const&, int)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imencode(cv::String const&, cv::_InputArray const&, std::vector<unsigned char, std::allocator<unsigned char> >&, std::vector<int, std::allocator<int> > const&)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imdecode(cv::_InputArray const&, int)'
collect2: error: ld returned 1 exit status
.build_release/lib/libcaffe.so: undefined reference to `cv::imread(cv::String Makefile:645: recipe for target '.build_release/examples/cifar10/convert_cifar_data.bin' failed
const&, make: *** [.build_release/examples/cifar10/convert_cifar_data.bin] Error 1
int)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imencode(cv::String const&, cv::_InputArray const&, std::vector<unsigned char, std::allocator<unsigned char> >&, std::vector<int, std::allocator<int> > const&)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imdecode(cv::_InputArray const&, int)'
collect2: error: ld returned 1 exit status
Makefile:645: recipe for target '.build_release/examples/siamese/convert_mnist_siamese_data.bin' failed
make: *** [.build_release/examples/siamese/convert_mnist_siamese_data.bin] Error 1
.build_release/lib/libcaffe.so: undefined reference to `cv::imread(cv::String const&, int)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imencode(cv::String const&, cv::_InputArray const&, std::vector<unsigned char, std::allocator<unsigned char> >&, std::vector<int, std::allocator<int> > const&)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imdecode(cv::_InputArray const&, int)'
collect2: error: ld returned 1 exit status
Makefile:640: recipe for target '.build_release/tools/upgrade_net_proto_binary.bin' failed
make: *** [.build_release/tools/upgrade_net_proto_binary.bin] Error 1
.build_release/lib/libcaffe.so: undefined reference to `cv::imread(cv::String const&, int)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imencode(cv::String const&, cv::_InputArray const&, std::vector<unsigned char, std::allocator<unsigned char> >&, std::vector<int, std::allocator<int> > const&)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imdecode(cv::_InputArray const&, int)'
collect2: error: ld returned 1 exit status
Makefile:645: recipe for target '.build_release/examples/mnist/convert_mnist_data.bin' failed
make: *** [.build_release/examples/mnist/convert_mnist_data.bin] Error 1
.build_release/lib/libcaffe.so: undefined reference to `cv::imread(cv::String const&, int)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imencode(cv::String const&, cv::_InputArray const&, std::vector<unsigned char, std::allocator<unsigned char> >&, std::vector<int, std::allocator<int> > const&)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imdecode(cv::_InputArray const&, int)'
collect2: error: ld returned 1 exit status
Makefile:640: recipe for target '.build_release/tools/upgrade_solver_proto_text.bin' failed
make: *** [.build_release/tools/upgrade_solver_proto_text.bin] Error 1
.build_release/examples/cpp_classification/classification.o: In function `main':
classification.cpp:(.text.startup+0x236): undefined reference to `cv::imread(cv::String const&, int)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imencode(cv::String const&, cv::_InputArray const&, std::vector<unsigned char, std::allocator<unsigned char> >&, std::vector<int, std::allocator<int> > const&)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imdecode(cv::_InputArray const&, int)'
collect2: error: ld returned 1 exit status
Makefile:645: recipe for target '.build_release/examples/cpp_classification/classification.bin' failed
make: *** [.build_release/examples/cpp_classification/classification.bin] Error 1
.build_release/lib/libcaffe.so: undefined reference to `cv::imread(cv::String const&, int)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imencode(cv::String const&, cv::_InputArray const&, std::vector<unsigned char, std::allocator<unsigned char> >&, std::vector<int, std::allocator<int> > const&)'
.build_release/lib/libcaffe.so: undefined reference to `cv::imdecode(cv::_InputArray const&, int)'
collect2: error: ld returned 1 exit status
Makefile:640: recipe for target '.build_release/tools/extract_features.bin' failed
make: *** [.build_release/tools/extract_features.bin] Error 1
```


