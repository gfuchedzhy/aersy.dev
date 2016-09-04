cmake_minimum_required(VERSION 3.3)
project(aersy.dev NONE)

set(GLAD_PROFILE "core" CACHE STRING "OpenGL profile" FORCE)
set(GLAD_API "gl=3.3" CACHE STRING "API type/version pairs, like \"gl=3.2,gles=\", no version means latest" FORCE)
set(GLAD_GENERATOR "c" CACHE STRING "Language to generate the binding for" FORCE)
set(GLAD_NO_LOADER ON CACHE BOOL "No loader" FORCE)
add_subdirectory(glad)
include_directories(${GLAD_INCLUDE_DIRS})

set(GLCXX_GL_INLCUDE_DEF "\
#include <glad/glad.h>
#define glcxx_load_gl gladLoadGLLoader")
add_subdirectory(glcxx)
set(GLCXX_LIBRARIES ${GLCXX_LIBRARIES} ${GLAD_LIBRARIES})
add_subdirectory(aersy)
