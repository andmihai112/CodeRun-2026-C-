cmake_minimum_required(VERSION 3.20)
project(CodeRun-2026-C-)

set(CMAKE_CXX_STANDARD 20)

add_subdirectory(glm)

add_executable(CodeRun-2026-C-
        main.cpp
        circle.cpp
        circle.h
        rectangle.cpp
        rectangle.h
)

target_include_directories(CodeRun-2026-C- PRIVATE SDL3/include)

target_link_directories(CodeRun-2026-C- PRIVATE SDL3/lib)

target_link_libraries(CodeRun-2026-C- PRIVATE
        SDL3
        glm::glm
)

add_custom_command(TARGET CodeRun-2026-C- POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_if_different
        "${CMAKE_CURRENT_SOURCE_DIR}/SDL3.dll"
        "$<TARGET_FILE_DIR:CodeRun-2026-C->/SDL3.dll"
)
