# Copyright (c) 2016 Joshua Brookover

cmake_minimum_required( VERSION 3.0 )
project( bgfx-projects )
add_subdirectory( deps )
include( deps/bgfx.cmake/cmake/util/ConfigureDebugging.cmake )
add_library( bigg STATIC src/bigg.cpp src/bigg_assets.h include/bigg.hpp )
target_link_libraries( bigg PUBLIC bgfx imgui glfw glm )
target_include_directories( bigg PUBLIC include )
add_subdirectory( examples )

option( BIGG_ASSET_GEN "Generate binary assets." OFF )
if( BIGG_ASSET_GEN )
	add_subdirectory( assets/gen )
endif()