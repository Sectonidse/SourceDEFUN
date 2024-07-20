cmake_minimum_required(VERSION 3.10)

# Project Name and Version
project(SourceDEFUN VERSION 1.0.0)

macro(cxx14)
  set (CMAKE_CXX_STANDARD 14)
endmacro(cxx14)

# Add subdirectories as projects
add_subdirectory(game/client)
add_subdirectory(game/server)
add_subdirectory(materialsystem/swarmshaders)
add_subdirectory(materialsystem/shaderlib)
