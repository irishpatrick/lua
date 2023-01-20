cmake_minimum_required(VERSION 3.20)

project(lua)

set(lua_sources
        lapi.h
        lauxlib.h
        lcode.h
        lctype.h
        ldebug.h
        ldo.h
        ljumptab.h
        llex.h
        llimits.h
        lmem.h
        lobject.h
        lopcodes.h
        lopnames.h
        lparser.h
        lprefix.h
        lstate.h
        lstring.h
        ltable.h
        ltests.h
        ltm.h
        lua.h
        luaconf.h
        lualib.h
        lundump.h
        lvm.h
        lzio.h

        lapi.c
        lauxlib.c
        lbaselib.c
        lcode.c
        lcorolib.c
        lctype.c
        ldblib.c
        ldebug.c
        ldo.c
        ldump.c
        lfunc.c
        lgc.c
        linit.c
        liolib.c
        llex.c
        lmathlib.c
        lmem.c
        loadlib.c
        lobject.c
        lopcodes.c
        loslib.c
        lparser.c
        lstate.c
        lstring.c
        lstrlib.c
        ltable.c
        ltablib.c
        ltests.c
        ltm.c
        lua.c
        lundump.c
        lutf8lib.c
        lvm.c
        lzio.c
        )

if (UNIX)
    set(lua_flags
            -Wfatal-errors
            -Wextra
            -Wshadow
            -Wsign-compare
            -Wundef
            -Wwrite-strings
            -Wredundant-decls
            -Wdisabled-optimization
            -Wdouble-promotion
            -Wmissing-declarations

            -std=c99
            -DLUA_USE_LINUX
            -DLUA_USE_READLINE
            )

    set(lua_linkflags
            -Wl -E
            )

    set(lua_libs
            m
            dl
            readline
            )

elseif (MSVC)
    set(flags
            /W3
            /WX
            /Md
            )
endif ()

add_library(${PROJECT_NAME} STATIC ${lua_sources})
target_compile_options(${PROJECT_NAME} PRIVATE ${lua_flags})
target_link_libraries(${PROJECT_NAME} PRIVATE ${lua_libs})
target_link_options(${PROJECT_NAME} PRIVATE ${lua_linkflags})

