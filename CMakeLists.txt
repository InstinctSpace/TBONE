cmake_minimum_required(VERSION 3.10)
project(CBONE)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Build type
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()

# Compiler flags
if(CMAKE_CXX_COMPILER_ID MATCHES "GNU|Clang")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra")
    set(CMAKE_CXX_FLAGS_RELEASE "-O3")
endif()

# Add source files - let's make this more explicit for debugging
set(SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/CBONE.cpp   # Point to CBONE.cpp instead of src/main.cpp
)

# Create executable
add_executable(${PROJECT_NAME} ${SOURCES})

# Include directories
target_include_directories(${PROJECT_NAME} PRIVATE 
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

# If you have external dependencies, add them here
# find_package(SomePackage REQUIRED)
# target_link_libraries(${PROJECT_NAME} PRIVATE SomePackage) 