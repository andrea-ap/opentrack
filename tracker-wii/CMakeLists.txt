if(WIN32)
    include(opentrack-opencv)
    find_package(OpenCV QUIET)
    if(OpenCV_FOUND)
        add_subdirectory(wiiyourself)
        otr_module(tracker-wii)
        target_link_libraries(${self} opentrack-tracker-pt-base opentrack-wiiyourself bthprops)
        if(MINGW32)
            target_link_libraries(${self} hid)
        endif()
        target_include_directories(${self} PRIVATE "${CMAKE_SOURCE_DIR}/tracker-pt")
    endif()
endif()
