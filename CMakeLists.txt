PROJECT (CMakeMACTest)
cmake_minimum_required(VERSION 2.8)

#------------------------------------
# Rapidjson
add_definitions(-DRAPIDJSON_HAS_STDSTRING=1)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
add_library(unqlite SHARED unqlite.c)

add_executable(HelloWorld main.cpp)

INSTALL(TARGETS HelloWorld DESTINATION .)
#INSTALL(TARGETS unqlite DESTINATION .)

target_link_libraries(HelloWorld unqlite)

#set(APPS "${CMAKE_INSTALL_PREFIX}/HelloWorld")  # paths to executables
set(APPS "/Users/travis/build/micfort/CMakeMACTest/_CPack_Packages/Darwin/Bundle/CMakeMACTest-0.1.1-Darwin/HelloWorld.app/Contents/Resources/./HelloWorld")  # paths to executables
set(DIRS "./")   # directories to search for prerequisites

INSTALL(CODE "
   include(BundleUtilities)
   fixup_bundle(\"${APPS}\"   \"\"   \"${DIRS}\")
   " COMPONENT Runtime)

set(CPACK_BUNDLE_NAME HelloWorld)
set(CPACK_BUNDLE_ICON OpenPSTD.icns)
set(CPACK_BUNDLE_PLIST Info.plist)
set(CPACK_BUNDLE_STARTUP_COMMAND HelloWorld)
   
set(CPACK_GENERATOR Bundle;DragNDrop;OSXX11;PackageMaker)
include(CPack)
