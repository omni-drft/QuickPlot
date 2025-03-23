cmake_minimum_required(VERSION 3.10)
project(QuickPlotLibrary)

# Create a static library called QuickPlot
add_library(QuickPlot STATIC
    src/quickplot.cc
    # You can list additional .cpp files here
)

# Tell CMake where to find the public headers for QuickPlot
target_include_directories(QuickPlot
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/include
)

# We need OpenGL:
find_package(OpenGL REQUIRED)

# Link dependencies: GLFW and OpenGL
# If GLFW is named "glfw3" in your setup, replace "glfw" with "glfw3".
target_link_libraries(QuickPlot
    PUBLIC
        glfw
        OpenGL::GL
)

# Platform-specific libraries:
if (WIN32)
    # Windows needs opengl32 explicitly
    target_link_libraries(QuickPlot PUBLIC opengl32)
elseif(UNIX AND NOT APPLE)
    # On Linux we typically need dl and pthread for GLFW
    target_link_libraries(QuickPlot PUBLIC dl pthread)
endif()
