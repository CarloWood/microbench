cmake_minimum_required( VERSION 3.12...3.16 )

project( microbench
         LANGUAGES CXX
         DESCRIPTION "A lightweight library for running micro-benchmarks on C++ code." )

# Add the local cmake directory to CMAKE_MODULE_PATH.
list( APPEND CMAKE_MODULE_PATH
      "${CMAKE_CURRENT_SOURCE_DIR}/../cwm4/cmake" )

include(AICxxProject)

#==============================================================================
# BUILD PROJECT
#

# This project is an OBJECT-library, used by other git submodules and the main project.
add_library( microbench_ObjLib OBJECT )

# Set SOURCE_DIR to the current directory.
set_property(
    TARGET     microbench_ObjLib
    PROPERTY   SOURCE_DIR       "${CMAKE_CURRENT_SOURCE_DIR}"
)

# The list of source files.
target_sources( microbench_ObjLib
    PRIVATE
        "systemtime.cpp"

        "microbench.h"
        "systemtime.h"
)

# Require support for C++11.
target_compile_features( microbench_ObjLib
    PUBLIC cxx_std_11
)

# Create an ALIAS target.
add_library( MoodyCamel::microbench ALIAS microbench_ObjLib )
