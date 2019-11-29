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

# Install and setup Qt
RUN pip3 install aqtinstall
RUN aqt install 5.13.2 linux desktop
RUN aqt tool linux tools_qtcreator 4.10.2-0 qt.tools.qtcreator

RUN /Tools/QtCreator/bin/qbs setup-toolchains --detect
RUN /Tools/QtCreator/bin/qbs setup-qt /5.13.2/gcc_64/bin/qmake qt-5-13-2

ENV QBS_COMMAND="/Tools/QtCreator/bin/qbs"
ENV QMAKE_COMMAND="/5.13.2/gcc_64/bin/qmake"

COPY startup.sh .

ARG RESOLUTION="1920x1080x24"
ENV XVFB_RES="${RESOLUTION}"
ARG XARGS=""
ENV XVFB_ARGS="${XARGS}"

ENTRYPOINT ["/bin/bash", "/startup.sh"]
