cmake_minimum_required(VERSION 3.13)

include(pico_sdk_import.cmake)

project(FirstExample C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
pico_sdk_init()

add_executable(FirstExample FirstExample.c)

pico_enable_stdio_usb(FirstExample 1)

pico_generate_pio_header(FirstExample ${CMAKE_CURRENT_LIST_DIR}/hello.pio)


pico_add_extra_outputs(FirstExample)

target_sources(FirstExample PRIVATE FirstExample.c)

target_link_libraries(FirstExample PRIVATE
        pico_stdlib
        hardware_pio
        )


