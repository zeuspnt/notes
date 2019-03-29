## Ubuntu

Need to install swig.

```bash
$ sudo apt install swig
```

You need to build pafprocess module which is written in c++. It will be used for post processing.

```bash
$ swig -python -c++ pafprocess.i && python3 setup.py build_ext --inplace
```

## MacOS

Install swig.

```bash
$ brew install swig
```

Build pafprocess

```bash
$ swig -python -c++ pafprocess.i && python3 setup.py build_ext --inplace
```
