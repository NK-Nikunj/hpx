# Copyright (c) 2018      Nikunj Gupta
#
# Distributed under the Boost Software License, Version 1.0. (See accompanying
# file LICENSE_1_0.txt or copy at http://www.boost.org/LICENSE_1_0.txt)

# Required atleast cmake version 3.0.2
cmake_minimum_required(VERSION 3.0.2 FATAL_ERROR)

#This cmake is not meant to be built in environment other than Linux
if(NOT UNIX)
	message(FATAL_ERROR "This cmake can only be built in linux systems.")
	return()
endif()

project(hello_world_component CXX)

add_custom_command ( OUTPUT hello_world_client 
					COMMAND chmod +x ../build/examples/hello_world_component/hello.sh
					COMMAND ../build/examples/hello_world_component/hello.sh
					COMMAND chmod -x ../build/examples/hello_world_component/hello.sh
					WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/)

add_custom_target(
				BuildDocs ALL
				DEPENDS hello_world_client)
