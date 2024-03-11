
# Define the library target with sources
add_library(${LIBRARY_NAME} SHARED
    stream_wrapper.cpp
    text_line_reader.cpp
    strnatcmp.c
    pipe_fitter.c
    # Add here other source files if needed
)

# Set properties for versioning
set_target_properties(${LIBRARY_NAME} PROPERTIES
    VERSION ${LIBGTU_VERSION}
    SOVERSION ${LIBGTU_SOVERSION}
    PUBLIC_HEADER "stream_wrapper.h;text_line_reader.h;container_join.h;natsort.h;strnatcmp.h;outbuf3.hpp;tuple_parser.h;exit_manip.h;inbuf1.hpp;pipe_fitter.h;string_tokenize.h"
    # Add all headers that should be installed
)

# Assuming `compiler_options` is defined in the root or passed down via `add_subdirectory`
target_link_libraries(${LIBRARY_NAME} PRIVATE compiler_options)

# Installation rules for the library and headers
install(TARGETS ${LIBRARY_NAME}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/${PROJECT_NAME}
)
