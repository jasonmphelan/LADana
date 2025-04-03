Repository for high level analysis of LAD data.  To set up, install hcana and LADlibs following https://hallcweb.jlab.org/wiki/index.php/LAD_Software.
Set then environment variable ```LAD_LIB_PATH``` to ```{LADlib_install}/lib64''' (CMake can't seem to find the install directory if I use the environment variable ```LD_LIB_PATH``` for some reason...)

To compile:

```mkdir build
cd build
cmake ..
make'''
