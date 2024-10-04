cmake_minimum_required(VERSION 3.10)

# Project name and version
project(voxelGpsImplementation)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Add executable
add_executable(voxelGpsImplementation main.cpp)

# Find Vulkan package
find_package(Vulkan REQUIRED)

# Platform-specific logic
if(UNIX)
    # Pour Linux
    find_package(glfw3 REQUIRED)
    find_package(glm REQUIRED)
    target_include_directories(voxelGpsImplementation PRIVATE /usr/include/glm)

elseif(WIN32)
    # Pour Windows
    set(GLFW_DIR "C:/libs/glfw")
    set(GLM_DIR "C:/libs/glm")

    # Ajout des chemins d'inclusion
    target_include_directories(voxelGpsImplementation PRIVATE "${GLFW_DIR}/include")
    target_include_directories(voxelGpsImplementation PRIVATE "${GLM_DIR}/glm")

    # Lien avec GLFW (librairie statique ou dynamique)
    target_link_libraries(voxelGpsImplementation PRIVATE "${GLFW_DIR}/lib-mingw-w64/libglfw3.a")

    # Assure-toi que glfw3.dll est dans le même répertoire que l'exécutable ou dans le PATH.
endif()

# Lien avec Vulkan
target_link_libraries(voxelGpsImplementation PRIVATE Vulkan::Vulkan)
