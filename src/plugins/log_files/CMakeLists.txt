add_library(mavsdk_log_files
    log_files.cpp
    log_files_impl.cpp
)

target_link_libraries(mavsdk_log_files
    mavsdk
)

set_target_properties(mavsdk_log_files
    PROPERTIES COMPILE_FLAGS ${warnings}
)

target_include_directories(mavsdk_log_files PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include/mavsdk>
    )

install(TARGETS mavsdk_log_files
    EXPORT mavsdk-targets
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    )

install(FILES
    include/plugins/log_files/log_files.h
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/mavsdk/plugins/log_files
)
