set(JSON_BuildTests OFF CACHE BOOL "Don't build json tests")
set(BUILD_CPR_TESTS OFF CACHE BOOL "Don't build cpr tests")

find_package(CURL)
if(CURL_FOUND)
    set(USE_SYSTEM_CURL ON CACHE BOOL "Use the system curl for faster builds")
    set(CURL_CA_PATH_SET NONE)
endif()

find_package(OpenSSL)
if(OPENSSL_FOUND)
    set(CMAKE_USE_OPENSSL ON CACHE BOOL "Use OPENSSL for cpr")
else()
    set(CMAKE_USE_OPENSSL OFF CACHE BOOL "OPENSSL not found")
endif()

add_subdirectory(json)
add_subdirectory(cpr)