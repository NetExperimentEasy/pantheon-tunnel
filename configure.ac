#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.68])
AC_INIT([pantheon-tunnel], [0.9], [snr@cs.stanford.edu])
AM_INIT_AUTOMAKE([foreign])
AC_CONFIG_SRCDIR([src/frontend/tunnelservershell.cc])
AC_CONFIG_HEADERS([config.h])

# Add picky CXXFLAGS
CXX11_FLAGS="-std=c++11 -pthread"
# https://blog.csdn.net/llm_hao/article/details/124279032
PICKY_CXXFLAGS="-pedantic -Wall -Wextra -Weffc++ -Werror -Wno-error=stringop-truncation"
AC_SUBST([CXX11_FLAGS])
AC_SUBST([PICKY_CXXFLAGS])

# Checks for programs.
AC_PROG_CXX
AC_PROG_RANLIB

AC_ARG_VAR([IPTABLES], [path to iptables])
AC_PATH_PROG([IPTABLES], [iptables], [no], [$PATH$PATH_SEPARATOR/sbin$PATH_SEPARATOR/usr/sbin$PATH_SEPARATOR/bin$PATH_SEPARATOR/usr/bin])
if test "$IPTABLES" = "no"; then
  AC_MSG_ERROR([iptables is required])
fi
AC_DEFINE_UNQUOTED([IPTABLES], ["$IPTABLES"], [path to iptables])

AC_ARG_VAR([IP], [path to ip])
AC_PATH_PROG([IP], [ip], [no], [$PATH$PATH_SEPARATOR/sbin$PATH_SEPARATOR/usr/sbin$PATH_SEPARATOR/bin$PATH_SEPARATOR/usr/bin])
if test "$IP" = "no"; then
  AC_MSG_ERROR([ip is required])
fi
AC_DEFINE_UNQUOTED([IP], ["$IP"], [path to ip])

AC_ARG_VAR([DNSMASQ], [path to dnsmasq])
AC_PATH_PROG([DNSMASQ], [dnsmasq], [no], [$PATH$PATH_SEPARATOR/sbin$PATH_SEPARATOR/usr/sbin$PATH_SEPARATOR/bin$PATH_SEPARATOR/usr/bin])
if test "$DNSMASQ" = "no"; then
  AC_MSG_ERROR([dnsmasq is required])
fi
AC_DEFINE_UNQUOTED([DNSMASQ], ["$DNSMASQ"], [path to dnsmasq])

# Checks for libraries.

# Checks for header files.

# Checks for typedefs, structures, and compiler characteristics.

# Checks for library functions.

AC_CONFIG_FILES([Makefile
		 src/Makefile
		 src/util/Makefile
		 src/packet/Makefile
		 src/frontend/Makefile])
AC_OUTPUT
