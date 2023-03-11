cmake_minimum_required (VERSION 3.10)

project ("ContinuousSubgraphMatching")

if ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "MSVC")
  message("MSVC")

  add_compile_options(/W3 /WX)
  add_compile_options(/wd4819)
  
elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
  message("GNU")
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -fopenmp -m64 -O3  -pthread -fexpensive-optimizations -flto=auto") # -Wall" )

elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang")
  message("Clang")
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -fopenmp -m64 -O3 -pthread")

elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Intel")
  message("Intel")

endif()

if (CMAKE_SYSTEM_NAME MATCHES "Linux")
	message(STATUS "Linux ")

elseif (CMAKE_SYSTEM_NAME MATCHES "Windows")
	message(STATUS "Windows")

    add_definitions(-D_CRT_SECURE_NO_WARNINGS)  

elseif (CMAKE_SYSTEM_NAME MATCHES "FreeBSD")
	message(STATUS "FreeBSD")

else ()
	message(STATUS "${CMAKE_SYSTEM_NAME}")
endif()

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include_directories(${PROJECT_SOURCE_DIR})
include_directories(${PROJECT_SOURCE_DIR}/graph)
include_directories(${PROJECT_SOURCE_DIR}/matching)
include_directories(${PROJECT_SOURCE_DIR}/utils)

add_subdirectory("graph")
add_subdirectory("utils")
add_subdirectory("matching")
