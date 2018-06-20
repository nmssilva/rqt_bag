cmake_minimum_required(VERSION 2.8.3)
project(rqt_bag)

find_package(catkin REQUIRED
   std_msgs
   message_generation
)

catkin_python_setup()

add_message_files(
  FILES
  Control.msg
)

add_service_files(
  FILES
  Pause.srv
)

generate_messages(
  DEPENDENCIES
  std_msgs
)

catkin_package(CATKIN_DEPENDS message_runtime)

install(FILES plugin.xml
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

install(DIRECTORY launch resource
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

install(PROGRAMS scripts/rqt_bag
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
