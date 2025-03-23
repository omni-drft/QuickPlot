cmake_minimum_required(VERSION 3.10)

# Name the overall solution/workspace:
project(QuickPlotSolution)

# We require a 64-bit architecture only.
if(CMAKE_SIZEOF_VOID_P EQUAL 8)
    message(STATUS "Building for 64-bit architecture.")
else()
    message(FATAL_ERROR "64-bit architecture not detected. Only 64-bit is supported.")
endif()

# Set the C++ standard to 17:
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# --- GLFW build options ---
# We typically disable GLFW examples, tests, docs when building it as a dependency.
option(GLFW_BUILD_EXAMPLES "Build the GLFW example programs" OFF)
option(GLFW_BUILD_TESTS    "Build the GLFW test programs"    OFF)
option(GLFW_BUILD_DOCS     "Build the GLFW documentation"    OFF)
# Link GLFW statically:
option(GLFW_BUILD_SHARED_LIBS "Build GLFW as a shared library" OFF)
option(GLFW_INSTALL "Generate installation target" OFF)

# Add GLFW (located at vendor/glfw)
add_subdirectory(vendor/glfw)

# Add our library and test projects:
add_subdirectory(QuickPlot)
add_subdirectory(Tests)
