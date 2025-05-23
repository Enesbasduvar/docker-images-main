# Copyright (c) 2019, 2023 Oracle and/or its affiliates.
#
# Licensed under the Universal Permissive License v 1.0 as shown at https://oss.oracle.com/licenses/upl.
#
# ORACLE DOCKERFILES PROJECT
# --------------------------
# This is the Dockerfile for Oracle JDK 11 on Oracle Linux 7
#
# REQUIRED FILES TO BUILD THIS IMAGE
# ----------------------------------
#
# (1) jdk-11.XX_linux-x64_bin.tar.gz or jdk-11.XX_linux-aarch64_bin.tar.gz
#     Download from https://www.oracle.com/java/technologies/downloads/
#
# HOW TO BUILD THIS IMAGE
# -----------------------
# Put all downloaded files in the same directory as this Dockerfile
# Run:
#      $ docker build -t oracle/jdk:11 .
#
# This command is already scripted in build.sh so you can alternatively run
#		$ bash build.sh
#
# The builder image will be used to uncompress the tar.gz file with the Java Runtime.

FROM oraclelinux:7-slim as builder

LABEL maintainer="Aurelio Garcia-Ribeyro <enes.basduvar@mail.com>"

RUN yum install -y gzip tar
		
	
# Default to UTF-8 file.encoding
ENV LANG en_US.UTF-8


# Environment variables for the builder image.
# Required to validate that you are using the correct file

ENV JAVA_HOME=/usr/java/jdk-11

##
COPY *.tar.gz /tmp/
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
RUN set -eux; \
	ARCH="$(uname -m)" && \
    if [ "$ARCH" = "x86_64" ]; \
    then \
		mv "$(ls /tmp/jdk-11*_linux-x64_bin.tar.gz)" /tmp/jdk.tar.gz ; \
        JAVA_SHA256=e73531c1b09cb6e618d4d3617f622acfb05bd9afea2f1539aa4cf452a24eb3bc ; \
    else \
	    mv "$(ls /tmp/jdk-11*_linux-aarch64_bin.tar.gz)" /tmp/jdk.tar.gz ; \
    	JAVA_SHA256=34c22df9bb58a97f92e4fffdd6961e56b9b4387a5055f8f4a98b361168e881cc ; \    	
    fi && \
	echo "$JAVA_SHA256 */tmp/jdk.tar.gz" | sha256sum -c -; \
	mkdir -p "$JAVA_HOME"; \
	tar --extract --file /tmp/jdk.tar.gz --directory "$JAVA_HOME" --strip-components 1
	
## Get a fresh version of SLIM for the final image	
FROM oraclelinux:7-slim

# Default to UTF-8 file.encoding
ENV LANG en_US.UTF-8

ENV JAVA_HOME=/usr/java/jdk-11

ENV	PATH $JAVA_HOME/bin:$PATH	

# Copy the uncompressed Java Runtime from the builder image
COPY --from=builder $JAVA_HOME $JAVA_HOME

RUN set -eux; \
# Update the base image
	yum -y update; \
	yum install -y \
# JDK assumes freetype is available		
		freetype fontconfig \
	; \
	rm -rf /var/cache/yum; \
	ln -sfT "$JAVA_HOME" /usr/java/default; \
	ln -sfT "$JAVA_HOME" /usr/java/latest; \
	for bin in "$JAVA_HOME/bin/"*; do \
		base="$(basename "$bin")"; \
		[ ! -e "/usr/bin/$base" ]; \
		alternatives --install "/usr/bin/$base" "$base" "$bin" 20000; \
	done; \
# -Xshare:dump will create a CDS archive to improve startup in subsequent runs	
	java -Xshare:dump; 

CMD ["jshell"]
