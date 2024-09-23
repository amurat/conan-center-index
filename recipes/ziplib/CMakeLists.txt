cmake_minimum_required(VERSION 3.15)
project(ziplib)

file(GLOB_RECURSE LZMA "ZipLib/extlibs/lzma/unix/*.c")
add_library(zipliblzma ${LZMA})

file(GLOB SOURCES "ZipLib/*.cpp")
file(GLOB DETAIL "ZipLib/detail/*.cpp")
file(GLOB_RECURSE HEADERS "ZipLib/*.h")
add_library(ziplib ${SOURCES} ${DETAIL})

target_sources(ziplib PUBLIC FILE_SET a TYPE HEADERS FILES "${HEADERS}")

install(TARGETS ziplib FILE_SET a DESTINATION include)

set_property(TARGET ziplib PROPERTY CXX_STANDARD 11)

install(TARGETS ziplib)
install(TARGETS zipliblzma)
