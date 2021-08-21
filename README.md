# dlib C++ library [![Travis Status](https://travis-ci.org/davisking/dlib.svg?branch=master)](https://travis-ci.org/davisking/dlib)

Dlib is a modern C++ toolkit containing machine learning algorithms and tools for creating complex software in C++ to solve real world problems. See [http://dlib.net](http://dlib.net) for the main project documentation and API reference.



## Compiling dlib C++ example programs

Go into the examples folder and type:

```bash
mkdir build; cd build; cmake .. ; cmake --build .
```

That will build all the examples.
If you have a CPU that supports AVX instructions then turn them on like this:

```bash
mkdir build; cd build; cmake .. -DUSE_AVX_INSTRUCTIONS=1; cmake --build .
```

Doing so will make some things run faster.

Finally, Visual Studio users should usually do everything in 64bit mode.  By default Visual Studio is 32bit, both in its outputs and its own execution, so you have to explicitly tell it to use 64bits.  Since it's not the 1990s anymore you probably want to use 64bits.  Do that with a cmake invocation like this:
```bash
cmake .. -G "Visual Studio 14 2015 Win64" -T host=x64 
```

## Compiling your own C++ programs that use dlib

The examples folder has a [CMake tutorial](https://github.com/davisking/dlib/blob/master/examples/CMakeLists.txt) that tells you what to do.  There are also additional instructions on the [dlib web site](http://dlib.net/compile.html).

Alternatively, if you are using the [vcpkg](https://github.com/Microsoft/vcpkg/) dependency manager you can download and install dlib with CMake integration in a single command:
```bash
vcpkg install dlib
```

## Compiling dlib Python API

Before you can run the Python example programs you must compile dlib. Type:

```bash
python setup.py install
```


## Running the unit test suite

Type the following to compile and run the dlib unit test suite:

```bash
cd dlib/test
mkdir build
cd build
cmake ..
cmake --build . --config Release
./dtest --runall
```

Note that on windows your compiler might put the test executable in a subfolder called `Release`. If that's the case then you have to go to that folder before running the test.

This library is licensed under the Boost Software License, which can be found in [dlib/LICENSE.txt](https://github.com/davisking/dlib/blob/master/dlib/LICENSE.txt).  The long and short of the license is that you can use dlib however you like, even in closed source commercial software.

## dlib sponsors

This research is based in part upon work supported by the Office of the Director of National Intelligence (ODNI), Intelligence Advanced Research Projects Activity (IARPA) under contract number 2014-14071600010. The views and conclusions contained herein are those of the authors and should not be interpreted as necessarily representing the official policies or endorsements, either expressed or implied, of ODNI, IARPA, or the U.S. Government.

How to install dlib v19.9 or newer (w/ python bindings) from github on macOS and Ubuntu
Pre-reqs:

Have Python 3 installed. On macOS, this could be installed from homebrew or even via standard Python 3.6 downloaded installer from https://www.python.org/download. On Linux, just use your package manager.
On macOS:
Install XCode from the Mac App Store (or install the XCode command line utils).
Have homebrew installed
On Linux:
For a full list of apt packages required, check out the example Dockerfile and copy what's installed there.
These instructions assume you are using Ubuntu 16.04 or newer. If you are using 14.04, you can try these installation instructions instead to work around the old CMake version.
These instructions assume you don't have an nVidia GPU and don't have Cuda and cuDNN installed and don't want GPU acceleration (since none of the current Mac models support this).
Clone the code from github:

git clone https://github.com/davisking/dlib.git
Build the main dlib library (optional if you just want to use Python):

cd dlib
mkdir build; cd build; cmake ..; cmake --build .
Build and install the Python extensions:

cd ..
python3 setup.py install
At this point, you should be able to run python3 and type import dlib successfully.
