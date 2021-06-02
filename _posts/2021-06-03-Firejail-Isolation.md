---
layout: post
title: Firejail Isolation
---
[![cat in a box (illustration)](/img/cat-5453535.jpg)](https://pixabay.com/)
This post will show how to utilize [Firejail](https://firejail.wordpress.com/) to
isolate the _UltraGrid_ process when run from an _AppImage_. AppImage already comes
with an automatic isolation using a default Firejail profile when running the
_AppImage_ from _GUI_ (eg. using the .desktop file). We will, however, focus
on running from a command-line interface.

A new optional environment variable `ULTRAGRID_USE_FIREJAIL` has been added to
AppImages in order to run the UltraGrid process with _Firejail_. The profile
is quite restrictive and some things may get broken. If you came across some,
please report it. Sample usage is:

    export ULTRAGRID_USE_FIREJAIL=1
    ./UltraGrid-continuous-x86_64.AppImage -d gl

Using that variable requires the `firejail` binary to be present on the system. If not,
UltraGrid won't get started. Also keep in mind that defining the environment variable has
effect only when running without the GUI. The GUI version is
[implicitly guarded](https://firejail.wordpress.com/documentation-2/appimage-support/) when
run through the _.desktop_ file (eg. from within the desktop environment) but the profile
is quite permissive.

You can check if _Firejail_ is effective by listing firejailed processes:

    firejail --list

UltraGrid is run approximately with the following options (_UltraGrid_ uses also
`--shell=none --private-bin=none`). You can issue the following command to check with shell
which parts of system are being isolated:

    firejail --caps.drop=all --ipc-namespace --nonewprivs --noroot \
      --protocol=unix,inet,inet6 --seccomp --disable-mnt \
      --private-opt=none --dbus-user=none --dbus-system=none \
      --private --read-only=/tmp --keep-var-tmp --writable-var \
      --private-etc=alsa,group,hostname,ld.so.conf,ld.so.cache,ld.so.conf.d,nsswitch.conf,passwd,resolv.conf

If you want a custom rules, you may even provide your own _profile file_. Just set
the variable `ULTRAGRID_USE_FIREJAIL` to path to your profile (values ending with `.profile`
are considered as profile files):

    export ULTRAGRID_USE_FIREJAIL=uv.profile
    ./UltraGrid-continuous-x86_64.AppImage -d gl

The use of Firejail is certaily possible also when not running UltraGrid from AppImage, eg.
own instance or from packages. In that case the options above may need minor adjustments, namely
not to blacklist the location from which the binary is run - if it is installed, skipping
`--private-bin` may be enough. If it is just compiled in user's home, skipping `--private` may
be required (and perhaps replacing the option with more lenient options).

Firejail support is available in _continuous_ builds since 3th June 2021.

