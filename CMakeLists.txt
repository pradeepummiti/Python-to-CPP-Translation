project(python_cpp)

cmake_minimum_required(VERSION 3.4)

set(CMAKE_CXX_STANDARD 11)

set(CMAKE_BUILD_TYPE Debug)

add_library(localizer
	debugging_helpers.cpp
	helpers.cpp
	localizer.cpp
	simulate.cpp
)

target_include_directories(localizer
	PUBLIC
		./
)

add_executable(localizer_tests
	tests.cpp
)

target_link_libraries(localizer_tests
	PUBLIC
		localizer
)

add_executable(simulation
	simulation.cpp
)

target_link_libraries(simulation
	localizer
)
