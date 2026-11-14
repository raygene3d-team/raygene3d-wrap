set(NAME raygene3d)

set(ROOT_DIR ${CMAKE_CURRENT_SOURCE_DIR}/wrap)
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
  ${CMAKE_CURRENT_SOURCE_DIR}/../3rdparty
)

if(UNIX)
  find_package(Threads REQUIRED)
  target_link_libraries(${NAME}-wrap PUBLIC
    Threads::Threads
    ${CMAKE_DL_LIBS}
  )
endif()
