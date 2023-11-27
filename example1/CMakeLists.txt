cmake_minimum_required( VERSION 3.3)

project( Hello )

set(DEPS_DIR deps)
set(SOURCE_CODE 
	src/hello.cpp
	${DEPS_DIR}/glad.c
   )

add_executable(hello 
	${SOURCE_CODE}
	)

target_include_directories(hello PRIVATE ${DEPS_DIR})
# include_directories(hello PRIVATE ${DEPS_DIR})

find_package(glfw3 3.3 REQUIRED)

target_link_libraries(hello glfw)

set(OpenGL_GL_PREFERENCE GLVND)
find_package(OpenGL REQUIRED)

target_link_libraries(hello OpenGL::GL)


