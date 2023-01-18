---
layout: post
title: UltraGrid updates
---
![interlaced video](/img/DnI7S.jpg)<br />
In development [**continuous builds**](https://github.com/CESNET/UltraGrid/releases/tag/continuous)
there has recently arrived few new features and also fixes.

Notably was improved the deinterlacing stuff in UltraGrid, notably:

- almost every pixel format can now be deinterlaced, namely higher bit depth ones
- the spatial _blend_ deinterlace was improved in terms of quality (doesn't decay vertical
  resolution to a half) and performance (mainly for 8-bit formats, the speed-up is
  multiple times)
- new temporal deinterlacers _bob_ (`-p deinterlace_bob`) and _linear_ (`-p deinterlace_linear`)
- improved existing ones postprocessors (`deinterlace` and `double_framerate`)
- when deinterlacing is used withing _OpenGL_ display (`-d gl:d`, or pressed '**d**'), shader-based
  deinterlacing is used (which is pretty fast even on higher bit-depth formats, where
  the CPU-backed deinterlacing might have problems)

Also most of the deinterlacers can be safely toggled on whenever _interlaced_
or _progressive_ video arrives - only interlaced video undergoes deinterlace,
progressive is untouched (unless deinterlacing is _forced_). This applies to
spatial deinterlacing, like `-p deinterlace_blend` or `-d gl:p`. Temporal or
temporal-spatial deinterlacing works similar but, while not deinterlacing
progressive video, it still doubles the video frame rate.

There has also already been some nice other features, namely _GUI_
initialization became significantly faster. Also there are some Vulkan fixes,
most of them will be also backported to UltraGrid 1.8.1 planned to be released
tomorrow.
