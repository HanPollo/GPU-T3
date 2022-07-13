set_property(GLOBAL PROPERTY USE_FOLDERS TRUE)
define_property(
    TARGET
    PROPERTY FOLDER
    INHERITED
    BRIEF_DOCS "Set the folder name."
    FULL_DOCS  "Use to organize targets in an IDE."
)

function(add_subdirectory_with_folder _folder_name _folder)
    add_subdirectory(${_folder} ${ARGN})
    set_property(DIRECTORY "${_folder}" PROPERTY FOLDER "${_folder_name}")
endfunction()

add_subdirectory_with_folder("third_party" glad)
add_subdirectory_with_folder("third_party" glfw)
add_subdirectory_with_folder("third_party" stb)
add_subdirectory_with_folder("third_party" assimp-5.0.1)
add_subdirectory_with_folder("third_party/OpenMesh" OpenMesh-8.1)



