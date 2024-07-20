cmake_minimum_required(VERSION 3.10)

# Project Name and Version
project(SourceDEFUN VERSION 1.0.0)

# Compatibility \(Test change, see if it compiles now)
set_property(PROPERTY CXX_STANDARD 11)

# Add subdirectories as projects
add_subdirectory(game/client)
add_subdirectory(game/server)
add_subdirectory(materialsystem/swarmshaders)
add_subdirectory(materialsystem/shaderlib)
