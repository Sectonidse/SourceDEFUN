# Set the project name
project(shaderlib)

# Location of source files relative to this CMakeLists.txt
set(SOURCE_FILES
  BaseShader.cpp
  ShaderDLL.cpp
  shaderlib_cvar.cpp
)

# Location of header files relative to this CMakeLists.txt
set(HEADER_FILES
  ../../public/shaderlib/BaseShader.h
  ../../public/tier0/basetypes.h
  ../../public/tier0/commonmacros.h
  ../../public/shaderlib/cshader.h
  ../../public/tier0/dbg.h
  ../../public/tier0/fasttimer.h
  ../../public/appframework/IAppSystem.h
  ../../public/tier0/icommandline.h
  ../../public/icvar.h
  ../../public/materialsystem/imaterial.h
  ../../public/materialsystem/imaterialsystem.h
  ../../public/materialsystem/imaterialsystemhardwareconfig.h
  ../../public/materialsystem/imaterialvar.h
  ../../public/materialsystem/imesh.h
  ../../public/materialsystem/IShader.h
  ../../public/materialsystem/ishaderapi.h
  ../IShaderSystem.h
  ../../public/materialsystem/itexture.h
  ../../public/materialsystem/materialsystem_config.h
  ../../public/mathlib/mathlib.h
  ../../public/tier0/memdbgoff.h
  ../../public/tier0/memdbgon.h
  ../../public/tier0/platform.h
  ../../public/tier0/protected_things.h
  ../../public/shaderlib/ShaderDLL.h
  shaderDLL_Global.h
  shaderlib_cvar.h
  ../../public/string_t.h
  ../../public/tier1/strtools.h
  ../../public/tier1/utlmemory.h
  ../../public/tier1/utlvector.h
  ../../public/mathlib/vector.h
  ../../public/mathlib/vector2d.h
  ../../public/mathlib/vector4d.h
  ../../public/mathlib/vmatrix.h
  ../../public/mathlib/vplane.h
  ../../public/vstdlib/vstdlib.h
)

include_directories(
  ../../common
  ../../public
  ../../public/tier0
  ../../public/tier1
  ../../public/mathlib
  ../../public/shaderlib
  ../../public/materialsystem
  ../../public/appframework
  ../../materialsystem
)

# Add compiler flags based on configuration (Debug/Release)
if(CMAKE_BUILD_TYPE MATCHES "Debug")
  # Debug flags (e.g. disable optimizations)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /Od")
else()
  # Release flags (e.g. enable optimizations)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /O2")
endif()

# Add source and header files
add_library(shaderlib STATIC ${SOURCE_FILES} ${HEADER_FILES})

# Target compiler and platform (assuming Visual Studio)
target_compile_features(shaderlib PRIVATE)

# Add preprocessor definitions
if (WIN32)
  set(PREPROCESSOR_DEFINITIONS WIN32;_WIN32;_DEBUG;DEBUG;_LIB;_CRT_SECURE_NO_DEPRECATE;_CRT_NONSTDC_NO_DEPRECATE;VPCGAME=swarm;VPCGAMECAPS=SWARM;_DLL_EXT=.dll;COMPILER_MSVC32;COMPILER_MSVC;LIBNAME=shaderlib;FAST_MATERIALVAR_ACCESS)
  add_compile_definitions(${PREPROCESSOR_DEFINITIONS})
endif (WIN32)
if (UNIX)
  set(PREPROCESSOR_DEFINITIONS LINUX;_LINUX;POSIX;_POSIX;UNIX;_UNIX;_DEBUG;DEBUG;_LIB;_CRT_SECURE_NO_DEPRECATE;_CRT_NONSTDC_NO_DEPRECATE;VPCGAME=swarm;VPCGAMECAPS=SWARM;_DLL_EXT=.dll;COMPILER_GCC;LIBNAME=shaderlib;FAST_MATERIALVAR_ACCESS)
  add_compile_definitions(${PREPROCESSOR_DEFINITIONS})
endif (UNIX)

# Optional: Set output directory for the library
if (WIN32)
set_target_properties(shaderlib PROPERTIES OUTPUT_DIRECTORY ../../lib/public)
endif (WIN32)
