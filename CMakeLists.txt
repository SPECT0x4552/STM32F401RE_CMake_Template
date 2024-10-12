# My template for compiling STM32F401RE projects using CMake
# Modified, but most credit goes to docs.jasony.org (jasonyang) 

# Define CMake version

cmake_minimum_required(VERSION 3.22)


# Setup cmake module path and compiler settings
list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")

# Message of the current build printed to the console
message("Build type: "      $(CMAKE_BUILD_TYPE))


# Setup C and C++ version

# C:
set(CMAKE_C_STANDARD            	11)
set(CMAKE_C_STANDARD_REQUIRED   	ON)
set(CMAKE_C_EXTENSIONS          	ON)
# C++: 
set(CMAKE_CXX_STANDARD          	17)
set(CMAKE_CXX_STANDARD_REQUIRED		ON)
set(CMAKE_CXX_EXTENSIONS		ON)

set(CMAKE_EXPORT_COMPILE_COMMANDS	ON)

# Define path for shorter reference 
set(PROJ_PATH 				${CMAKE_CURRENT_SOURCE_DIR}) 

# Define .cmake module for toolchain compile flags that hold true on all ARM projects
# Path is defined by the list() function (below) 
set(CMAKE_TOOLCHAIN_FILE		gcc-arm-none-eabi)



# Project Name - EDIT ACCORDING TO YOUR PROJECT 
project(401RE-Template) 

enable_language(C CXX ASM)

# Linker file - EDIT ACCORDING TO YOUR PROJECT 
set(linker_script_SRC			${CMAKE_PROJECT_NAME}/Core/STM32F401RETX_FLASH.ld)

# Use project name when compiling into binary files (binary names) 
set(EXECUTABLE				${CMAKE_PROJECT_NAME}) 


# MCU Specific settings - EDIT ACCORDING TO YOUR PROJECT
# Path defined in list() function above
include(STM32F4xx_HAL_PARA)


# .cmake module generated using .\getIncludeList.sh and .\getSourceList.sh 
# These paths contain ALL the project source file list and include list 
# Defined in the list() function above 
include(SourceList) 
include(IncludeList)

# Executable files (binaries) 











