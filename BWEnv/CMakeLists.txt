cmake_minimum_required(VERSION 3.1)

add_subdirectory(tsc-bw/mini-openbwapi)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}/include
	${CMAKE_CURRENT_SOURCE_DIR}/fbs
	${CMAKE_CURRENT_SOURCE_DIR}/../include
	${CMAKE_CURRENT_SOURCE_DIR}/tsc-bw/mini-openbwapi
	${SDL2_INCLUDE_DIR}
)

add_executable(bwenv
	src/main.cc
	src/config_manager.cc
	src/controller.cc
	src/user_actions.cc
	src/utils.cc
	src/zmq_server.cc
	../replayer/frame.cpp
)

target_link_libraries(bwenv
	czmq
	${SDL2_LIBRARY}
	mini-openbwapi
)
