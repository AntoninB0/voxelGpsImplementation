cmake_minimum_required(VERSION 3.10)

# Project name and version
project(untitled2)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Find the Vulkan package
find_package(Vulkan REQUIRED)

# Find the GLFW package
find_package(glfw3 REQUIRED)

# Find GLM package
find_package(glm REQUIRED)

# Add the executable
add_executable(untitled2 main.cpp)

# Link the libraries (GLFW, Vulkan, and GLM)
target_include_directories(untitled2 PRIVATE ${/usr/include/glm})
target_link_libraries(untitled2 PRIVATE Vulkan::Vulkan glfw )
