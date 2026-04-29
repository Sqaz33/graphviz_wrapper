cmake_minimum_required(VERSION 3.5 FATAL_ERROR)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

project(graphviz_wrapper)

find_package(PkgConfig REQUIRED)

pkg_check_modules(GVC REQUIRED libgvc)
pkg_check_modules(LIBCGRAPH REQUIRED libcgraph)

add_library(${PROJECT_NAME} STATIC "src/graphviz.cpp")

target_include_directories(${PROJECT_NAME} PRIVATE ${GVC_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} PRIVATE ${GVC_LIBRARIES})
target_include_directories(${PROJECT_NAME} PRIVATE ${LIBCGRAPH_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} PRIVATE ${LIBCGRAPH_LIBRARIES})

target_include_directories(${PROJECT_NAME} INTERFACE "src")