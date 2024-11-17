if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "RelWithDebInfo" CACHE STRING "" FORCE)
endif()

cmake_minimum_required(VERSION 3.16)

project(thirdparty-gtsam)

set(GTSAM_ENABLE_BOOST_SERIALIZATION OFF)
set(GTSAM_USE_BOOST_FEATURES OFF)
set(GTSAM_BUILD_UNSTABLE ON)
set(GTSAM_ALLOW_DEPRECATED_SINCE_V42 OFF)

include(FetchContent)
fetchcontent_declare(
    gtsam
    GIT_REPOSITORY    https://github.com/mcm001/gtsam
    GIT_TAG           23362b8e79b832deafd71f17d2a72f9d9f734ced
)
fetchcontent_makeavailable(gtsam)

add_subdirectory(allwpilib)

set(CMAKE_CXX_STANDARD 20)

add_executable(constrained_solvepnp_test 
  src/ConstrainedPnp.cpp
  src/TagModel.cpp
  src/gtsam_utils.cpp)

target_link_libraries(constrained_solvepnp_test 
  gtsam 
  gtsam_unstable 
  wpimath
  apriltag
)
