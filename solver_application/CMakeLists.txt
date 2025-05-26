cmake_minimum_required(VERSION 3.11)
project(solver_app LANGUAGES CXX)

add_executable(solver equation.cpp)
if(MSVC)
    target_link_libraries(solver PRIVATE solver_lib formatter_ex formatter)
else()
    target_link_libraries(solver PRIVATE solver_lib formatter_ex formatter m)
endif()
