add_library(mavsdk_tune
    tune.cpp
    tune_impl.cpp
)

target_link_libraries(mavsdk_tune
    mavsdk
)

set_target_properties(mavsdk_tune
    PROPERTIES COMPILE_FLAGS ${warnings}
)

target_include_directories(mavsdk_tune PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include/mavsdk>
    )

install(TARGETS mavsdk_tune
    EXPORT mavsdk-targets
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    )

install(FILES
    include/plugins/tune/tune.h
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/mavsdk/plugins/tune
)
