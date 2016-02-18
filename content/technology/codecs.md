---
title: "Video Codecs"
date: 2015-11-16
weight: 2
image: "video-codecs.jpg"
menu:
  main:
    name: "Video Codecs"
    parent: "Technology"
    weight: 0
---

Ever since video first started to be stored digitally, the problems with storage and bandwidth requirements arose. Today, with a lot of video streamed online and the skyrocketing use of video on smartphones, the problems have only become larger and will continue to entice engineers and mathematicians for the forseeable future. 

In order to reduce the size of a video file we use a codec, which is short for *compressor and decompressor*. This concept is closely linked to [compression](../compression). Codecs are not to be confused with the concept of *container* which contains all the information about the video file, including what codec is used. Common video codecs are H.264/MPEG-4, WMV (Windows Media Video) and VP8, while common container formats are AVI, MP4, and MKV (Matroska). <!--more--> The codec concept exists in similar fashion for audio and image files as well, although file sizes are nowhere near those of video clips.

A video codec can either be a hardware component or more commonly a piece of software to convert raw (uncompressed) digital video to a compressed format, and back. There is a standard specification which describes how a particular codec works. They typically specify a lossy compression, meaning that the compressed video lacks some of the information present in the original video. A consequence of this is that decompressed video has lower quality than the original video. In general, one must always endeavor to strike a balance between video quality and file size.

It is not as easy as a fraction. There are complex relationships between video quality, the amount of data used to represent the video (determined by the bit rate), the complexity of the encoding and decoding algorithms, sensitivity to data losses and errors, ease of editing, random access, and end-to-end delay (latency). Codecs are widely used in applications that record or transmit video, which may not be feasible with the high data volumes and bandwidths of uncompressed video. For example, they are used in operating theaters to record surgical operations, in IP-based security systems, and in remotely operated vehicles such as ROVs and UAVs where Vidhance solutions are also used.

All codecs benefit from stabilization because compression becomes easier. Most use common, standard video compression formats.  For example, video created with a standard MPEG-4 Part 2 codec such as Xvid can be decoded (played back) using any other standard MPEG-4 Part 2 codec such as FFmpeg, MPEG-4 or DivX Pro Codec, because they all use the same video format.

As also described in the document on compression, storing complete information about every frame is unneccessary. It is enough to save the change (or *diff*) from one frame to another. Still, some frames are kept in their entirety to make it easier to jump around in the video. These complete frames are called *key frames*.

There is no single "best" codec for a general scenario. Beyond the trade-offs of video quality and frame rate vs. file size, as well as compression/decompression time consumption, the efficiency of a codec can depend heavily on CPU support, RAM speed and the availability of a graphics card or some other compatible accelerator. 

Vidhance must handle video of different formats in order to be useful. Smartphones and cameras differ widely in terms of performance and Vidhance automatically adapts to that.
