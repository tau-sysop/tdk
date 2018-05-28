# @(#) $Tau: tdk/docker/grpc/Dockerfile $

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

## gRPC build image

FROM tauproject/core:shimmer
ARG GRPC_RELEASE=master

RUN apt-get install -qq build-essential clang \
		autoconf automake libtool pkg-config libgflags-dev libgtest-dev \
		libc++-dev git curl ca-certificates
		
RUN git clone -b $GRPC_RELEASE https://github.com/grpc/grpc

RUN cd grpc && \
	git submodule update --init --recursive
RUN cd grpc && \
	make clean && \
	make prefix='/opt/grpc' PROTOBUF_CONFIG_OPTS='--prefix=/opt/grpc' && \
	make prefix='/opt/grpc' PROTOBUF_CONFIG_OPTS='--prefix=/opt/grpc' install	
RUN cd grpc/third_party/protobuf && make install

COPY grpc.sh /etc/profile.d/
COPY grpc.conf /etc/ld.so.conf.d/
RUN /sbin/ldconfig
RUN for file in /opt/grpc/bin/* ; do ln -sf $file /usr/local/bin/ ; done
CMD [ "/bin/bash", "--login" ]
