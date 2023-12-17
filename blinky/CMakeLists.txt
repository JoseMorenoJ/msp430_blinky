set(EXECUTABLE blinky)

set(ELF_FILE ${EXECUTABLE}.elf)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR})

set(CMAKE_EXE_LINKER_FLAGS
    "${CMAKE_EXE_LINKER_FLAGS} \
    -Wl,-Map,\"${EXECUTABLE}.map\" \
")

add_executable(${ELF_FILE}
    "${PROJECT_SOURCE_DIR}/blinky/main.c"
    "${PROJECT_SOURCE_DIR}/MSP430FR5xx_6xx/gpio.c"
    "${PROJECT_SOURCE_DIR}/MSP430FR5xx_6xx/wdt_a.c"
    "${PROJECT_SOURCE_DIR}/MSP430FR5xx_6xx/pmm.c"
    "${SOURCE_FILES}"
    )

msp430_add_executable_upload(${EXECUTABLE})
