project(game_shader_generic_deferred)

# source files
set(SOURCE_FILES
  BaseVSShader.cpp
  deferred_model.cpp
  deferred_brush.cpp
  IDeferredExt.cpp
  debug_shadow.cpp
  lighting_global.cpp
  debug_lightingctrl.cpp
  lighting_pass_basic.cpp
  lighting_pass_volum.cpp
  defpass_shadow.cpp
  defpass_gbuffer.cpp
  defpass_composite.cpp
  lighting_volume.cpp
  lighting_world.cpp
  volume_prepass.cpp
  blur.cpp
  volume_blend.cpp
  deferred_utility.cpp
  radiosity_global.cpp
  debug_radiosity_grid.cpp
  radiosity_propagate.cpp
  radiosity_blend.cpp
  screenspace_shading.cpp
  deferred_decalModulate.cpp
  screenspace_combine.cpp
  pbr_dx9.cpp
)

# header files
set(HEADER_FILES
  BaseVSShader.h
  deferred_context.h
  deferred_includes.h
  deferred_utility.h
  IDeferredExt.h
  lighting_helper.h
  deferred_global_common.h
  cpp_shader_constant_register_map.h
  common_fxc.h
  common_hlsl_cpp_consts.h
  common_pragmas.h
  common_ps_fxc.h
  common_vertexlitgeneric_dx9.h
  common_vs_fxc.h
  commandbuilder.h
  common_deferred_fxc.h
  lighting_pass_basic.h
  common_lighting_fxc.h
  common_shadowmapping_fxc.h
  lighting_pass_volum.h
  defpass_shadow.h
  defpass_gbuffer.h
  defpass_composite.h
  pbr_common_ps2_3_x.h
)

# header directories
include_directories(
  ../../common
  ../../public
  ../../public/tier0
  ../../public/tier1
  ../../dx9sdk/include
  fxctmp9
  include
  vshtmp9
)

# link directories
link_directories(
  ../../lib/common
  ../../lib/public
)

# link libraries
link_libraries(
  version.lib
  winmm.lib
  ../../dx9sdk/lib/d3dx9
  ../../public/interfaces
  ../../public/mathlib
  ../../public/matsys_controls
  ../../public/shaderlib
  ../../public/tier0
  ../../public/tier1
  ../../public/tier2
  ../../public/tier3
  ../../public/vstdlib
)

add_library(game_shader_generic_deferred SHARED ${SOURCE_FILES} ${HEADER_FILES})

# Target compiler and platform (assuming Visual Studio)
target_compile_features(game_shader_generic_deferred PRIVATE)

# Add preprocessor definitions
if (WIN32)
  set(PREPROCESSOR_DEFINITIONS WIN32;_WIN32;_DEBUG;DEBUG;_WINDOWS;_USRDLL;_CRT_SECURE_NO_DEPRECATE;_CRT_NONSTDC_NO_DEPRECATE;STDSHADER_DX9_DLL_EXPORT;FAST_MATERIALVAR_ACCESS;COMPILER_MSVC;COMPILER_MSVC32)
  add_compile_definitions(${PREPROCESSOR_DEFINITIONS})
endif (WIN32)
if (UNIX)
  set(PREPROCESSOR_DEFINITIONS LINUX;_LINUX;POSIX;_POSIX;UNIX;_UNIX;_DEBUG;DEBUG;_USRDLL;_CRT_SECURE_NO_DEPRECATE;_CRT_NONSTDC_NO_DEPRECATE;STDSHADER_DX9_DLL_EXPORT;FAST_MATERIALVAR_ACCESS;COMPILER_GCC)
  add_compile_definitions(${PREPROCESSOR_DEFINITIONS})
endif (UNIX)

# Optional: Set output directory for the library
if (WIN32)
  set_target_properties(game_shader_generic_deferred PROPERTIES OUTPUT_DIRECTORY Release_dx9/game_shader_generic_deferred.dll)
endif (WIN32)
