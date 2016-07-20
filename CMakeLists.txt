project(QtWaitingSpinner)



set(CMAKE_AUTOMOC ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)
#set (CMAKE_AUTOUIC ON)

#set(CMAKE_AUTORCC ON)

find_package(Qt4 COMPONENTS QtCore QtGui REQUIRED)
#      set (QT_USE_QTOPENGL TRUE))
include(${QT_USE_FILE})


file (GLOB source *.cpp)
file (GLOB header *.h)


message("sources ${source}" )

add_library(${PROJECT_NAME} STATIC ${source} ${header})
target_link_libraries(${PROJECT_NAME} ${QT_LIBRARIES} )
