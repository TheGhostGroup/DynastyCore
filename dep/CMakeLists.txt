#
#  Dynasty Core
#  Dynasty Gaming 2019
#  https://github.com/TheGhostGroup/DynastyCore
#

if( MSVC )
  add_definitions(/W0)
else()
  add_definitions(-w)
endif()

#add_subdirectory(threads)

if(CMAKE_SYSTEM_NAME MATCHES "Linux")
  if(SERVERS AND NOT NOJEM)
    add_subdirectory(jemalloc)
#    add_subdirectory(valgrind)
  endif()
endif()

if(CMAKE_SYSTEM_NAME MATCHES "Windows")
  if(SERVERS)
    add_subdirectory(acelite)
  endif()
  if(TOOLS)
    add_subdirectory(bzip2)
  endif()
  if(SERVERS OR TOOLS)
    add_subdirectory(zlib)
  endif()
endif()

if(SERVERS OR TOOLS)
  add_subdirectory(g3dlite)
  add_subdirectory(recastnavigation)
endif()

if(SERVERS)
  add_subdirectory(gsoap)
endif()

if(TOOLS)
  add_subdirectory(CascLib)
endif()
