cmake_minimum_required(VERSION 3.25)
project(kinetic C)

set(PROJECT_DIR ${PROJECT_SOURCE_DIR})
set(PROJECT_INCLUDE_DIR ${PROJECT_DIR}/include)
set(PROJECT_SOURCE_DIR ${PROJECT_DIR}/src)
set(PROJECT_SOURCES
        ${PROJECT_SOURCE_DIR}/containers/darray.c
        ${PROJECT_SOURCE_DIR}/graphics/shaderProgram.c
)

add_subdirectory(lib)

add_library(${PROJECT_NAME} ${PROJECT_SOURCES})

target_include_directories(${PROJECT_NAME} PRIVATE ${PROJECT_INCLUDE_DIR}/kinetic)
target_include_directories(${PROJECT_NAME} PUBLIC ${PROJECT_INCLUDE_DIR})

find_package(glfw3 3.2 REQUIRED)

target_link_libraries(${PROJECT_NAME} PRIVATE glfw glad cglm)
