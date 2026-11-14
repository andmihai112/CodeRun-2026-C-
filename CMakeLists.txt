cmake_minimum_required(VERSION 4.0)
project(SDL3_Project_SelfContained)

set(CMAKE_CXX_STANDARD 20)

include_directories(SDL3/include)
link_directories(SDL3/lib)

//add_subdirectory(glm)

add_executable(SDL3_Project_SelfContained main.cpp)

//target_link_libraries(SDL3_Project_SelfContained PRIVATE glm::glm)

target_link_libraries(SDL3_Project_SelfContained mingw32 SDL3)