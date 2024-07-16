project(game_shader_generic_deferred)

# source files
set(SOURCE_FILES
  BaseVSShader.cpp
  blur.cpp
  debug_lightingctrl.cpp
  debug_radiosity_grid.cpp
  debug_shadow.cpp
  deferred_brush.cpp
  deferred_decalModulate.cpp
  deferred_model.cpp
  deferred_utility.cpp
  defpass_composite.cpp
  defpass_gbuffer.cpp
  defpass_shadow.cpp
  IDeferredExt.cpp
  lighting_global.cpp
  lighting_pass_basic.cpp
  lighting_pass_volum.cpp
  lighting_world.cpp
  lighting_volume.cpp
  pbr_dx9.cpp
  radiosity_blend.cpp
  radiosity_global.cpp
  radiosity_propagate.cpp
  screenspace_combine.cpp
  screenspace_shading.cpp
  volume_blend.cpp
  volume_prepass.cpp
)

# header files
set(HEADER_FILES
  BaseVSShader.h
  commandbuilder.h
  common_deferred_fxc.h
  common_fxc.h
  common_hlsl_cpp_consts.h
  common_lighting_fxc.h
  common_pragmas.h
  common_ps_fxc.h
  common_shadowmapping_fxc.h
  common_vertexlitgeneric_dx9.h
  common_vs_fxc.h
  cpp_shader_constant_register_map.h
  deferred_context.h
  deferred_global_common.h
  deferred_includes.h
  deferred_utility.h
  defpass_composite.h
  defpass_gbuffer.h
  defpass_shadow.h
  IDeferredExt.h
  lighting_helper.h
  lighting_pass_basic.h
  lighting_pass_volum.h
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
set(PREPROCESSOR_DEFINITIONS WIN32;_WIN32;_DEBUG;DEBUG;_WINDOWS;_USRDLL;_CRT_SECURE_NO_DEPRECATE;_CRT_NONSTDC_NO_DEPRECATE;STDSHADER_DX9_DLL_EXPORT;FAST_MATERIALVAR_ACCESS;COMPILER_MSVC;COMPILER_MSVC32)
add_compile_definitions(${PREPROCESSOR_DEFINITIONS})

# Optional: Set output directory for the library
set_target_properties(game_shader_generic_deferred PROPERTIES OUTPUT_DIRECTORY Release_dx9/game_shader_generic_deferred.dll)
