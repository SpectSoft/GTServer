project(server LANGUAGES CXX)

file(GLOB INCLUDE_FILES
    *.h
    database/*.h
    database/item/*.h
    events/*.h
    events/text_events/*.h
    player/*.h
    proton/*.h
    proton/utils/*.h
    server/*.h
    utils/*.h)
file(GLOB SOURCE_FILES
    *.cpp
    database/*.cpp
    database/item/*.cpp
    events/*.cpp
    events/text_events/*.cpp
    player/*.cpp
    proton/*.cpp
    proton/utils/*.cpp
    server/*.cpp
    utils/*.cpp)

add_executable(${PROJECT_NAME}
    ${INCLUDE_FILES}
    ${SOURCE_FILES}
)

set_target_properties(${PROJECT_NAME} PROPERTIES
    C_STANDARD 11
    CXX_STANDARD 20
    CXX_STANDARD_REQUIRED ON
)

target_compile_definitions(${PROJECT_NAME} PUBLIC
    NOMINMAX
    WIN32_LEAN_AND_MEAN
)

target_include_directories(${PROJECT_NAME} PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/../vendor/enet/include
    ${CMAKE_CURRENT_SOURCE_DIR}/../vendor/fmt/include
    ${CMAKE_CURRENT_SOURCE_DIR}/../vendor/proton/shared
)

target_link_libraries(${PROJECT_NAME} 
    enet
    fmt
)
