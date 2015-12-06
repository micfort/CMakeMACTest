PROJECT (CMakeMACTest)
cmake_minimum_required(VERSION 2.8)

add_executable(HelloWorld main.cpp)

INSTALL(TARGETS HelloWorld DESTINATION .)

set(CPACK_GENERATOR ZIP)
include(CPack)
