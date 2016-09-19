PROJECT(sqlite3)
cmake_minimum_required(VERSION 2.8)

add_library(sqlite3 STATIC sqlite3.c sqlite3.h sqlite3ext.h)
add_executable(sqlite sqlite3.c shell.c sqlite3.h sqlite3ext.h)
set_target_properties(sqlite PROPERTIES OUTPUT_NAME sqlite3)

if (UNIX)
	target_link_libraries(sqlite dl pthread m)
endif (UNIX)

add_definitions(-DSQLITE_ENABLE_RTREE)
add_definitions(-DSQLITE_ENABLE_FTS4)
add_definitions(-DSQLITE_ENABLE_FTS5)
add_definitions(-DSQLITE_ENABLE_JSON1)
