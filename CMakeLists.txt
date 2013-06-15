cmake_minimum_required(VERSION 2.6)

project(ARTEMIS)
set(ARTEMIS_VERSION 1.0.0)

set(CMAKE_C_COMPILER_INIT g++)

set(ARTEMIS_SRC
    src/BitSize.h
    src/Component.cpp
    src/Component.h
    src/ComponentMapper.h
    src/ComponentType.cpp
    src/ComponentType.h
    src/ComponentTypeManager.cpp
    src/ComponentTypeManager.h
    src/DelayedEntityProcessingSystem.cpp
    src/DelayedEntityProcessingSystem.h
    src/DelayedEntitySystem.cpp
    src/DelayedEntitySystem.h
    src/Entity.cpp
    src/Entity.h
    src/EntityManager.cpp
    src/EntityManager.h
    src/EntityProcessingSystem.cpp
    src/EntityProcessingSystem.h
    src/EntitySystem.cpp
    src/EntitySystem.h
    src/GroupManager.cpp
    src/GroupManager.h
    src/ImmutableBag.h
    src/SystemBitManager.cpp
    src/SystemBitManager.h
    src/SystemManager.cpp
    src/SystemManager.h
    src/TagManager.cpp
    src/TagManager.h
    src/TypeInfoComparator.h
    src/World.cpp
    src/World.h
)

include_directories(
    src
)

add_library(artemis STATIC
    ${ARTEMIS_SRC}
)

add_definitions(-Wall)
add_definitions(-O2)
add_definitions(-lstdc++)

set_target_properties(artemis PROPERTIES
    OUTPUT_NAME "artemis"
    CLEAN_DIRECT_OUTPUT 1
    VERSION ${ARTEMIS_VERSION}
)

source_group(src FILES ${ARTEMIS_SRC})
