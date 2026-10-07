cmake_minimum_required(VERSION 3.16)

project(cpp_interview LANGUAGES CXX)

# Sub-projects are built in place, so no source file is moved or renamed.
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(MSVC)
    # Sources are UTF-8 without BOM and carry Chinese comments. Without /utf-8
    # MSVC reads them in the local ANSI codepage and reports C4819.
    add_compile_options(/utf-8)
endif()

# DesignPattern is a self-contained CMake project; it is added as-is, so its own
# CMakeLists.txt keeps working when the folder is opened standalone.
add_subdirectory(DesignPattern)

add_subdirectory(Algorithm)
add_subdirectory(DataStructure)
add_subdirectory(Problems)

# STL/ holds only notes (README.md, STL.md) - there is nothing to compile there.
