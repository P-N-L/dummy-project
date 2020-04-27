If no CMAKE_BUILD_TYPE is specified (which is more likely to happen on CLI),
Debug is assumed.

Then, whatever the CMAKE_BUILD_TYPE is at configure time, the allowed
CMAKE_CONFIGURATION_TYPES are restricted to that single type for build time.

Since VSCode does not pass the GUI-selected CMAKE_BUILD_TYPE along at configure
time, this code always assumes Debug. This will be fine for Debug builds.
However, at build time, the GUI-selected CMAKE_BUILD_TYPE is passed along,
so for non-Debug builds, the CMAKE_BUILD_TYPE at build time will not match
the CMAKE_CONFIGURATION_TYPES at configure time (which was restricted to
CMAKE_BUILD_TYPE at configure time). This causes the build to fail.

The output log files in cmake_output were created with no VSCode settings
for CMake. All I did was select my generator via the GUI, select the appropriate
build type via the GUI, configure, and build.
