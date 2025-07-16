cmake_minimum_required(VERSION 3.10)
project(hello-cpack VERSION 1.0.0 LANGUAGES C)

add_executable(hello main.c)

# Add this at the top
set(CMAKE_INSTALL_PREFIX "/usr")

# Then the install target
install(TARGETS hello
    RUNTIME DESTINATION bin
)

# CPACK configuration
include(InstallRequiredSystemLibraries)

set(CPACK_GENERATOR "DEB")
set(CPACK_PACKAGE_NAME "hello-cpack")
set(CPACK_PACKAGE_VERSION "${PROJECT_VERSION}")
set(CPACK_PACKAGE_CONTACT "you@example.com")
set(CPACK_DEBIAN_PACKAGE_MAINTAINER "Your Name")
set(CPACK_DEBIAN_PACKAGE_ARCHITECTURE "armhf")
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "Simple Hello World C program")

include(CPack)