#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([xssp], [3.0.1], [Coos.Baakman@radboudumc.nl])
AM_INIT_AUTOMAKE([subdir-objects])
AC_CONFIG_SRCDIR([config.h.in])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIR([m4])

# Checks for programs.
AC_PROG_CXX
AC_PROG_CC
AC_PROG_INSTALL
AC_CHECK_PROGS([PERL], [perl], [yes])
if test -z "$PERL"; then
  AC_MSG_WARN([perl not found - cannot build mkhssp])
fi
AC_CHECK_PROGS([CPPCHECK], [cppcheck], [yes])
if test -z "$CPPCHECK"; then
  AC_MSG_WARN([cppcheck not found - continuing without cppcheck support])
fi

# Checks for libraries.
AX_BOOST_BASE([1.48])
AX_BOOST_DATE_TIME
AX_BOOST_FILESYSTEM
AX_BOOST_IOSTREAMS
AX_BOOST_PROGRAM_OPTIONS
AX_BOOST_REGEX
AX_BOOST_SYSTEM
AX_BOOST_THREAD
AX_BOOST_UNIT_TEST_FRAMEWORK
AM_CONDITIONAL([HAVE_CPPCHECK], [test -n "$CPPCHECK"])
AC_CHECK_LIB([zeep], [main], [ ],
             [AC_MSG_WARN([libzeep not found - cannot build mkhssp])])
AX_CHECK_LIBRARY([LIBBZ2], [bzlib.h], [bz2], [],
                 [AC_MSG_WARN([libbz2 not found - compressed files not supported])])
AX_CHECK_LIBRARY([LIBZ], [zlib.h], [z], [],
                 [AC_MSG_WARN([libz not found - compressed files not supported])])

# Checks for header files.
AC_CHECK_HEADERS([sys/ioctl.h termios.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_CHECK_HEADER_STDBOOL
AC_C_INLINE
AC_TYPE_INT16_T
AC_TYPE_INT32_T
AC_TYPE_INT64_T
AC_TYPE_INT8_T
AC_TYPE_SIZE_T
AC_TYPE_UINT16_T
AC_TYPE_UINT32_T
AC_TYPE_UINT64_T
AC_TYPE_UINT8_T

# Checks for library functions.
AC_FUNC_ERROR_AT_LINE
AC_FUNC_FORK
AC_CHECK_FUNCS([dup2 floor pow socket sqrt strchr strerror])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
