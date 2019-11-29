## Docker Image for Qt Builds

Base image that comes with Qt and Xvfb preinstalled.

## Build tools

The following build tools are provided:

`cmake` `qbs` `qmake`

`cmake` is installed through apt and is available on the path.
`qbs` and `qmake` are installed through `aqt` and we provide two
environment vaiable so that they can be used in the scripts
that build your software.

### QBS_COMMAND

Set to `/Tools/QtCreator/bin/qbs`

### QMAKE_COMMAND

Set to `/<qt_version>/<arch>/bin/qmake`

