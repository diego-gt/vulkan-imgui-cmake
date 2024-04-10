# dependencies
find_package(glfw3 3.4 REQUIRED)
find_package(Vulkan REQUIRED OPTIONAL_COMPONENTS MoltenVK)

set(IMGUI_SOURCES
    ${PROJECT_SOURCE_DIR}/external/imgui/imgui.cpp
    ${PROJECT_SOURCE_DIR}/external/imgui/imgui_draw.cpp
    ${PROJECT_SOURCE_DIR}/external/imgui/imgui_demo.cpp
    ${PROJECT_SOURCE_DIR}/external/imgui/imgui_widgets.cpp
    ${PROJECT_SOURCE_DIR}/external/imgui/imgui_tables.cpp
    ${PROJECT_SOURCE_DIR}/external/imgui/backends/imgui_impl_glfw.cpp
    ${PROJECT_SOURCE_DIR}/external/imgui/backends/imgui_impl_vulkan.cpp
)

set(IMGUI_HEADERS
    ${PROJECT_SOURCE_DIR}/external/imgui/imgui.h
    ${PROJECT_SOURCE_DIR}/external/imgui/backends/imgui_impl_glfw.h
    ${PROJECT_SOURCE_DIR}/external/imgui/backends/imgui_impl_vulkan.h
)

add_executable(vktest main.cpp ${IMGUI_SOURCES} ${IMGUI_HEADERS})

target_compile_features(vktest PUBLIC cxx_std_23)

target_include_directories(vktest PRIVATE ${PROJECT_SOURCE_DIR}/external/imgui)
target_include_directories(vktest PRIVATE ${PROJECT_SOURCE_DIR}/external/imgui/backends)

set_target_properties(vktest PROPERTIES
    CXX_EXTENSIONS OFF
    LINKER_LANGUAGE CXX
)

target_link_libraries(vktest glfw)
target_link_libraries(vktest Vulkan::Vulkan)

