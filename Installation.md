Lomse library installation
======================================

This document contains detailed instructions for building Lomse library and tests
program from sources. If you find things that need to be fixed and would like to contribute, you are welcome. Thank you.

* [Quick instructions](#quick)
* [Detailed instructions](#detailed)
* [Building a binary package](#package)


<a name="quick">Quick instructions</a>
----------------------------------------

Download lomse sources from master repository at GitHub, either the latest code:
```bash
cd <projects>
git clone -b master --single-branch --depth 1 https://github.com/lenmus/lomse.git
cd lomse
```

or a specific Release (i.e. 0.16.1)
```bash
cd <projects>
git clone -b '0.16.1' --single-branch --depth 1 https://github.com/lenmus/lomse.git
cd lomse
```

Generate the makefiles, build, run unit tests and install:

```bash
mkdir build
cd build
cmake -G "Unix Makefiles" ../           #generate the makefile
make                                    #build
./bin/testlib                           #run unit tests
sudo make install                       #install Lomse
```
Done!

<a name="detailed">Detailed instructions</a>
----------------------------------------------


### Requirements ###

To build the lomse library, the following software has to be installed in your system:

- CMake version 2.8 or higher ([cmake.org](http://www.cmake.org))
- UnitTest++ 1.3.0 or higher ([unittest-cpp proyect](http://unittest-cpp.sourceforge.net/))
- FreeType 2.3.5-1 or higher ([freetype.org](http://www.freetype.org/))
- Boost 1.42 or higher ([boost.org](http://www.boost.org/))
- zlib ([zlib.net](http://zlib.net/))
- libpng ([libpng.org](http://www.libpng.org/))

Please refer to each package website for installation instructions. In many Linux distros, these packages are already installed in your system, but if anyone is missing, normally you can install it using the package manager. For instance, in Ubuntu
```bash
sudo apt-get install cmake cmake-data
sudo apt-get install git
sudo apt-get install libunittest++-dev
sudo apt-get install libfreetype6-dev
sudo apt-get install libpng++-dev
sudo apt-get install zlib1g-dev
sudo apt-get install libboost-date-time-dev libboost-thread-dev libboost-system-dev
```

For other  operating systems you will have to check if your system has these packages installed, and install any missing one. Please refer to each package website for instructions.


### Step 1: Download the Lomse source code ###

The simplest approach is to clone the Lomse repository at GitHub, either the latest code:
```bash
cd <projects>
git clone -b master --single-branch --depth 1 https://github.com/lenmus/lomse.git
cd lomse
```

or a specific Release (i.e. 0.16.1)
```bash
cd <projects>
git clone -b '0.16.1' --single-branch --depth 1 https://github.com/lenmus/lomse.git
cd lomse
```

As an alternative, you can download a Sorce Code package from [Lomse Releases page](https://github.com/lenmus/lomse/releases), by visiting that page and clicking on the package. Alrenatively, you can do it from a command console. For instance, to download source code for release 0.16.1:
```bash
cd <projects>
wget https://github.com/lenmus/lomse/archive/0.16.1.tar.gz
tar xzf lomse-0.16.1.tar.gz
cd lomse-0.16.1
```


### Step 2: Create a folder for building ###

When you generates the makefiles and build Lomse a lot of files are created and they have to go somewhere. The best apoproach is to put them in a completely separate directory, so that
your source tree is unchanged. Out-of-source builds are recommended. 

Create a directory to hold your build files (e.g. "build-lomse"), and move to it:

```bash
mkdir build-lomse
cd build-lomse
```

### Step 3: Generate the makefiles ###

Lomse distribution does not include makefiles. All makefiles are generated
with CMake build system. CMake can generate different kinds of
native build files for your system (e.g. Unix Makefiles, Eclipse CDT 4.0
project files, Visual Studio project files, etc.).

Therefore, the first step is to generate a make file. For this you just have to run CMake. In the following command please replace '<lomse>' with the name of the folder containing the Lomse source code, normally 'lomse' if you has clones the master repo or 'lomse-x.y.z' if you have downloaded the release x.y.z:
```bash
cmake -G "Unix Makefiles" -DCMAKE_BUILD_TYPE=Debug ../<lomse>

```
By default, Lomse library will be installed
in [prefix]/lib and header files in [prefix]/include/lomse, with [prefix]
defaulting to usr/local.


### Step 4: Build Lomse and run unit tests ###
For building just run the standard 'make' program:
```bash
make
```
The build should finish without errors. 

**Important**: In case of problems, before repeating all the build procedure (after fixing the errors), the makefile should be re-created. The safest way to proceed is to delete the whole content of the build folder and start again from step 3. So move to folder to build and clean all:

```bash
    rm * -rf     #AWARE: BE SURE YOU ARE IN THE build-lomse FOLDER !!!!
```
and repeat build process from step 3, after fixing the errors.


### Step 5: Run unit tests ###

The build process also generates the unit test program. For running it just do:
```bash
./bin/testlib
```
You will get an output similar to this one:
```bash
    Lomse version 0.17.53-a19de1d. Library tests runner.

    Lomse build date: 2016-01-27 12:06:01 UTC
    Path for tests scores: '<local-path>/test-scores/'

    Running all tests

    Success: 1405 tests passed.
    Test time: 9.23 seconds.

```
The number of tests will grow over time, and the times reported will depend on your computer.


If you'd like, you also can build a small example program, using the library, and run it:
```bash
make example_1
./bin/example_1
```

### Step 6: Install Lomse ###
Finally, if no errors in the unit tests, install lomse:
```bash
sudo make install

```
That installs Lomse on your system. Lomse library is installed
in [prefix]/lib and header files in [prefix]/include/lomse, with [prefix]
defaulting to usr/local if you didn't specify a different prefix in step 3.


### Step 7: Remove build folder and sources ###

If you'd like, now you can remove build folder and sources- Remember to replace '<lomse>' with the name of the folder containing the Lomse source code, normally 'lomse' if you have cloned the master repo or 'lomse-x.y.z' if you have downloaded the release x.y.z
```bash
cd ..
rm build-lomse -rf      #remove build folder
rm <lomse> -rf          #remove sources

```

<a name="package">Building a binary package</a>
--------------------------------------------------

If you'd like to build a binary package for Debian systems, just do this after building and testing (step 5):
```bash
make package
```

After executing this command you wil find the package (i.e. lomse_0.16.1_amd64.deb) in the build folder.


