project(generator-${LIBROMFS_PROJECT_NAME})
set(CMAKE_CXX_STANDARD 20)

# This is a code generator, so when cross compiling it should be built with the host (native) toolchain
if(CMAKE_CROSSCOMPILING)
    SET(CMAKE_C_COMPILER ${NATIVE_CMAKE_C_COMPILER})
    SET(CMAKE_CXX_COMPILER ${NATIVE_CMAKE_CXX_COMPILER})
    SET(CMAKE_C_FLAGS ${NATIVE_CMAKE_C_FLAGS})
    SET(CMAKE_CXX_FLAGS ${NATIVE_CMAKE_CXX_FLAGS})
endif()


# Add sources
add_executable(${PROJECT_NAME}
    source/main.cpp
)
target_compile_definitions(${PROJECT_NAME} PRIVATE RESOURCE_LOCATION="${LIBROMFS_RESOURCE_LOCATION}" LIBROMFS_PROJECT_NAME="${LIBROMFS_PROJECT_NAME}")
target_include_directories(${PROJECT_NAME} PRIVATE include)

# Export generated romfs resource file to libromfs
set(ROMFS "libromfs_resources.cpp" PARENT_SCOPE)
set(ROMFS "libromfs_resources.cpp")