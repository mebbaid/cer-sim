################################################################################
#                                                                              #
# Copyright (C) 2019 Fondazione Istitito Italiano di Tecnologia (IIT)          #
# All Rights Reserved.                                                         #
#                                                                              #
################################################################################



set(yarprobotname cer-sim)
set(CER_INSTALL_DIR_NAME ami_cer-sim)

# Install the dic urdf from assets
get_property(CER_URDF GLOBAL PROPERTY CER_URDF)

configure_file(${CER_URDF} ${CMAKE_CURRENT_BINARY_DIR}/cer.urdf)
yarp_install(FILES ${CMAKE_CURRENT_BINARY_DIR}/cer.urdf
             DESTINATION ${CMAKE_INSTALL_DATADIR}/${CER_INSTALL_DIR_NAME}/robots/${yarprobotname})


# Install .ini files
file(GLOB ini ${CMAKE_CURRENT_SOURCE_DIR}/*.ini)
yarp_install(FILES ${ini} DESTINATION ${CMAKE_INSTALL_DATADIR}/${CER_INSTALL_DIR_NAME}/robots/${yarprobotname})

# Install .xml files
file(GLOB xml ${CMAKE_CURRENT_SOURCE_DIR}/*.xml)
yarp_install(FILES ${xml} DESTINATION ${CMAKE_INSTALL_DATADIR}/${CER_INSTALL_DIR_NAME}/robots/${yarprobotname})

