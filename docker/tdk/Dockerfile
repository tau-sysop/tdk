# @(#) $Tau: tdk/docker/tdk/Dockerfile $

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

FROM tauproject/core:shimmer

## Include gRPC in the image

COPY --from=tauproject/tdk-build:grpc /opt/grpc /opt/grpc
COPY --from=tauproject/tdk-build:grpc /etc/profile.d/grpc.sh /etc/profile.d
COPY --from=tauproject/tdk-build:grpc /etc/ld.so.conf.d/grpc.conf /etc/ld.so.conf.d
RUN for file in /opt/grpc/bin/* ; do ln -sf $file /usr/local/bin/ ; done

## Standard packages

RUN apt-get update -qq -y && \
	apt-get install -qq -y build-essential clang libtool autoconf automake \
		pkg-config curl netcat-openbsd

## Post-installation

RUN /sbin/ldconfig
