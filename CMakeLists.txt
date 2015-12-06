PROJECT (CMakeMACTest)
cmake_minimum_required(VERSION 2.8)

add_executable(QtTest main.cpp)

INSTALL(TARGETS QtTest DESTINATION .)

set(CPACK_GENERATOR ZIP)
include(CPack)
