cmake_minimum_required(VERSION 3.10)

project(openGL_learning)
#add_definitions(-std=c99 -O3)
set(CMAKE_CXX_STANDARD 11)

set(GLEW_H /usr/local/Cellar/glew/2.1.0/include/GL)
set(GLFW_H /usr/local/Cellar/glfw/3.3/include/GLFW)
set(ASSIMP_H /usr/local/Cellar/assimp/4.1.0/include)
set(GLAD_H /usr/local/include/glad)
set(KH_H /usr/local/include/KHR)
include_directories(${GLEW_H} ${GLFW_H} ${GLAD_H} ${KH_H} ${ASSIMP_H})
include_directories(include)

set(GLEW_LINK /usr/local/Cellar/glew/2.1.0/lib/libGLEW.2.1.dylib)
set(GLFW_LINK /usr/local/Cellar/glfw/3.3/lib/libglfw.3.3.dylib)
set(ASSIMP_LINK /usr/local/Cellar/assimp/4.1.0/lib/libassimp.4.1.0.dylib)
link_libraries(${OPENGL} ${GLEW_LINK} ${GLFW_LINK} ${ASSIMP_LINK})

add_executable(openGL_learning src/chapter4/blending_discard.cpp libsrc/glad.c include/opengl/shader.h include/opengl/camera.h src/chapter4/face_elimination.cpp src/chapter4/frame_buffer.cpp)

#判断是否是苹果电脑
if(APPLE)
    target_link_libraries(openGL_learning "-framework OpenGL")
    target_link_libraries(openGL_learning "-framework GLUT")
endif()