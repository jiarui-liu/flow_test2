cmake_minimum_required(VERSION 3.10)
project(CVAS)

set(CMAKE_CXX_STANDARD 17)

FILE(GLOB SRC_LIST_CPP ${PROJECT_SOURCE_DIR}/src/*.cpp)

INCLUDE_DIRECTORIES(${PROJECT_SOURCE_DIR}/include)

find_package(OpenCV REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})

SET(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

ADD_LIBRARY(cvas SHARED src/car_status.cpp src/data.cpp)

add_executable(run run.cpp)

TARGET_LINK_LIBRARIES(run cvas ${OpenCV_LIBS})
