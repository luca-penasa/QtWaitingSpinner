project(QtWaitingSpinner)



set(CMAKE_AUTOMOC ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)
#set (CMAKE_AUTOUIC ON)

#set(CMAKE_AUTORCC ON)


#find_package(Qt4 COMPONENTS QtCore QtGui REQUIRED)
##      set (QT_USE_QTOPENGL TRUE))
#include(${QT_USE_FILE})

if(VTK_QT_VERSION VERSION_GREATER "4")
    # Instruct CMake to run moc automatically when needed.
    find_package(Qt5Widgets REQUIRED QUIET)
else()
    find_package(Qt4 COMPONENTS QtGui QtOpenGL QtCore QtSql QtTest REQUIRED)
    include(${QT_USE_FILE})
endif()


file (GLOB source *.cpp)
file (GLOB header *.h)


message("sources ${source}" )

if(VTK_QT_VERSION VERSION_GREATER "4") # when on qt5
    add_library(${PROJECT_NAME} STATIC ${source} ${header})
    qt5_use_modules(${PROJECT_NAME} Widgets)
#    target_link_libraries(${CMAKE_PROJECT_NAME )
else() # we are on qt4
    add_library(${PROJECT_NAME} STATIC ${source} ${header})
    target_link_libraries(${PROJECT_NAME} ${QT_LIBRARIES} )
endif()


