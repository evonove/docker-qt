FROM ubuntu:19.10

# Install sudo
RUN apt-get update -y \
 && apt-get install -y --no-install-recommends \
        build-essential \
        libglvnd-dev \
        mesa-common-dev \
        p7zip \
        python3-pip \
        python3-setuptools \
        qbs \
        xvfb \
        cmake \
 && rm -rf /var/lib/apt/lists/*

# Setup Variables
ENV QT_VERSION="5.14.0"
ENV QBS_PROFILE="qt-5-14-0"
ENV QT_CREATOR_VERSION="4.11.0-0"

# Install and setup Qt
RUN pip3 install aqtinstall
RUN aqt install ${QT_VERSION} linux desktop
RUN aqt tool linux tools_qtcreator ${QT_CREATOR_VERSION} qt.tools.qtcreator

RUN /Tools/QtCreator/bin/qbs setup-toolchains --detect
RUN /Tools/QtCreator/bin/qbs setup-qt /${QT_VERSION}/gcc_64/bin/qmake ${QBS_PROFILE}

ENV QBS_COMMAND="/Tools/QtCreator/bin/qbs"
ENV QMAKE_COMMAND="/${QT_VERSION}/gcc_64/bin/qmake"

ARG RESOLUTION="1920x1080x24"
ENV XVFB_RES="${RESOLUTION}"
ARG XARGS=""
ENV XVFB_ARGS="${XARGS}"

COPY docker-entrypoint.sh /usr/local/bin/
ENTRYPOINT ["docker-entrypoint.sh"]
