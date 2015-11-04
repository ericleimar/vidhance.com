---
title: "Transferring data between CPU and GPU"
date: 2015-11-03
weight: 1
image: "circuitboard.jpg"
menu:
  main:
    name: "CPU-GPU Data Transfer"
    parent: "Technology"
    weight: 0
---
In all real-time video analysis, especially in Vidhance, all operations are time critical. Video frames arrive at a steady rate and need to be processed in real time before the next frame arrives. Every millisecond counts.

Complex real-time video enhancement algorithms require work to be done on both the CPU (Central Processing Unit) and the GPU (Graphics Processing Unit) to achieve the highest performance. This is due to the fact that these algorithms depend on both sequential and parallel operations. <!--more-->A CPU handles the former better than a GPU, and vice versa. As these have separate memory, data must be transferred back and forth between them.

Transfer time involves two concepts: latency and throughput. The throughput is the the rate at which the data is transferred during the actual data transfer. Latency is the time it takes for the whole transfer to occur, including time for initialization and waiting. The latency of the transfer becomes important when working with real-time analysis. Although the data throughput may be high, there can be a high latency which increases the overall transfer time. Transfer speed and latency are therefore very important.

Vidhance often has to run on resource constrained devices such as smartphones or rugged computers. Therefore it has to be optimized for minimum resource consumption. Most of the computing time is preferrably spent analyzing and enhancing the video rather than shuffling memory between different processing units. Unfortunately, a large portion of the time is spent preparing the video stream and transferring it between CPU memory and GPU memory. A shorter transfer time means there is more time available to process the image and provide good results.

When image data arrives into the system it has to be decoded into a useful pixel format. Afterwards, it is handled by the CPU, which analyzes the data and applies the first part of the image processing. When the CPU analysis is complete the image is sent to the GPU for further processing. The GPU applies various video enhancing techniques and then outputs the enhanced image to the screen. In some use cases the enhanced video stream needs to be streamed to other systems or saved to disk. In those cases data needs to be transferred back to the CPU, resulting in another resource-expensive transfer between CPU and GPU.

The time required to transfer image data is not completely linear to the data size. The transfer rate heavily depends on the data size and platform, so precautions must be taken not to fall into a possible local minimum. Many different options for data transfer exist, some generic and some platform-specific. OpenGL API functions, the use of a *pixel buffer object* (PBO), and OpenCL all fall in the first category. Intel, AMD, and NVIDIA all have platform-specific alternatives, such as the *INTEL_map_texture* OpenGL extension, the *AMD_pinned_memory* OpenGL extension, or NVIDIA's *GPU Direct* and *Unified Virtual Addressing*. Naturally, Vidhance must make the most of what's available on each device.

By implementing, calibrating, and using a decision tree, only a subset of the above methods needs to be tested. This reduces the time it takes for the data transfer controller to determine the fastest method. The controller could actually do this on the fly by transferring each frame with a new method and comparing the result against the best method so far. After a few frames the best method for that device will have been found. When using the decision algorithms to determine the fastest method, the transfer times can be drastically reduced. Most importantly, this enables work to be performed on the GPU without spending Vidhance's entire time budget.

Most of the information here comes from the Master's thesis "Transfer Time Reduction of Data Transfers between CPU and GPU" performed for us in collaboration with Uppsala university. Read it in full [here](http://urn.kb.se/resolve?urn=urn:nbn:se:uu:diva-205272). This is a problem we continually confront as we strive to improve Vidhance even more.
