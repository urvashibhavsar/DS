cmake_minimum_required(VERSION 2.8)

project(opencv)
macro(use_cxx11)
  if (CMAKE_VERSION VERSION_LESS "3.1")
    if (CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
      set (CMAKE_CXX_FLAGS "-std=gnu++11 ${CMAKE_CXX_FLAGS}")
    endif ()
  else ()
    set (CMAKE_CXX_STANDARD 11)
  endif ()
endmacro(use_cxx11)

use_cxx11()

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

find_package(OpenCV REQUIRED)

include_directories(${PROJECT_SOURCE_DIR}/include ${OpenCV_INCLUDE_DIRS})

add_executable(run src/cpp.cc)

target_link_libraries(run ${OpenCV_LIBS})
