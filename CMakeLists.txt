cmake_minimum_required( VERSION 3.6 )
project( LADana )
set(CMAKE_CXX_FLAGS "-std=c++17")

set(ENV_LAD $ENV{LAD_LIB_PATH})
SET(CMAKE_PREFIX_PATH ${ENV_LAD})

#message(STATUS ${CMAKE_PREFIX_PATH})

find_package(ROOT REQUIRED)
#set(CMAKE_FIND_DEBUG_MODE TRUE)
find_library(LAD_LIB
	NAMES LAD
	HINTS "${CMAKE_PREFIX_PATH}"
	PATH_SUFFIXES 64)
if(NOT LAD_LIB)
	message(FATAL_ERROR "LAD library not found")
endif()

#SET(CMAKE_SKIP_BUILD_RPATH  FALSE)
#SET(CMAKE_BUILD_WITH_INSTALL_RPATH FALSE)
#SET(CMAKE_INSTALL_RPATH "${CMAKE_SOURCE_DIR}/lib")
#SET(CMAKE_INSTALL_RPATH_USE_LINK_PATH TRUE)
LIST(FIND CMAKE_PLATFORM_IMPLICIT_LINK_DIRECTORIES "${CMAKE_SOURCE_DIR}/lib" isSystemDir)
IF("${isSystemDir}" STREQUAL "-1")
	SET(CMAKE_INSTALL_RPATH "${CMAKE_SOURCE_DIR}/lib")
ENDIF("${isSystemDir}" STREQUAL "-1")
#set path for include directories and libraries
set (INCLUDES ${ROOT_INCLUDE_DIR} ${CMAKE_SOURCE_DIR}/include)
 
list (APPEND CMAKE_PREFIX_PATH $ENV{ROOTSYS}) 
include(${ROOT_USE_FILE})
#ADD_DEFINITIONS( -D_DATA="${CMAKE_SOURCE_DIR}/data" )
#ADD_DEFINITIONS( -D_DATA="${ENV_DATA}" )
 
 
#add_subdirectory(classes)
                                 
add_subdirectory(skimmers)
