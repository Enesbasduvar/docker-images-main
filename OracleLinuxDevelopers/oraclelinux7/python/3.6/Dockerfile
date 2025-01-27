# Copyright (c) 2020 Oracle and/or its affiliates.
# Licensed under the Universal Permissive License v 1.0 as shown at https://oss.oracle.com/licenses/upl.
FROM oraclelinux:7-slim

RUN yum -y update && yum clean all

RUN yum -y install oraclelinux-developer-release-el7 && \
    yum -y install python3 python3-libs python3-pip python3-setuptools && \
    yum clean all


CMD ["/bin/python3","--version"]