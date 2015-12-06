PROJECT (CMakeMACTest)
cmake_minimum_required(VERSION 2.8)

add_executable(HelloWorld main.cpp)

INSTALL(TARGETS HelloWorld DESTINATION .)

INSTALL(CODE "
   include(BundleUtilities)
   fixup_bundle(\"${APPS}\"   \"\"   \"${DIRS}\")
   " COMPONENT Runtime)

set(CPACK_GENERATOR Bundle;DragNDrop;OSXX11;PackageMaker)
include(CPack)
