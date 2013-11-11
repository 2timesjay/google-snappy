CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
INCLUDE(CheckFunctionExists)
INCLUDE(CheckIncludeFile)
INCLUDE(CheckIncludeFiles)
INCLUDE(CheckLibraryExists)
INCLUDE(CheckSymbolExists)
INCLUDE(CheckTypeSize)

ADD_DEFINITIONS(-DBUILDING_SNAPPY)

ADD_LIBRARY(snappy SHARED
            snappy.cc
            snappy-sinksource.cc
            snappy-stubs-internal.cc
            snappy-c.cc)
#SET_TARGET_PROPERTIES(snappy PROPERTIES SOVERSION 1.1.1)

INSTALL(FILES
        snappy.h
        snappy-c.h
        snappy-sinksource.h
        snappy-stubs-public.h
        snappy-visibility.h
        DESTINATION include)

INSTALL(TARGETS snappy
        RUNTIME DESTINATION bin
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib)


CONFIGURE_FILE(${CMAKE_CURRENT_SOURCE_DIR}/config.cmake.h.in
               ${CMAKE_CURRENT_BINARY_DIR}/config.h)
#CONFIGURE_FILE(${CMAKE_CURRENT_SOURCE_DIR}/snappy-stubs-public.h.in
#               ${CMAKE_CURRENT_BINARY_DIR}/snappu-stubs-public.h)
