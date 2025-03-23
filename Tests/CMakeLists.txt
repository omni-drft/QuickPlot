cmake_minimum_required(VERSION 3.10)
project(QuickPlotTest)

# Create an executable for testing
add_executable(QuickPlotTest
    src/main.cc
    # Add other test files if needed
)

# Link our QuickPlot library into this test application
target_link_libraries(QuickPlotTest PRIVATE QuickPlot)

# Include QuickPlot headers in this test project
target_include_directories(QuickPlotTest
    PRIVATE
        ${CMAKE_CURRENT_LIST_DIR}/../QuickPlot/include
)
