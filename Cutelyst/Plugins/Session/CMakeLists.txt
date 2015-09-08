include_directories(
    ${CMAKE_BINARY_DIR}
    ${CMAKE_CURRENT_BINARY_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}
)

set(plugin_session_SRC
    sessionstorefile.cpp
    sessionstorefile_p.h
    session.cpp
    session_p.h
)

set(plugin_session_HEADERS
    sessionstorefile.h
    session.h
    Session
)

add_definitions(
    -std=c++11
)

add_library(cutelyst_qt5_plugin_session SHARED
    ${plugin_session_SRC}
    ${plugin_session_HEADERS}
)
add_library(CutelystQt5::Session ALIAS cutelyst_qt5_plugin_session)
set_property(TARGET cutelyst_qt5_plugin_session PROPERTY EXPORT_NAME Session)

set_target_properties(cutelyst_qt5_plugin_session PROPERTIES
    VERSION ${CUTELYST_VERSION}
    SOVERSION ${CUTELYST_API_LEVEL}
)

target_link_libraries(cutelyst_qt5_plugin_session
    cutelyst-qt5
    Qt5::Core
    Qt5::Network
)

install(TARGETS cutelyst_qt5_plugin_session EXPORT CutelystQt5Targets DESTINATION ${CMAKE_INSTALL_LIBDIR})

install(FILES ${plugin_session_HEADERS}
        DESTINATION include/cutelyst-qt5/Cutelyst/Plugins/Session
        COMPONENT Session
)