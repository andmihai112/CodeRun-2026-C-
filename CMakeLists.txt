cmake_minimum_required(VERSION 3.20)

project(CodeRun_2026_C LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)


add_executable(${PROJECT_NAME}
    main.cpp
    circle.cpp
    rectangle.cpp
)

target_include_directories(${PROJECT_NAME}
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}
)


list(PREPEND CMAKE_PREFIX_PATH "${CMAKE_CURRENT_SOURCE_DIR}/SDL3")
find_package(SDL3 CONFIG REQUIRED)

target_link_libraries(${PROJECT_NAME}
    PRIVATE
        SDL3::SDL3
)


if (EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/SDL3.dll")
    add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_if_different
            "${CMAKE_CURRENT_SOURCE_DIR}/SDL3.dll"
            "$<TARGET_FILE_DIR:${PROJECT_NAME}>"
    )
endif()
