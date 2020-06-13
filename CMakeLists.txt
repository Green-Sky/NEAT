cmake_minimum_required(VERSION 3.0)
project(neat C CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

if(NOT CMAKE_BUILD_TYPE)
	set(CMAKE_BUILD_TYPE "Debug")
endif()

add_library(neat
	./include/gene.h
	./include/genome.h
	./include/innovation.h
	./include/link.h
	./include/neat.h
	./include/network.h
	./include/nnode.h
	./include/organism.h
	./include/population.h
	./include/species.h
	./include/trait.h

	./src/gene.cpp
	./src/genome.cpp
	./src/innovation.cpp
	./src/link.cpp
	./src/neat.cpp
	./src/network.cpp
	./src/nnode.cpp
	./src/organism.cpp
	./src/population.cpp
	./src/species.cpp
	./src/trait.cpp
)

target_include_directories(neat PUBLIC "include")

add_executable(neat_experiments
	./experiments/experiments.h
	./experiments/experiments.cpp

	./experiments/neatmain.h
	./experiments/neatmain.cpp
)

target_include_directories(neat PUBLIC "experiments")

target_link_libraries(neat_experiments PUBLIC
	neat
)

