cmake_minimum_required(VERSION 3.15)
project(gtextutils VERSION 0.7
    DESCRIPTION "Gordon's text-utility classes"
    LANGUAGES C CXX
    )
set(LIBRARY_NAME "libgtextutils")

include(GNUInstallDirs)
configure_file(
    ${CMAKE_CURRENT_SOURCE_DIR}/${PROJECT_NAME}.pc.in
    ${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}.pc
    @ONLY
)

include_directories(${PROJECT_BINARY_DIR})


# Options
option(ENABLE_WALL "Enable many common GCC warnings" ON)
option(ENABLE_DEBUG "Enable debug mode" ON)
option(ENABLE_TUPLE_PARSER_CHECK "Enable Tuple Parser Check (requires g++ > 4.3.2)" OFF)

# Interface Library for Compiler Options
add_library(compiler_options INTERFACE)
add_subdirectory(src)

# Common GCC warnings
if(ENABLE_WALL)
  target_compile_options(compiler_options INTERFACE
    -Wall
    -Wextra
    -Wformat-nonliteral
    -Wformat-security
    -Wswitch-default
    -Wswitch-enum
    -Wunused-parameter
    -Wfloat-equal
    -Werror
  )
endif()

# Debug mode
if(ENABLE_DEBUG)
  target_compile_definitions(compiler_options INTERFACE DEBUG=1)
  target_compile_options(compiler_options INTERFACE -g -O1)
else()
  target_compile_options(compiler_options INTERFACE -O3)
endif()

# Tuple Parser Check
if(ENABLE_TUPLE_PARSER_CHECK)
  target_compile_definitions(compiler_options INTERFACE TUPLE_PARSER_CHECK=1)
endif()

# Install the .pc file to the appropriate directory
install(
    FILES ${CMAKE_CURRENT_BINARY_DIR}/gtextutils.pc
    DESTINATION ${CMAKE_INSTALL_LIBDIR}/pkgconfig
)
