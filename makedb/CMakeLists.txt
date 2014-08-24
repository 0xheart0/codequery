cmake_minimum_required(VERSION 2.8)
project(CodeQueryDBMaker)

#add_definitions( -Wall )

find_package( Qt4 REQUIRED )
find_package(Sqlite REQUIRED)

set( QT_DONT_USE_QTGUI TRUE )
set( QT_USE_QTXML FALSE )

INCLUDE( "${QT_USE_FILE}" )

include_directories( "." )
include_directories( "../querylib" )
include_directories( "${SQLITE_INCLUDE_DIR}" )
include_directories( "/usr/local/include" )

set( CQMAKEDB_SRCS
     sqlbase.cpp
     csdbheader.cpp
     csdbparser.cpp
     cs2sq.cpp
     ctagread.cpp
     main.cpp
   )

add_executable( cqmakedb ${CQMAKEDB_SRCS} )
target_link_libraries( cqmakedb ${QT_LIBRARIES} ${SQLITE_LIBRARIES} small_lib optlist_lib)

install(TARGETS cqmakedb RUNTIME DESTINATION bin)


