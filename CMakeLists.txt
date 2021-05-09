cmake_minimum_required(VERSION 3.19)

project(jucetest CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(third_party/JUCE)

juce_add_console_app(hellojuce
    PRODUCT_NAME "Hello Juce" # The name of the final executable, which can differ from the target name
    VERSION "1.0.0")

target_sources(hellojuce
    PRIVATE
        src/main.cpp)

target_compile_definitions(hellojuce
    PRIVATE
        JUCE_WEB_BROWSER=0
        JUCE_USE_CURL=0)

target_link_libraries(hellojuce
    PRIVATE
        juce::juce_core
    PUBLIC
        juce::juce_recommended_config_flags
        juce::juce_recommended_warning_flags)
