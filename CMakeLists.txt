PROJECT (CMakeMACTest)
cmake_minimum_required(VERSION 2.8)

add_executable(HelloWorld main.cpp)

INSTALL(TARGETS HelloWorld DESTINATION .)

set(APPS "HelloWorld")  # paths to executables
set(DIRS " ")   # directories to search for prerequisites

#INSTALL(CODE "
#   include(BundleUtilities)
#   fixup_bundle(\"${APPS}\"   \"\"   \"${DIRS}\")
#   " COMPONENT Runtime)

set(CPACK_BUNDLE_NAME HelloWorld)
set(CPACK_BUNDLE_ICON OpenPSTD.icns)
set(CPACK_BUNDLE_PLIST Info.plist)
set(CPACK_BUNDLE_STARTUP_COMMAND HelloWorld)
   
set(CPACK_GENERATOR Bundle;DragNDrop;OSXX11;PackageMaker)
include(CPack)
