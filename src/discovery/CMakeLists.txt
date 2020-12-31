project(QtZeroConfExample)
cmake_minimum_required(VERSION 2.8.11)

find_package(Qt5 COMPONENTS Gui Widgets Network REQUIRED)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)
set(QtZeroConf_LIB ${CMAKE_BINARY_DIR}/lib/QtZeroConf/libQtZeroConf.so)
# Find QtZeroConf library if we're building standalone
if(NOT TARGET QtZeroConf)
    find_package(QtZeroConf CONFIG REQUIRED)
endif()
include_directories(
    ${SRC_DIRECTORY}/lib/QtZeroConf

)
message("======================> " ${SRC_DIRECTORY}/lib/QtZeroConf)
add_executable(Discovery
    window.h
    window.cpp
    main.cpp
)

target_link_libraries(Discovery
    ${QtZeroConf_LIB}
    Qt5::Gui Qt5::Widgets
    Qt5::Network
)
