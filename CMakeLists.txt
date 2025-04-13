cmake_minimum_required(VERSION 3.16)
project(calculator LANGUAGES CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS 1)
# 添加子项目
add_subdirectory(lib/calc)

# 主程序
add_executable(${PROJECT_NAME} src/main.cpp)

# 链接子项目静态库
target_link_libraries(${PROJECT_NAME} PRIVATE libcalc)