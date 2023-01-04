cmake_minimum_required(VERSION 3.14)

ADD_LIBRARY(libtinycompress STATIC
	    src/lib/compress.c
	    src/lib/compress_hw.c)

SET(CRECORD_EXECUTABLE_NAME crecord)

# set the project name
project(${CRECORD_EXECUTABLE_NAME})

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(SOURCES 
    src/utils/crecord.c
    src/utils/wave.c)

include_directories(
    include
)

set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -pthread")

# add the executable
add_executable(${CRECORD_EXECUTABLE_NAME} ${SOURCES})
target_link_libraries(${CRECORD_EXECUTABLE_NAME} libtinycompress dl)
