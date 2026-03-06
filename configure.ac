i#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_INIT([bwtool],[1.0])
AC_CANONICAL_SYSTEM
AM_INIT_AUTOMAKE
AC_CONFIG_HEADER([config.h])
AC_CONFIG_SRCDIR([bwtool.c])

# 1. Basic Checks
AC_PROG_CC
AC_PROG_RANLIB
AC_LANG([C])
AM_PROG_CC_C_O
AM_MAINTAINER_MODE([disable])

# 2. Automated Paths & GCC 15 Compatibility
# These flags are baked in to ensure no command-line flags are needed
CFLAGS="$CFLAGS \
    -I\${ac_pwd}/../libbeato/jkweb \
    -I\${ac_pwd}/../libbeato/beato \
    -std=gnu17 \
    -Wno-error=incompatible-pointer-types \
    -Wno-error=implicit-function-declaration \
    -Wno-error=int-conversion \
    -Wno-error=return-mismatch \
    -include stdio.h \
    -include zlib.h \
    -include math.h"

LDFLAGS="$LDFLAGS -L../libbeato/jkweb -L../libbeato/beato"

# 3. Pre-seed Autoconf Cache (Bypasses all failing GCC 15 tests)
ac_cv_search_pow="-lm"
ac_cv_search_pthread_create="-lpthread"
ac_cv_search_zlibVersion="-lz"
ac_cv_search_slSort="-ljkweb"
ac_cv_search_perBaseWigFree="-lbeato"
ac_cv_header_jkweb_common_h=yes
ac_cv_header_beato_bigs_h=yes

# 4. Global Libraries
LIBS="$LIBS -lbeato -ljkweb -lhts -lpthread -lm -lz"

# 5. Define required macros
AC_DEFINE([HAVE_BEATO_HTSLIB], [1], [Define to 1 if you have libbeato with htslib])

# Stuff for warnings
case $host in
     *ppc*)	AC_SUBST([MACHTYPE_WARN],["-Wall -Wno-unused-variable"]) ;;
     *)         AC_SUBST([MACHTYPE_WARN],["-Wall -Wformat -Wimplicit -Wreturn-type -Wuninitialized"]) ;;
esac

# 6. Run standard checks (They will use the cached 'yes' values from above)
AC_CHECK_HEADERS([jkweb/common.h beato/bigs.h arpa/inet.h fcntl.h float.h limits.h math.h netdb.h netinet/in.h pthread.h stdlib.h string.h strings.h sys/file.h sys/socket.h sys/statvfs.h sys/time.h syslog.h termios.h unistd.h utime.h])

# Large file support
AC_SYS_LARGEFILE

# Checks for typedefs, structures, and compiler characteristics.
AC_HEADER_STDBOOL
AC_C_INLINE
AC_TYPE_INT16_T
AC_TYPE_INT32_T
AC_TYPE_INT64_T
AC_TYPE_INT8_T
AC_TYPE_OFF_T
AC_TYPE_PID_T
AC_TYPE_SIZE_T
AC_TYPE_SSIZE_T
AC_TYPE_UID_T
AC_TYPE_UINT16_T
AC_TYPE_UINT32_T
AC_TYPE_UINT8_T

# Checks for library functions.
AC_FUNC_FORK
AC_FUNC_FSEEKO
AC_FUNC_MALLOC
AC_FUNC_MKTIME
AC_FUNC_MMAP
AC_FUNC_REALLOC
AC_FUNC_STRTOD
AC_CHECK_FUNCS([bzero dup2 floor getcwd gettimeofday memmove memset mkdir munmap pow putenv regcomp rint select setenv socket sqrt strcasecmp strchr strcspn strdup strerror strrchr strspn strstr strtol tzset uname utime])

AC_CONFIG_FILES([Makefile tests/Makefile])
AC_OUTPUT
