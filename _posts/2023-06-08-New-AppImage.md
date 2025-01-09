---
layout: post
title: New AppImages
---
![Distro Logos](/img/rhel-derivatives.png)<br />
There is now a new alternative (similarly as for macOS) Linux build available
[**here**](https://frakira.fi.muni.cz/~xpulec/ug-alt-builds/)
targetting older Linux distributions than regular
[continuous](https://github.com/CESNET/UltraGrid/releases/tag/continuous)
build.

What is a difference compared to standard continuous builds? Standard
_continuous_ builds are currently built with Ubuntu 20.04. That, however,
restricts the other distribution compatibility to approximately that age
(to be more precise, it requires at least glibc 2.31).

But as there are plenty of enterprise-class distributions that are much more
conservative, like RHEL and its derivatives. For this reasion, the above
(rarely updated) build has been created. For the time being, CentOS 7 is the
oldest, yet supported, distribution, so it has been chosen as the base for
the build.


