# Copyright (C) 2007-2009 LuaDist.
# Created by Peter Kapec
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

PROJECT(lua_iconv C)
CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
INCLUDE(dist.cmake)

# Build
IFIND_PATH(ICONV_INCLUDE_DIR NAMES iconv.h)
FIND_LIBRARY(ICONV_LIBRARY NAMES iconv)

INCLUDE(FindPackageHandleStandardArgs)
FIND_PACKAGE_HANDLE_STANDARD_ARGS(ICONV DEFAULT_MSG ICONV_LIBRARY ICONV_INCLUDE_DIR)

INCLUDE_DIRECTORIES(ICONV_INCLUDE_DIR)
SET(LIBS ${ICONV_LIBRARY})

ADD_LUA_MODULE(iconv luaiconv.c)
TARGET_LINK_LIBRARIES(iconv ${LIBS})

# Install all files and documentation
INSTALL (TARGETS iconv DESTINATION ${INSTALL_CMOD})
INSTALL (FILES COPYING README DESTINATION ${INSTALL_DATA})
INSTALL (FILES test_iconv.lua DESTINATION ${INSTALL_TEST})
