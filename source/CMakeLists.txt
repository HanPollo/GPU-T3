set(T3GPU_HEADERS
        BasicMesh.h
        camera.h
        EBO.h
        Model.h
        shaderClass.h
        VAO.h
        VBO.h
        )
set(T3GPU_SOURCES
        BasicMesh.cpp
        Camera.cpp
        EBO.cpp
        Model.cpp
        shaderClass.cpp
        VAO.cpp
        VBO.cpp
        )
add_library(T3GPU STATIC ${T3GPU_SOURCES} ${T3GPU_HEADERS} system.h ${Shaders})
if (MSVC)
    target_compile_options(T3GPU PUBLIC /wd5033)
endif(MSVC)
target_include_directories(T3GPU PRIVATE ${THIRD_PARTY_INCLUDE_DIRECTORIES} T3GPU_INCLUDE_DIRECTORY)
target_link_libraries(T3GPU PRIVATE ${THIRD_PARTY_LIBRARIES})
set_property(TARGET T3GPU PROPERTY CXX_STANDARD 20)
source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${T3GPU_SOURCES} ${T3GPU_HEADERS})

function(MakeExample TARGETNAME FILENAME)
	add_executable(${TARGETNAME} ${FILENAME})
	set_property(TARGET ${TARGETNAME} PROPERTY CXX_STANDARD 20)
	target_link_libraries(${TARGETNAME} PRIVATE T3GPU)
	target_include_directories(${TARGETNAME} PRIVATE ${T3GPU_INCLUDE_DIRECTORY} ${THIRD_PARTY_INCLUDE_DIRECTORIES})

endfunction(MakeExample)

MakeExample(t3 t3GPU.cpp)