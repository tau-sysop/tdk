# @(#) $Tau: tdk/configure.ac $

## ------------------------------------------------------------------------- ##
##                          T A U    P R O J E C T                           ##
## ------------------------------------------------------------------------- ##
##                                                                           ##
##  Licensed under the Apache License, Version 2.0 (the "License");          ##
##  you may not use this file except in compliance with the License.         ##
##                                                                           ##
##  You may obtain a copy of the License at:                                 ##
##                                                                           ##
##      http://www.apache.org/licenses/LICENSE-2.0                           ##
##                                                                           ##
##  Unless required by applicable law or agreed to in writing, software      ##
##  distributed under the License is distributed on an "AS-IS" BASIS,        ##
##  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. ##
##  See the License for the specific language governing permissions and      ##
##  limitations under the License.                                           ##
##                                                                           ##
## ------------------------------------------------------------------------- ##

AC_INIT([tdk],[shimmer])
AS_VAR_SET([ORG],[tauproject])
AC_SUBST([ORG])
AS_VAR_SET([RELEASE],[shimmer])
AC_SUBST([RELEASE])
AC_CONFIG_AUX_DIR([scripts])
AC_CONFIG_MACRO_DIR([m4])
AM_INIT_AUTOMAKE([foreign])
AM_MAINTAINER_MODE

AC_CHECK_PROG([DOCKER],[docker],[docker])
AM_CONDITIONAL([WITH_DOCKER],[test x"$DOCKER" != x""])

AC_MSG_CHECKING([which gRPC release to build])
AC_ARG_WITH([grpc_release],[AS_HELP_STRING([--with-grpc-release=TAG],[specify the gRPC release tag or branch to clone within the gRPC build container])],[grpc_release=${withval}])
if test x"$grpc_release" = x"" || test x"$grpc_release" = x"yes" || test x"$grpc_release" = x"no" ; then
	grpc_release=master
fi
AC_SUBST([grpc_release])
AC_MSG_RESULT([$grpc_release])

AC_CONFIG_FILES([
Makefile
docker/Makefile
docker/core/Makefile
docker/grpc/Makefile
docker/tdk/Makefile
])
	
AC_OUTPUT
