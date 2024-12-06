cmake_minimum_required (VERSION 3.0)

project (kdetoys)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_BUILD_WITH_INSTALL_RPATH ON)

find_package(KDE1 REQUIRED)
#find_package(uulib REQUIRED)

add_definitions(-DHAVE_CONFIG_H)

include_directories(common)

include(CMakePackageConfigHelpers)
include(Qt1Macros)
include(KDE1Macros)
include(KDE1InstallDirs)

if (CMAKE_COMPILER_IS_GNUCXX)
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-write-strings")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fpermissive -std=c++98")
    set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} -Wl,--no-undefined")
endif()

if (CMAKE_SYSTEM_NAME MATCHES "NetBSD")
    set(CMAKE_C_FLAGS  "${CMAKE_C_FLAGS} -I/usr/X11R7/include -I/usr/pkg/include -I/usr/local/include -I/usr/kde1/include -L/usr/X11R7/lib -L/usr/pkg/lib -L/usr/local/lib -L/usr/kde1/lib -Wl,-R/usr/X11R7/lib -Wl,-R/usr/pkg/lib -Wl,-R/usr/local/lib -Wl,-R/usr/kde1/lib")
    set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -I/usr/X11R7/include -I/usr/pkg/include -I/usr/local/include -I/usr/kde1/include -L/usr/X11R7/lib -L/usr/pkg/lib -L/usr/local/lib -L/usr/kde1/lib -Wl,-R/usr/X11R7/lib -Wl,-R/usr/pkg/lib -Wl,-R/usr/local/lib -Wl,-R/usr/kde1/lib")
    set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} -L/usr/X11R7/lib -L/usr/pkg/lib -L/usr/local/lib -L/usr/kde1/lib -R/usr/X11R7/lib -R/usr/pkg/lib -R/usr/local/lib -R/usr/kde1/lib")
elseif (CMAKE_SYSTEM_NAME MATCHES "FreeBSD")
    set(CMAKE_C_FLAGS  "${CMAKE_C_FLAGS} -I/usr/local/include -I/usr/kde1/include")
    set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -I/usr/local/include -I/usr/kde1/include")
    set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} -L/usr/local/lib -L/usr/kde1/lib -R/usr/local/lib -R/usr/kde1/lib")
elseif (CMAKE_SYSTEM_NAME MATCHES "OpenBSD")
    set(CMAKE_C_FLAGS  "${CMAKE_C_FLAGS} -I/usr/local/include -I/usr/kde1/include -I/usr/X11R6/include")
    set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -I/usr/local/include -I/usr/kde1/include -I/usr/X11R6/include")
    set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} -L/usr/local/lib -L/usr/kde1/lib -L/usr/X11R6/lib -R/usr/local/lib -R/usr/kde1/lib -R/usr/X11R6/lib")
endif()

add_subdirectory(kmoon)
add_subdirectory(kworldwatch)
add_subdirectory(mouse)
add_subdirectory(po)
