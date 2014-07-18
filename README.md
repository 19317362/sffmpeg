`sffmpeg` is a simple cmake-based full-featured FFmpeg static build helper.

It currently works on Linux, OpenBSD, FreeBSD, and MacOSX. It has been tested the most heavily on Linux/x86_64 (Ubuntu 14.04).
The helper will grab the latest versions of most FFmpeg dependencies, providing a way to effectively build, test and compare
multiple static builds of FFmpeg on the same host.

Requirements
------------

`sffmpeg` requires:

- a POSIX-compliant system (virtually any system today).
- a recent version of [gcc](http://gcc.gnu.org/).
- a recent version of [cmake](http://www.cmake.org/) (2.8.8+, with proper git and mercurial bindings).
- the [autoconf](http://www.gnu.org/software/autoconf/) and [libtool](http://www.gnu.org/software/libtool/) utilities.
- the [pkg-config](http://www.freedesktop.org/wiki/Software/pkg-config) utility.

Usage
-----

Just type the following commands at the shell prompt:

    $ git clone https://github.com/pyke369/sffmpeg
    $ cd sffmpeg
    $ make

Then go grab a coffee (or maybe two). The helper will download and compile all FFmpeg dependencies for you.
Once done, you should get a static system-independent FFmpeg binary in the `build/bin` directory.

    $ ./build/bin/ffmpeg
    ffmpeg version 2.3 Copyright (c) 2000-2014 the FFmpeg developers
      built on Jul 18 2014 12:08:26 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
      libavutil      52. 92.100 / 52. 92.100
      libavcodec     55. 69.100 / 55. 69.100
      libavformat    55. 48.100 / 55. 48.100
      libavdevice    55. 13.102 / 55. 13.102
      libavfilter     4. 11.100 /  4. 11.100
      libswscale      2.  6.100 /  2.  6.100
      libswresample   0. 19.100 /  0. 19.100
      libpostproc    52.  3.100 / 52.  3.100
    Hyper fast Audio and Video encoder
    usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man ffmpeg'

    $ ldd ./build/bin/ffmpeg
    not a dynamic executable

From there, you may use the binary immediately or build a Debian package for later deployment (see below).

Packaging
---------

You may optionally build a Debian package by typing the following command at the shell prompt:

    $ make deb

The `ffmpeg` and i`ffprobe` static binaries will be installed by the package in the `/usr/bin` directory.

    $ sudo dpkg -i sffmpeg_2.3_amd64.deb
    Selecting previously unselected package sffmpeg.
    Unpacking sffmpeg (from sffmpeg_2.3_amd64.deb) ...
    Setting up sffmpeg (2.3) ...
