# CMake Vcpkg Integration Script

This repository contains a CMake script that automates the process of downloading and installing libraries for C++ projects using vcpkg. The script ensures that vcpkg is present in your project and installs the required libraries specified in your CMakeLists.txt file.

## 👾 Features

- Automatically clones the vcpkg repository if not present.
- Installs specified libraries using vcpkg.
- Integrates seamlessly with CMake projects.

## ⚒️ Getting Started

### Prerequisites

- CMake 3.12 or higher
- Git

### Usage

1. **Include the vcpkg.cmake script in your project.**

   Copy the `vcpkg.cmake` script to your project's `cmake` directory or any preferred location.

2. **Modify your `CMakeLists.txt` to use the script.**

   Below is an example of how to integrate the script with your `CMakeLists.txt` file.

   ```cmake
   cmake_minimum_required(VERSION 3.12)
   project(YourProjectName)

   # Define the path to the vcpkg.cmake script
   set(CMAKE_TOOLCHAIN_FILE "${CMAKE_CURRENT_SOURCE_DIR}/cmake/vcpkg.cmake")

   # Include the vcpkg script
   include("${CMAKE_CURRENT_SOURCE_DIR}/cmake/vcpkg.cmake")

   # Specify the libraries to be installed via vcpkg
   
   vcpkg_install_not_found(fmt)
   vcpkg_install_not_found(boost)
   
   find_package(fmt REQUIRED)
   find_package(boost REQUIRED)

   add_executable(${PROJECT_NAME} src/main.cpp)

   target_link_libraries(${PROJECT_NAME} PRIVATE fmt::fmt boost::boost)
