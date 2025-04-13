cmake_minimum_required(VERSION 3.16)
project(calc LANGUAGES CXX)

# 设置生成静态库
add_library(libcalc STATIC src/calc.cpp)
target_include_directories(libcalc PUBLIC ${PROJECT_SOURCE_DIR}/include)