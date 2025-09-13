include(${CMAKE_CURRENT_SOURCE_DIR}/../../max-sdk-base/script/max-pretarget.cmake)

#############################################################
# MAX EXTERNAL
#############################################################

include_directories( 
	"${MAX_SDK_INCLUDES}"
	"${MAX_SDK_MSP_INCLUDES}"
	"${MAX_SDK_JIT_INCLUDES}"

    # Add any additional includes here
    # "${CMAKE_CURRENT_SOURCE_DIR}/../../include"  # e.g. if you put your includes in /source/include
)

set(PROJECT_SRC
    # Add any files you need to compile
    until.c
    ../../include/pdx.cpp
)

add_library( 
	${PROJECT_NAME} 
	MODULE
	${PROJECT_SRC}
)

add_compile_definitions(OBJECT_SETUP_CALL=until_setup)

set_source_files_properties(${PROJECT_SRC} PROPERTIES LANGUAGE CXX)

include(${CMAKE_CURRENT_SOURCE_DIR}/../../max-sdk-base/script/max-posttarget.cmake)

target_include_directories(pd.until
   PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/../../include
)
