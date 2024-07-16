cmake_minimum_required(VERSION 3.10)

# Project Name and Version (Optional)
project(MyGameProject VERSION 1.0.0)

# Find dependencies (if any)
# For example: find_package(OpenGL REQUIRED)

# Add subdirectories as projects
#add_subdirectory(client)
#add_subdirectory(server)
#add_subdirectory(game_shader_generic_deferred)
add_subdirectory(materialsystem/shaderlib)  # Assuming shaderlib is located here

# Optional: Add targets to build all subdirectories at once
# This is just an example, you might need to adjust it based on your project structure
#add_custom_target(build_all ALL COMMAND make VERBOSE_MAKEFILE=1)
