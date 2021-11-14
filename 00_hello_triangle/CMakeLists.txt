cmake_minimum_required(VERSION 3.6)   # CMake version check
project(antons_tutorials C CXX)               # Create project "simple_example"
set(CMAKE_CXX_STANDARD 11)            # Enable c++11 standard
# modified cmake file M. Stadlhofer 14.11.21

cmake_path(GET PROJECT_SOURCE_DIR PARENT_PATH PARENT_DIRECTORY)

#add source folder so the program can be compiled at build folder
include_directories(${CMAKE_SOURCE_DIR})

#Headers
file(GLOB HEADERS
  *.h
  )

#GLEW
list(APPEND CMAKE_PREFIX_PATH "C:\\Users\\mista\\Documents\\GitHub\\glew")
find_package(GLEW REQUIRED)

include_directories(${GLEW_INCLUDE_DIR})


#Main
add_executable(hellot main.c ${HEADERS})

#OpenGL
find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIR})
target_link_libraries(hellot ${OPENGL_gl_LIBRARY})


#GLFW
add_subdirectory("C:\\Users\\mista\\Documents\\GitHub\\glfw-3.3.5" "${PARENT_DIRECTORY}/GLFW/bin" EXCLUDE_FROM_ALL)
target_link_libraries(hellot glfw)



target_link_libraries(hellot ${GLEW_LIBRARIES})
include_directories("${PARENT_DIRECTORY}/include/")


