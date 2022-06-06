cmake_minimum_required(VERSION 3.8)
project(eigen_ros2)

find_package(ament_cmake REQUIRED)

# set(EIGEN_VERSION "3.4.0" CACHE STRING "version of eigen version will be installed")

# if(NOT EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/include/eigen-${EIGEN_VERSION})
#     execute_process(
#         # COMMAND bash ${CMAKE_CURRENT_SOURCE_DIR}/getEigen.sh '${CMAKE_CURRENT_SOURCE_DIR}'
#         COMMAND wget https://gitlab.com/libeigen/eigen/-/archive/${EIGEN_VERSION}/eigen-${EIGEN_VERSION}.tar.bz2 -P ${CMAKE_CURRENT_SOURCE_DIR}/include
#         COMMAND tar -jxvf ${CMAKE_CURRENT_SOURCE_DIR}/include/eigen-${EIGEN_VERSION}.tar.bz2 -C ${CMAKE_CURRENT_SOURCE_DIR}/include
#     )

# endif()

# include(FetchContent)
# FetchContent_Declare(eigen_src
#     URL https://gitlab.com/libeigen/eigen/-/archive/3.4.0/eigen-3.4.0.tar.bz2
#     URL_HASH MD5=0cb037162b00a50f79674555f6ca62a6
#     DOWNLOAD_NO_EXTRACT true
# )
# FetchContent_MakeAvailable(eigen_src)

add_library(${PROJECT_NAME} INTERFACE)
target_include_directories(${PROJECT_NAME} INTERFACE
  "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>"
  "$<INSTALL_INTERFACE:include>"
)

install(
  TARGETS ${PROJECT_NAME}
  EXPORT "export_${PROJECT_NAME}"
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION lib
  INCLUDES DESTINATION include
)

install(DIRECTORY include/Eigen
  DESTINATION "include"
)

ament_export_targets("export_${PROJECT_NAME}")
ament_package()