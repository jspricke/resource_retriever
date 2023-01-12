cmake_minimum_required(VERSION 3.10)
project(libcurl_vendor C)

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_vendor_package REQUIRED)

find_package(CURL QUIET)

ament_vendor(libcurl_vendor
  SATISFIED ${CURL_FOUND}
  VCS_TYPE tar
  VCS_URL https://github.com/curl/curl/releases/download/curl-7_81_0/curl-7.81.0.tar.gz
  VCS_VERSION curl-7.81.0
  CMAKE_ARGS
    -DENABLE_MANUAL:BOOL=OFF
    -DCURL_ENABLE_SSL:BOOL=ON  # default, but just to make clear
    -DUSE_LIBIDN2:BOOL=OFF
)

ament_package(
  CONFIG_EXTRAS "libcurl_vendor-extras.cmake.in"
)
