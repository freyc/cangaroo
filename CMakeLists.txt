cmake_minimum_required(VERSION 3.20)

project(cangaroo C CXX)

add_library(qt_framework INTERFACE)

find_package(Qt6 COMPONENTS Widgets Xml Core5Compat QUIET)
if(NOT Qt6_FOUND)
    find_package(Qt5 5.15 REQUIRED COMPONENTS Widgets Xml)
    target_link_libraries(qt_framework INTERFACE Qt::Widgets Qt::Xml)
else()
    target_link_libraries(qt_framework INTERFACE Qt::Widgets Qt::Xml Qt::Core5Compat)
endif()

add_subdirectory(canifconfig)

add_subdirectory(src)
