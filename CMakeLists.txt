cmake_minimum_required(VERSION 2.8)

project(artemis)
set(ARTEMIS_VERSION 1.0.0)
set(ARTEMIS_BUILD_DIR ${PROJECT_SOURCE_DIR}/build)

set(CMAKE_C_COMPILER_INIT g++)

set(ARTEMIS_SRC
    ${PROJECT_SOURCE_DIR}/src/BitSize.h
    ${PROJECT_SOURCE_DIR}/src/Component.cpp
    ${PROJECT_SOURCE_DIR}/src/Component.h
    ${PROJECT_SOURCE_DIR}/src/ComponentMapper.h
    ${PROJECT_SOURCE_DIR}/src/ComponentType.cpp
    ${PROJECT_SOURCE_DIR}/src/ComponentType.h
    ${PROJECT_SOURCE_DIR}/src/ComponentTypeManager.cpp
    ${PROJECT_SOURCE_DIR}/src/ComponentTypeManager.h
    ${PROJECT_SOURCE_DIR}/src/DelayedEntityProcessingSystem.cpp
    ${PROJECT_SOURCE_DIR}/src/DelayedEntityProcessingSystem.h
    ${PROJECT_SOURCE_DIR}/src/DelayedEntitySystem.cpp
    ${PROJECT_SOURCE_DIR}/src/DelayedEntitySystem.h
    ${PROJECT_SOURCE_DIR}/src/Entity.cpp
    ${PROJECT_SOURCE_DIR}/src/Entity.h
    ${PROJECT_SOURCE_DIR}/src/EntityManager.cpp
    ${PROJECT_SOURCE_DIR}/src/EntityManager.h
    ${PROJECT_SOURCE_DIR}/src/EntityProcessingSystem.cpp
    ${PROJECT_SOURCE_DIR}/src/EntityProcessingSystem.h
    ${PROJECT_SOURCE_DIR}/src/EntitySystem.cpp
    ${PROJECT_SOURCE_DIR}/src/EntitySystem.h
    ${PROJECT_SOURCE_DIR}/src/GroupManager.cpp
    ${PROJECT_SOURCE_DIR}/src/GroupManager.h
    ${PROJECT_SOURCE_DIR}/src/ImmutableBag.h
    ${PROJECT_SOURCE_DIR}/src/SystemBitManager.cpp
    ${PROJECT_SOURCE_DIR}/src/SystemBitManager.h
    ${PROJECT_SOURCE_DIR}/src/SystemManager.cpp
    ${PROJECT_SOURCE_DIR}/src/SystemManager.h
    ${PROJECT_SOURCE_DIR}/src/TagManager.cpp
    ${PROJECT_SOURCE_DIR}/src/TagManager.h
    ${PROJECT_SOURCE_DIR}/src/TypeInfoComparator.h
    ${PROJECT_SOURCE_DIR}/src/World.cpp
    ${PROJECT_SOURCE_DIR}/src/World.h
)

include_directories(
    ${PROJECT_SOURCE_DIR}/src
)

file(MAKE_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)
file(MAKE_DIRECTORY ${PROJECT_SOURCE_DIR}/include)

add_library(artemis STATIC
    ${ARTEMIS_SRC}
)

add_definitions(-Wall -Wextra)
add_definitions(-O2)
add_definitions(-lstdc++)

source_group(src FILES ${ARTEMIS_SRC})

INSTALL(TARGETS artemis 
    ARCHIVE DESTINATION ${PROJECT_SOURCE_DIR}/bin
)

INSTALL(DIRECTORY ${PROJECT_SOURCE_DIR}/src/
    DESTINATION ${PROJECT_SOURCE_DIR}/include
    FILES_MATCHING PATTERN "*.h"
)
