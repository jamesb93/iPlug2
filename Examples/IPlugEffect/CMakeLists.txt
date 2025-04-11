cmake_minimum_required(VERSION 3.11 FATAL_ERROR)
cmake_policy(SET CMP0091 NEW)

project(IPlugEffect VERSION 1.0.0 LANGUAGES C CXX)


# Set project directories and source files
set(SRC_FILES
  "config.h"
  "IPlugEffect.h"
  "IPlugEffect.cpp"
)
source_group(TREE "${CMAKE_CURRENT_SOURCE_DIR}" FILES ${SRC_FILES})

iplug_add_app(IPlugEffect
    SOURCES ${SRC_FILES}
    RESOURCES resources/fonts/Roboto-Regular.ttf
)

iplug_add_vst3(IPlugEffect
    SOURCES ${SRC_FILES}
    RESOURCES resources/fonts/Roboto-Regular.ttf
)

set(AUv2_SRC_FILES
  "../../IPlug/AUv2/IPlugAU_view_factory.mm"
)

iplug_add_auv2(IPlugEffect
    SOURCES ${SRC_FILES} ${AUv2_SRC_FILES}
    RESOURCES resources/fonts/Roboto-Regular.ttf
)

set_target_properties(IPlugEffectApp PROPERTIES
    OUTPUT_NAME_DEBUG "IPlugEffect"
    OUTPUT_NAME_RELEASE "IPlugEffect"
)

set_target_properties(IPlugEffectVST3 PROPERTIES
    OUTPUT_NAME_DEBUG "IPlugEffect"
    OUTPUT_NAME_RELEASE "IPlugEffect"
)

set_target_properties(IPlugEffectAUv2 PROPERTIES
    OUTPUT_NAME_DEBUG "IPlugEffect"
    OUTPUT_NAME_RELEASE "IPlugEffect"
)
