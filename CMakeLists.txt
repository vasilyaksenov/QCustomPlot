cmake_minimum_required(VERSION 3.16)

project(QCustomPlot LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Widgets PrintSupport)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Widgets PrintSupport)

add_library(qcustomplot 
  qcustomplot.cpp
  qcustomplot.h
)

target_link_libraries(qcustomplot PRIVATE Qt${QT_VERSION_MAJOR}::Widgets Qt${QT_VERSION_MAJOR}::PrintSupport)
add_library(QCustomPlot::QCustomPlot ALIAS qcustomplot)
target_include_directories(qcustomplot INTERFACE ${CMAKE_CURRENT_LIST_DIR})

add_subdirectory(examples)  