
project(canifconfig)

find_package(PkgConfig)

pkg_check_modules(LIBNL REQUIRED libnl-3.0)
pkg_check_modules(LIBNL_ROUTE REQUIRED libnl-route-3.0)

add_executable(${PROJECT_NAME} main.c)

target_link_libraries(${PROJECT_NAME} PRIVATE ${LIBNL_LIBRARIES} ${LIBNL_ROUTE_LIBRARIES})
target_include_directories(${PROJECT_NAME} PRIVATE ${LIBNL_INCLUDE_DIRS})
