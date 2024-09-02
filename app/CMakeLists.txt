cmake_minimum_required(VERSION 3.16)

set(ProjectName "app")
project(${ProjectName})

link_directories(
    ${enet_BINARY_DIR}
    ${flecs_BINARY_DIR}
    ${raylib_BINARY_DIR}/raylib
)

file(GLOB_RECURSE APP_SRC
    "src/*.cpp"
    "src/*.h"
)

add_executable(${ProjectName} ${APP_SRC})

add_dependencies(${ProjectName} core)

target_include_directories( ${ProjectName}
    PUBLIC ${core_SOURCE_DIR}/src
    PUBLIC ${app_SOURCE_DIR}/src
)

target_link_libraries(${ProjectName}
    PUBLIC core
)
