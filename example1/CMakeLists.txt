cmake_minimum_required( VERSION 3.3)
set(cmake_cxx_standard 17)
set(cmake_c_standard 99)
set(this hello)
list(APPEND CMAKE_PREFIX_PATH "/usr/lib")

# project( Hello )
project(${this} CXX C)

set(DEPS_DIR deps)
set(SOURCE_CODE 
	src/hello.cpp
	${DEPS_DIR}/glad.c
   )

add_executable(${this} 
	${SOURCE_CODE}
	)

include_directories(
  include
  /usr/include
)

target_include_directories(${this} PRIVATE ${DEPS_DIR})
# include_directories(${this} PRIVATE ${DEPS_DIR})

# set(glm_DIR /usr/lib/cmake/glm) # if necessary
find_package(glm REQUIRED)
target_link_libraries(${this} glm::glm)

find_package(GLEW 2.2 REQUIRED)

# if (GLEW_FOUND)
#     include_directories($(GLEW_INCLUDE_DIRS))
# endif()

target_link_libraries(${this} GLEW::GLEW)

find_package(glfw3 3.3 REQUIRED)

target_link_libraries(${this} glfw)

set(OpenGL_GL_PREFERENCE GLVND)

find_package(OpenGL REQUIRED)

target_link_libraries(${this} OpenGL::GL)


find_library(SOIL soil-debug)
# find_library(SOIL2 REQUIRED)

# find_library(SOIL2 SOIL2 /usr/lib/libSOIL.so)

target_link_libraries(${this} SOIL)

