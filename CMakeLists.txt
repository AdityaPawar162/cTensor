cmake_minimum_required(VERSION 3.10)
project(cTensor C)

set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)

include_directories(include)

file(GLOB_RECURSE SOURCES "src/*.c")

add_executable(main ${SOURCES} src2/main.c)
target_link_libraries(main m)

target_compile_options(main PRIVATE
    -O0
    -Wfatal-errors
    -g
    -DDEBUG
)


target_compile_options(main PRIVATE -fsanitize=address,undefined)
target_link_options(main PRIVATE -fsanitize=address,undefined)
