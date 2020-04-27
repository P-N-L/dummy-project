message("CMAKE_BUILD_TYPE not passed to configure as of CMake Tools v1.3.1: ${CMAKE_BUILD_TYPE}")

if (NOT CMAKE_BUILD_TYPE)
    # Use Debug as default build type if unspecified
    set(CMAKE_BUILD_TYPE Debug)
endif()
message("CMAKE_BUILD_TYPE after default is handled (if necessary): ${CMAKE_BUILD_TYPE}")

# Restrict valid configuration types to match current build type, to only allow
# builds for the single build type used at configure time.
# Understood that this does not modify the selectable list in VSCode GUI at
# this time.
set(CMAKE_CONFIGURATION_TYPES ${CMAKE_BUILD_TYPE} CACHE STRING
    "Semicolon separated list of supported configuration types." FORCE)

project(HelloWorld CXX)

add_executable(HelloWorld
    main.cpp
)
