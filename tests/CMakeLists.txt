cmake_minimum_required(VERSION 3.1...3.21)

project(test VERSION 0.0.1 LANGUAGES CXX)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_BINARY_DIR})
list(APPEND CMAKE_PREFIX_PATH ${CMAKE_BINARY_DIR})

find_package(libesp8266 CONFIG REQUIRED)

add_executable (${PROJECT_NAME} esp8266.test.cpp)

target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_20)
set_target_properties(${PROJECT_NAME} PROPERTIES CXX_EXTENSIONS OFF)
target_compile_definitions(${PROJECT_NAME} PRIVATE -DPLATFORM=test)
target_link_libraries(${PROJECT_NAME} PRIVATE
libesp8266::libesp8266
libembeddedhal::libembeddedhal)
