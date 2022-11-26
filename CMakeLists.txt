cmake_minimum_required(VERSION 3.8.2)

project(usbguard-applet-qt)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall")

find_package(Qt5 REQUIRED COMPONENTS Widgets)

find_package(PkgConfig REQUIRED)
pkg_check_modules(usbguard REQUIRED IMPORTED_TARGET libusbguard)

add_executable(usbguard-applet-qt
  src/DeviceDialog.cpp
  src/DeviceModel.cpp
  src/main.cpp
  src/MainWindow.cpp
  src/SessionBlocker.cpp
  src/TargetDelegate.cpp
  src/DeviceDialog.h
  src/DeviceModel.h
  src/MainWindow.h
  src/SessionBlocker.h
  src/TargetDelegate.h
  src/MainWindow.ui
)

target_link_libraries(usbguard-applet-qt Qt5::Widgets PkgConfig::usbguard)

install(TARGETS usbguard-applet-qt DESTINATION bin)
