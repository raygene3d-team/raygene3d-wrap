set(NAME raygene3d)

set(ROOT_DIR ${CMAKE_SOURCE_DIR}/${NAME}-wrap/wrap)
set(ROOT_SOURCE
	${ROOT_DIR}/broker.h
	${ROOT_DIR}/broker.cpp
)

set(SOURCE base.h base.cpp wrap.h wrap.cpp
	${ROOT_SOURCE}
)

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${SOURCE})

add_library(${NAME}-wrap STATIC ${SOURCE})
	
target_include_directories(${NAME}-wrap PUBLIC
	${CMAKE_SOURCE_DIR}/3rdparty
)

IF(WIN32)

ELSE(WIN32)
target_link_libraries(${NAME}-wrap PRIVATE
	optimized -ldl
	optimized -lpthread
)
ENDIF(WIN32)
