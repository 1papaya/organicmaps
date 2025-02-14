project(routing_quality)

set(
  SRC
  waypoints.cpp
  waypoints.hpp
)

omim_add_library(${PROJECT_NAME} ${SRC})

omim_link_libraries(
  ${PROJECT_NAME}
  routes_builder
  routing
  traffic
  routing_common
  transit
  storage
  indexer
  platform
  mwm_diff
  bsdiff
  geometry
  coding
  base
  icu
  jansson
  oauthcpp
  protobuf
  succinct
  ${LIBZ}
)

add_subdirectory(api)
add_subdirectory(routing_quality_tool)

omim_add_test_subdirectory(routing_quality_tests)

link_qt5_core(${PROJECT_NAME})
link_qt5_network(${PROJECT_NAME})
