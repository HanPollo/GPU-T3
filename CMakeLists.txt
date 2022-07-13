set(CMAKE_LEGACY_CYGWIN_WIN32 OFF)
cmake_minimum_required(VERSION 3.15)
project(t3GPU C CXX)
find_package(OpenGL REQUIRED)
add_definitions(-D_USE_MATH_DEFINES)
set(THIRD_PARTY_INCLUDE_DIRECTORIES "${CMAKE_CURRENT_SOURCE_DIR}/third_party/glad/include"
									"${CMAKE_CURRENT_SOURCE_DIR}/third_party/glfw/include"
									"${CMAKE_CURRENT_SOURCE_DIR}/third_party/stb"
									"${CMAKE_CURRENT_SOURCE_DIR}/third_party/assimp/include"
									"${CMAKE_CURRENT_SOURCE_DIR}/third_party/OpenMesh-8.1/src"
									"${CMAKE_CURRENT_SOURCE_DIR}/third_party/glm")
set(T3GPU_INCLUDE_DIRECTORY "${CMAKE_SOURCE_DIR}/source/")

if(MSVC)
	set(THIRD_PARTY_LIBRARIES glad glfw ${OPENGL_LIBRARIES} ${BULLET_LIBRARIES} assimp stb)
else()
	set(THIRD_PARTY_LIBRARIES glad glfw ${OPENGL_LIBRARIES} ${BULLET_LIBRARIES} stdc++fs assimp stb)
endif(MSVC)

configure_file(CMakeConfigFiles/root_directory.h.in "${CMAKE_SOURCE_DIR}/source/root_directory.h")
add_subdirectory(third_party)
add_subdirectory(source)
