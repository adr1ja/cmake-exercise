cmake_minimum_required(VERSION 3.10)

project(CMakeExercise)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_BUILD_TYPE Release)

# --- DEPENDENCIES ---
find_package(Boost REQUIRED COMPONENTS filesystem system)
find_package(deal.II REQUIRED)

# --- EXECUTABLE ---
add_executable(main 
    main.cpp 
    flatset/flatset.cpp 
    filesystem/filesystem.cpp
    fem/fem.cpp
    yamlParser/yamlParser.cpp
)

# --- LINKING ---
DEAL_II_SETUP_TARGET(main)
target_link_libraries(main Boost::filesystem Boost::system)

find_package(yaml-cpp REQUIRED)
target_link_libraries(main Boost::filesystem Boost::system yaml-cpp)