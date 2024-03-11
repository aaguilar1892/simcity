cmake_minimum_required(VERSION 3.28)
project(simcity)

set(CMAKE_CXX_STANDARD 17)

add_executable(simcity main.cpp zone.cpp zone.h initialization.cpp initialization.h output.cpp output.h
)
