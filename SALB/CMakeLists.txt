cmake_minimum_required(VERSION 3.10)

# Set project name and specify it's a C++ project
project(salb CXX)

# Set C++ standard (equivalent to -std=c++0x from your Makefile)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Source files
set(SRCS
        bbr.cpp
        best_first_bbr.cpp
        bfs_bbr.cpp
        bin_packing.cpp
        hoffman.cpp
        io.cpp
        memory.cpp
)

# Compiler flags (equivalent to your Makefile's flags)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fmessage-length=100 -Wempty-body -Wall -Wno-sign-compare")

# Debug flags
set(CMAKE_CXX_FLAGS_DEBUG "-g -pg")

# Release/Optimization flags
set(CMAKE_CXX_FLAGS_RELEASE "-O2")

# Create the main executable
add_executable(salb ${SRCS})

# Create debug executable (optional - CLion can handle this through build types)
if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    set_target_properties(salb PROPERTIES OUTPUT_NAME "salb_d")
endif()

# If you need to link any libraries, add them here
# target_link_libraries(salb some_library)

# Create obj directory equivalent (CMake handles this automatically)
# But if you want to specify output directory:
set_target_properties(salb PROPERTIES
        RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}
)

# Print some information during build
message(STATUS "Configuring SALB project")
message(STATUS "Source files: ${SRCS}")
message(STATUS "Build type: ${CMAKE_BUILD_TYPE}")