add_executable(trace_cpp main.cpp)
target_link_libraries(trace_cpp PRIVATE minilogger)
target_compile_options(trace_cpp PRIVATE -g -ggdb -gdwarf)
if (NOT APPLE)
    target_compile_options(trace_cpp PRIVATE -rdynamic -funwind-tables)
else()
    target_compile_options(trace_cpp PRIVATE -Wl,-export_dynamic)
    target_compile_options(trace_cpp PRIVATE -funwind-tables)
endif()

add_executable(trace_c main.c)
target_link_libraries(trace_c PRIVATE minilogger)
target_compile_options(trace_c PRIVATE -g -ggdb -gdwarf)
if (NOT APPLE)
    target_compile_options(trace_cpp PRIVATE -rdynamic -funwind-tables)
else()
    target_compile_options(trace_cpp PRIVATE -Wl,-export_dynamic)
    target_compile_options(trace_cpp PRIVATE -funwind-tables)
endif()

