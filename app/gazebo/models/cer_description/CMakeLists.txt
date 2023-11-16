################################################################################
#                                                                              #
# Copyright (C) 2019 Fondazione Istitito Italiano di Tecnologia (IIT)          #
# All Rights Reserved.                                                         #
#                                                                              #
################################################################################

# @author Mohamed Elobaid <mohamed.elobaid@iit.it>

# List the subdirectory (http://stackoverflow.com/questions/7787823/cmake-how-to-get-the-name-of-all-subdirectories-of-a-directory)
macro(SUBDIRLIST result curdir)
  file(GLOB children RELATIVE ${curdir} ${curdir}/*)
  set(dirlist "")
  foreach(child ${children})
    if(IS_DIRECTORY ${curdir}/${child})
      list(APPEND dirlist ${child})
    endif()
  endforeach()
  set(${result} ${dirlist})
endmacro()

# Get list of models
subdirlist(subdirs ${CMAKE_CURRENT_SOURCE_DIR})

# Install  model
foreach (dir ${subdirs})
  yarp_install(DIRECTORY ${dir} DESTINATION ${CMAKE_INSTALL_DATADIR}/gazebo/models)
endforeach ()

# Install the urdf from assets
get_property(CER_URDF GLOBAL PROPERTY CER_URDF)

configure_file(${CER_URDF} ${CMAKE_CURRENT_BINARY_DIR}/cer.urdf)
yarp_install(FILES ${CMAKE_CURRENT_BINARY_DIR}/cer.urdf
             DESTINATION ${CMAKE_INSTALL_DATADIR}/gazebo/models/cer_urdf)


# Install the meshes from assets
get_property(CER_MESHES GLOBAL PROPERTY CER_MESHES)
yarp_install(DIRECTORY ${CER_MESHES} DESTINATION ${CMAKE_INSTALL_DATADIR}/gazebo/models/cer_urdf)
