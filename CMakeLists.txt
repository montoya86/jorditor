cmake_minimum_required(VERSION 2.6)
set(PROJECT_NAME jorditor)
project ( ${PROJECT_NAME} )

# declaring files in your project

set ( SOURCES
        main.cpp
        mainwindow.cpp
        )

set ( MOC_HEADERS
        mainwindow.h
        )

set ( RESOURCES
        application.qrc
        )

# Next lines needed for building all Qt projects
find_package(Qt5Widgets REQUIRED)
add_definitions( ${QT_DEFINITIONS} )
include_directories( ${CMAKE_BINARY_DIR} )


# Next, using precompiler, compiler and linker

# using Qt meta-system (precompiler)
QT5_ADD_RESOURCES( RES_SOURCES ${RESOURCES} )
QT5_WRAP_CPP( MOC_SRCS ${MOC_HEADERS} )

# compile
add_executable( ${PROJECT_NAME} ${SOURCES} ${MOC_SRCS} ${RES_SOURCES} ${UI_HEADERS} )
# or use line below instead, if you using Windows ™ Operating System.
#add_executable( ${PROJECT_NAME} WIN32 ${SOURCES} ${MOC_SRCS} ${RES_SOURCES} ${UI_HEADERS} )

# build it (link libraries)
target_link_libraries( ${PROJECT_NAME} ${QT_LIBRARIES} )
qt5_use_modules(${PROJECT_NAME} Widgets)