cmake_minimum_required(VERSION 3.10)

# Project name
project(3d-example)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Add executable target
file(GLOB_RECURSE SOURCES "src/*.cpp" "vendor/glad/glad.c")
file(GLOB_RECURSE HEADERS "include/*.h" "vendor/glad/glad.h" "vendor/linmath/linmath.h")

add_executable(${PROJECT_NAME} ${SOURCES} ${HEADERS})

# Include directories for headers
target_include_directories(${PROJECT_NAME} PRIVATE
	${CMAKE_CURRENT_SOURCE_DIR}/include
)

target_include_directories(${PROJECT_NAME} PRIVATE
	${CMAKE_CURRENT_SOURCE_DIR}/vendor/glad
)

target_include_directories(${PROJECT_NAME} PRIVATE
	${CMAKE_CURRENT_SOURCE_DIR}/vendor/linmath
)

# Link GLFW and other necessary libraries
target_link_directories(${PROJECT_NAME} PRIVATE /usr/lib/x86_64-linux-gnu)
target_link_libraries(${PROJECT_NAME} PRIVATE glfw)
