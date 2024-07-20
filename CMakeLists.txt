cmake_minimum_required(VERSION 3.10)

# Project Name and Version
project(SourceDEFUN VERSION 1.0.0)

set (CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if (${IS_LINUX})
  add_compile_options(
	  -g
	  -m32
	  $<$<COMPILE_LANGUAGE:CXX>:-fpermissive>
	  -fdiagnostics-color
	  -Wno-narrowing
	  $<${IS_LINUX}:-U_FORTIFY_SOURCE>
	  -Usprintf
	  -Ustrncpy
	  -UPROTECTED_THINGS_ENABLE
	  -fabi-compat-version=2>
  )
endif()

# Add subdirectories as projects
add_subdirectory(game/client)
add_subdirectory(game/server)
add_subdirectory(materialsystem/swarmshaders)
add_subdirectory(materialsystem/shaderlib)
