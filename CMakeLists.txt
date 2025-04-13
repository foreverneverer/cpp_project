cmake_minimum_required(VERSION 3.16)
project(ArrowHouse)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_BUILD_TYPE Release)
set(ARROW_SIMD_LEVEL NONE)
set(CMAKE_EXPORT_COMPILE_COMMANDS 1)

# 设置Arrow静态编译选项
set(ARROW_BUILD_STATIC ON)
set(ARROW_BUILD_SHARED OFF)
set(ARROW_DEPENDENCY_SOURCE "AUTO")
set(ARROW_VERBOSE_THIRDPARTY_BUILD ON)

# 重要：禁用不需要的组件（按需调整）
set(ARROW_COMPUTE OFF)
set(ARROW_CSV OFF)
set(ARROW_DATASET OFF)
set(ARROW_FILESYSTEM ON)  # 保持基础文件系统支持
set(ARROW_JSON OFF)

# 包含Arrow子模块
add_subdirectory(lib/arrow/cpp)

# 主程序
add_executable(ArrowHouse src/main.cpp)

# 链接静态库
target_link_libraries(ArrowHouse PRIVATE
    arrow_static  # Arrow核心静态库
    arrow_bundled_dependencies  # 第三方依赖
)