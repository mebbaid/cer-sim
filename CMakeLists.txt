################################################################################
#                                                                              #
# Copyright (C) 2019 Fondazione Istitito Italiano di Tecnologia (IIT)          #
# All Rights Reserved.                                                         #
#                                                                              #
################################################################################

# @author:Mohamed Elobaid <mohamed.elobaid@iit.it>

cmake_minimum_required(VERSION 3.5)
project(cer-sim)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

#find_package(catkin REQUIRED)
find_package(YARP REQUIRED)

# Enable C++11
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED 11)

# Assets contributed by Honda
add_subdirectory(assets)

# Model and configuration files
add_subdirectory(app)


