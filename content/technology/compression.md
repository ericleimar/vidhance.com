---
title: "Video Compression"
date: 2015-11-03
weight: 1
image: "compression.png"
menu:
  main:
    name: "Video Compression"
    parent: "Technology"
    weight: 0
---
We generally say that a video is a series of images, around 30 or so for each second of video. Each image is called a **frame**. This means that storing or transmitting a video file really involves storing or transmitting a potentially very large set of images. Naturally, we want to minimize the time and cost of this action, which is why we *compress* videos.

Images can themselves be compressed, for example by storing them in like JPEG and PNG. However, video compression usually works by computing and compressing **deltas** between frames, the difference between one frame and the next. <!--more--> This is preferable over storing each individual frame as a compressed image, because if a frame is more similar to the previous one, less data is required in order to describe the delta. As a digital image consists of pixels, the delta is an accumulation of differences in corresponding pixels.

The difference, or **diff** for short, between two pixels can be computed by taking the absolute value of the difference between the colors of those pixels. An image diff can be created by computing the pixel diff for every pixel in two different images. If a pixel has the exact same color in both images, that pixel will be black in the diff, since the color black is (0,0,0) in the RGB color space. The larger the difference between corresponding pixels in two frames, the brighter the pixel will be in the diff. Thus the diff between two frames can itself be viewed as an image, as seen below. The more similar the images are, the darker the total diff will be.

The above image shows one frame of a video with the diff on the left. Because the current and next frame are mostly similar images, the diff is mostly black. The outlines of the girl's hair can be seen as purple lines where pixels have gone from green to white: adding purple (255,0,255) to green (0,255,0) results in white (255,255,255). As the video was a bit shaky, there are unwanted camera movements resulting in an unneccessary large diff.

Stabilization works by compensating for unwanted camera movements, effectively making each frame in the video more similar to the one before it. Most modern video encoders (such as H.264) have some form of motion compensation built-in. This compensation can often reduce the delta between two frames to a few vectors describing how elements in the frame have moved in the next. The encoders do not, however, compensate for unwanted movement in the video.

Although professional video is often very stable to begin with, the same cannot be said for amateur video captured using a camcorder or a smartphone. Vidhance stabilization keeps the image stable by compensating for unwanted movement, keeping the object being viewed in place. This makes for a more comfortable viewer experience and takes some of the workload off the video encoder. With a stable video, the current and next frame are even more similar, which would make the diff even more black.

Stabilizing video before compressing it can dramatically reduce file size for medium and low quality video. This translates into less bandwidth usage, ultimately increasing network performance. Our initial study showed file size reduction typically in the range of 5% to 20% in the range of standard encoding qualities.

Video can be encoded at either **constant** or **variable** bitrate. When encoding video at a constant bitrate, the quality of the video is limited by the amount of data allowed for each frame, so the delta must be reduced to that amount of data, even if this means losing a lot of information. When encoding video at a variable bitrate, the bitrate of the video is governed by the quality setting, so in order to maintain a given quality score, the delta may become very complex. Storing a complex delta without losing information requires more data.

By stabilizing the video before compressing it, the delta will be smaller in size because the stabilized frame is more similar to the preceding one. This translates into higher possible video quality with stabilization than without. In all of our experiments, the stabilized video resulted in smaller files for the lower quality settings, especially for very low quality settings.

As a rule, the lower the quality setting, the greater the benefit of stabilization. The net result is a higher-quality video at no effort for the user - Vidhance handles everything in the background.
