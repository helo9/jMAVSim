# Copyright (c) 2022 Jonathan Hahn
# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.20)

project(jMAVSim)

add_custom_target(jMAVSim
    COMMAND
    ant
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    USES_TERMINAL
)

add_custom_target(jMAVSim_run
    COMMAND
    java --add-exports=java.desktop/sun.awt=ALL-UNNAMED -cp lib/\*:out/production/jmavsim.jar me.drton.jmavsim.Simulator -m
    DEPENDS 
    jMAVSim
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    USES_TERMINAL
)
