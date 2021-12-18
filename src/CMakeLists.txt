# 4. Include/Link everything
set(PLUGIN_NAME URIResolver)

link_directories(${USD_LIBRARY_DIR})


set(
        SRC
                resolver.cpp
)

add_library(${PLUGIN_NAME}
    SHARED
                ${SRC}
)

find_package(PythonLibs REQUIRED)

target_link_libraries(${PLUGIN_NAME}
    PUBLIC
                "C:/Program Files/Side Effects Software/Houdini 18.5.596/custom/houdini/dsolib/hboost_python27-mt-x64.lib"
                "C:/Program Files/Side Effects Software/Houdini 18.5.596/custom/houdini/dsolib/libpxr_ar.lib"
                "C:/Program Files/Side Effects Software/Houdini 18.5.596/python27/libs/python27.lib"
)

target_include_directories(
        ${PLUGIN_NAME}
                SYSTEM
                        PRIVATE
                                ${USD_INCLUDE_DIR}

                        PUBLIC
                                ${PYTHON_INCLUDE_PATH}
)

install(
    TARGETS
        ${PLUGIN_NAME}
        DESTINATION
                .
)

install(
    FILES
                plugInfo.json
    DESTINATION
        ./resources
)
