AC_INIT([libnp1sec], [0.0.0])

AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_HEADERS([config.h])

AM_INIT_AUTOMAKE([-Wall -Werror foreign subdir-objects])

AM_PROG_AR
LT_INIT

AC_PROG_CXX
AC_LANG([C++])

CXXFLAGS+=" -std=c++11 -Wall -Wextra -Werror" #-Wno-error"

GTEST_BASE=contrib/gtest
GTEST_INCLUDE=${GTEST_BASE}/include
AC_SUBST(GTEST_BASE)
AC_SUBST(GTEST_INCLUDE)

PKG_CHECK_MODULES([GLIB], [glib-2.0], [
	AC_SUBST(GLIB_CFLAGS)
	AC_SUBST(GLIB_LIBS)
], [
	AC_MSG_RESULT(no)
	AC_MSG_ERROR([No glib])
])

PKG_CHECK_MODULES([PURPLE], [purple], [
	AC_DEFINE([HAVE_PURPLE], [1], [Define if we have found libpurple.])
	AC_SUBST(PURPLE_CFLAGS)
	AC_SUBST(PURPLE_LIBS)
], [
	AC_MSG_RESULT(no)
	AC_MSG_ERROR([No libpurple])
])

PKG_CHECK_MODULES([LIBEVENT], [libevent], [
	AC_DEFINE([HAVE_LIBEVENT], [1], [Define if we have found libevent.])
	AC_SUBST(LIBEVENT_CFLAGS)
	AC_SUBST(LIBEVENT_LIBS)
], [
	AC_MSG_RESULT(no)
	AC_MSG_ERROR([No libevent])
])

AM_PATH_LIBGCRYPT([], [
	AC_SUBST(LIBGCRYPT_CFLAGS)
	AC_SUBST(LIBGCRYPT_LIBS)
], [
	AC_MSG_RESULT(no)
	AC_MSG_ERROR([No libgcrypt])
])

AC_CHECK_LIB([pthread], [pthread_create], [
	PTHREAD="-lpthread"
	AC_SUBST(PTHREAD)
], [])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
