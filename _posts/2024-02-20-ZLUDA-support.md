---
layout: post
title: ZLUDA support
---
[![AMD GPU](/img/pc-2798015_640.jpg)](https://pixabay.com/photos/pc-calculation-technology-mining-2798015/)<br />

With the help of [**ZLUDA**](https://github.com/vosen/ZLUDA) you can now
utilize **CUDA** support on **AMD GPUs**.

ZLUDA tool has recently released [support for AMD
cards](https://www.xda-developers.com/nvidia-cuda-amd-zluda/), allowing
to run _native CUDA_ application on AMD GPU.

In terms of UltraGrid it means that CUDA-accelerated
code can be run on AMD HW as well. This is mostly
interesting namely for GPUJPEG, more instructions can be found
[here](https://github.com/CESNET/GPUJPEG/blob/master/ZLUDA.md). Measured
[performance](https://github.com/CESNET/GPUJPEG/tree/master?tab=readme-ov-file#performance)
of AMD Radeon RX 7600 roughly matches NVIDIA GTX 2080 Ti, which has
approximately the same performance. That means it works roughly
with native performance of the card. Other code, like GPU-accelerated
LDGM works as well.

iGPU are also supported, but only the
newest based on RDNA 3 (and partially some of [RDNA
2](https://en.wikipedia.org/wiki/RDNA_2#Integrated_graphics_processing_units_(iGPUs))
cards) provide sufficient performance.
