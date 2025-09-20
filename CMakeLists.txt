cmake_minimum_required(VERSION 3.10)
project(JWasm C)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)

# Add source files
file(GLOB SOURCES src/*.c)

add_executable(jwasm ${SOURCES})

if(MSVC)
    target_compile_options(jwasm PRIVATE -D_CRT_SECURE_NO_WARNINGS)
endif()

# Include directories
target_include_directories(jwasm PRIVATE src/H)

# Optional: Set output directory
set_target_properties(jwasm PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin"
)