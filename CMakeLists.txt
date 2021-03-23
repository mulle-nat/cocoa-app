cmake_minimum_required(VERSION 2.8.8)
project(foo)

set(CMAKE_OSX_ARCHITECTURES "arm64;x86_64")

add_executable(
    foo
    MACOSX_BUNDLE
    AppDelegate.h
    AppDelegate.m
    main.m
    MainMenu.nib
)

set_source_files_properties(
    MainMenu.nib
    PROPERTIES
    MACOSX_PACKAGE_LOCATION Resources
)


add_custom_command( OUTPUT MainMenu.nib
    DEPENDS MainMenu.xib
    COMMAND ibtool --errors --warnings --notices --output-format human-readable-text
        --compile MainMenu.nib ${CMAKE_CURRENT_SOURCE_DIR}/MainMenu.xib
)



set_target_properties(
    foo
    PROPERTIES
    MACOSX_BUNDLE_GUI_IDENTIFIER "com.whoever.fo"    
    MACOSX_BUNDLE_INFO_PLIST ${CMAKE_CURRENT_SOURCE_DIR}/plist.in
)

set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -framework AppKit")

