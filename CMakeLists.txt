CMAKE_MINIMUM_REQUIRED(VERSION 2.8.3)
project(rviz_vectorize_button)

FIND_PACKAGE(Qt5 COMPONENTS Core Gui REQUIRED)
FIND_PACKAGE(catkin COMPONENTS message_runtime message_generation std_msgs roscpp rviz)
SET(CMAKE_INCLUDE_CURRENT_DIR ON)
#SET(CMAKE_AUTOMOC ON)
SET(CMAKE_CXX_FLAGS "-std=c++0x -Wall -Werror")

ADD_DEFINITIONS(-DQT_NO_KEYWORDS)

add_message_files(DIRECTORY msg FILES WriteMsg.msg)
generate_messages(DEPENDENCIES std_msgs)

qt5_wrap_cpp(MOC_FILES src/rviz_vectorize_button.h)

catkin_package(
  LIBRARIES rviz_vectorize_button
  CATKIN_DEPENDS message_runtime std_msgs rviz)

include_directories(${catkin_INCLUDE_DIRS})
add_library(rviz_vectorize_button src/rviz_vectorize_button.cc ${MOC_FILES})
target_link_libraries(rviz_vectorize_button Qt5::Core Qt5::Gui)
add_dependencies(rviz_vectorize_button rviz_vectorize_button_generate_messages_cpp ${catkin_EXPORTED_TARGETS})

