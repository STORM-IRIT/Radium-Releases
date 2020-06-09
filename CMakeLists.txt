cmake_minimum_required(VERSION 3.6)

project (radiumreleases)

#------------------------------------------------------------------------------
# Policies and global parameters for CMake

set(CMAKE_DISABLE_SOURCE_CHANGES ON)
set(CMAKE_DISABLE_IN_SOURCE_BUILD ON)

include(ExternalProject)

#-------------------------------------------------------------------------------
# Set default install location to RADIUM_BUNDLE_DIRECTORY
# we do not want to install to /usr by default
if (CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
    set (CMAKE_INSTALL_PREFIX "${RADIUM_BUNDLE_DIRECTORY}" CACHE PATH
        "Install path prefix, prepended onto install directories." FORCE )
    message( "Set install prefix to ${CMAKE_INSTALL_PREFIX}" )
endif()

ExternalProject_Add( radiumproject
    GIT_REPOSITORY https://github.com/STORM-IRIT/Radium-Engine.git
    GIT_TAG origin/master
    GIT_SHALLOW TRUE
    GIT_PROGRESS TRUE
    INSTALL_DIR "${CMAKE_INSTALL_PREFIX}"
    BUILD_COMMAND ${CMAKE_COMMAND} -E echo "Compiling in Installing Radium"
    COMMAND       ${CMAKE_COMMAND} --build <BINARY_DIR> --target install
    CMAKE_ARGS
    -DCMAKE_INSTALL_PREFIX=<INSTALL_DIR>
    -DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}
    -DCMAKE_PREFIX_PATH=${CMAKE_PREFIX_PATH}
    -DRADIUM_ENABLE_TESTING=FALSE
    -DRADIUM_IO_ASSIMP=${RADIUM_IO_ASSIMP}
    )


ExternalProject_Add( radiumapps
    GIT_REPOSITORY https://github.com/STORM-IRIT/Radium-Apps.git
    GIT_TAG origin/master
    GIT_SHALLOW TRUE
    GIT_PROGRESS TRUE
    INSTALL_DIR "${CMAKE_INSTALL_PREFIX}"
    DEPENDS radiumproject
    BUILD_COMMAND ${CMAKE_COMMAND} -E echo "Compiling in Installing Radium-Apps"
    COMMAND       ${CMAKE_COMMAND} --build <BINARY_DIR> --target install
    CMAKE_ARGS
    -DCMAKE_INSTALL_PREFIX=<INSTALL_DIR>
    -DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}
    -DCMAKE_PREFIX_PATH=${CMAKE_PREFIX_PATH}
    -DRadium_DIR=<INSTALL_DIR>
    )
