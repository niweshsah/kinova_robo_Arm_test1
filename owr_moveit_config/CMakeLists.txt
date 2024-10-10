cmake_minimum_required(VERSION 3.1.3)
project(owr_moveit_config)

if(CMAKE_COMPILER_IS_GNUCXX OR ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang"))
    set(CMAKE_CXX_FLAGS "-std=c++11 ${CMAKE_CXX_FLAGS}")
endif()

find_package(catkin REQUIRED COMPONENTS
  message_generation
  moveit_core
  moveit_ros_planning
  moveit_ros_planning_interface
  trac_ik_lib
  moveit_msgs
  roscpp
  std_msgs
  pluginlib
)

#find_package(Boost REQUIRED)
find_package(Boost REQUIRED COMPONENTS date_time)
# find_package(orocos_kdl REQUIRED)

## Generate added messages and services with any dependencies listed here
generate_messages(
  DEPENDENCIES
  std_msgs
 )

catkin_package(
  CATKIN_DEPENDS
    trac_ik_lib
  DEPENDS
    Boost
    orocos_kdl
)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
include_directories(
  include
  ${catkin_INCLUDE_DIRS}
  ${Boost_INCLUDE_DIRS}
  ${orocos_kdl_INCLUDE_DIRS}
)

## Declare a C++ executable
add_executable(setHomePose src/setHomePose.cpp)
## Add cmake target dependencies of the executable
## same as for the library above
add_dependencies(setHomePose ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
## Specify libraries to link a library or executable target against
target_link_libraries(setHomePose ${catkin_LIBRARIES})

add_executable(owr_ik_tests src/ik_tests.cpp)
target_link_libraries(owr_ik_tests ${catkin_LIBRARIES} ${Boost_LIBRARIES} ${orocos_kdl_LIBRARIES})

#############
## Install ##
#############

install(DIRECTORY launch DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  PATTERN "setup_assistant.launch" EXCLUDE)
install(DIRECTORY config DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
install(DIRECTORY src DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})

































# cmake_minimum_required(VERSION 3.1.3)
# project(owr_moveit_config)

# if(CMAKE_COMPILER_IS_GNUCXX OR ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang"))
#     set(CMAKE_CXX_FLAGS "-std=c++11 ${CMAKE_CXX_FLAGS}")
# endif()


# if(NLopt_FOUND)
#   target_link_libraries(Minimizer PUBLIC nlopt)
#   target_include_directories(Minimizer PUBLIC ${NLopt_INCLUDE_DIR})
# endif()


# find_package(catkin REQUIRED COMPONENTS
#   message_generation
#   moveit_core
#   moveit_ros_planning
#   moveit_ros_planning_interface
#   trac_ik_lib
#   moveit_msgs
#   roscpp
#   std_msgs
#   pluginlib
# )

# find_package(Boost REQUIRED COMPONENTS date_time)
# find_package(orocos_kdl REQUIRED)
# find_package(nlopt REQUIRED)  # Added NLopt

# ## Generate added messages and services with any dependencies listed here
# generate_messages(
#   DEPENDENCIES
#   std_msgs
#  )

# catkin_package(
#   CATKIN_DEPENDS
#     trac_ik_lib
#   DEPENDS
#     Boost
#     orocos_kdl
#     nlopt  # Added NLopt
# )

# ###########
# ## Build ##
# ###########

# ## Specify additional locations of header files
# ## Your package locations should be listed before other locations
# include_directories(
#   include
#   ${catkin_INCLUDE_DIRS}
#   ${Boost_INCLUDE_DIRS}
#   ${orocos_kdl_INCLUDE_DIRS}
#   ${nlopt_INCLUDE_DIRS}  # Added NLopt include directory
# )

# ## Declare a C++ executable
# add_executable(setHomePose src/setHomePose.cpp)
# ## Add cmake target dependencies of the executable
# ## same as for the library above
# add_dependencies(setHomePose ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
# ## Specify libraries to link a library or executable target against
# target_link_libraries(setHomePose ${catkin_LIBRARIES})

# add_executable(owr_ik_tests src/ik_tests.cpp)
# target_link_libraries(owr_ik_tests ${catkin_LIBRARIES} ${Boost_LIBRARIES} ${orocos_kdl_LIBRARIES} ${nlopt_LIBRARIES})  # Linked NLopt library

# #############
# ## Install ##
# #############

# install(DIRECTORY launch DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
#   PATTERN "setup_assistant.launch" EXCLUDE)
# install(DIRECTORY config DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
# install(DIRECTORY src DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})


































# cmake_minimum_required(VERSION 3.1.3)
# project(owr_moveit_config)

# ## Specify C++ Standard
# if(CMAKE_COMPILER_IS_GNUCXX OR ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang"))
#     set(CMAKE_CXX_FLAGS "-std=c++11 ${CMAKE_CXX_FLAGS}")
# endif()

# ## Find Catkin and other ROS packages
# find_package(catkin REQUIRED COMPONENTS
#   message_generation
#   moveit_core
#   moveit_ros_planning
#   moveit_ros_planning_interface
#   trac_ik_lib
#   moveit_msgs
#   roscpp
#   std_msgs
#   pluginlib
# )

# ## Find Boost components
# find_package(Boost REQUIRED COMPONENTS date_time)

# ## Use pkg-config to find NLOpt (instead of find_package)
# find_package(PkgConfig REQUIRED)
# pkg_check_modules(NLOPT REQUIRED nlopt)

# ## Generate added messages and services with any dependencies listed here
# generate_messages(
#   DEPENDENCIES
#   std_msgs
# )

# ## Catkin package
# catkin_package(
#   CATKIN_DEPENDS
#     trac_ik_lib
#   DEPENDS
#     Boost
#     orocos_kdl
#     NLOPT
# )

# ###########
# ## Build ##
# ###########

# ## Specify additional locations of header files
# include_directories(
#   include
#   ${catkin_INCLUDE_DIRS}
#   ${Boost_INCLUDE_DIRS}
#   ${NLOPT_INCLUDE_DIRS}  ## Include NLOpt headers
# )

# ## Declare C++ executables
# add_executable(setHomePose src/setHomePose.cpp)
# add_dependencies(setHomePose ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
# target_link_libraries(setHomePose ${catkin_LIBRARIES} ${NLOPT_LIBRARIES})  ## Link against NLOpt

# add_executable(owr_ik_tests src/ik_tests.cpp)
# add_dependencies(owr_ik_tests ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
# target_link_libraries(owr_ik_tests ${catkin_LIBRARIES} ${Boost_LIBRARIES} ${NLOPT_LIBRARIES})  ## Link against Boost and NLOpt

# #############
# ## Install ##
# #############

# ## Mark directories for installation
# install(DIRECTORY launch DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION} PATTERN "setup_assistant.launch" EXCLUDE)
# install(DIRECTORY config DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
# install(DIRECTORY src DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})





















































