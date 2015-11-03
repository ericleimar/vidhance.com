---
title: "Six degrees of freedom"
date: 2015-11-03
weight: 10
menu:
  main:
    name: "Six degrees of freedom"
    parent: "Technology"
    weight: 0
---

# Six degrees of freedom
Our world consists of three dimensions - breadth, width, and height - and the word **freedom** refers to free movement in these three directions. In mathematics and engineering, we usually denote these three dimensions by *x*, *y*, and *z*.

![](six-degrees/degrees.png)

By the word **move**, we mean both changing location by moving along an axis through space - known as translation, but also rotating along an axis while still remaining at the same coordinates. Consider how you would say you are *moving* when you are turning around, even though you're standing on the same spot. A phone, like any other 3D object, has six degrees of freedom. Moving forward/backward, up/down, or left/right is called translation, and rotation around an axis, often termed pitch, yaw, and roll.

Measuring movement in these six degrees of freedom is accomplished today through both AC and DC magnetic or electromagnetic fields in sensors that transmit positional and angular data to a processing unit. The data is in real time processed in Vidhance. Based on the translation and rotation information provided by the smartphone's sensors, or inferred by tracking changes in the current scene, Vidhance uses this information to calculate smoothen out the total movement and make each frame be the scene you intended. This is done by separating the intended motion from the unintended motion, keeping only the former and disregarding the latter.

A rotation in 3D space can be represented numerically in several ways, for example with matrices or with unit quaternions. They provide a convenient mathematical notation for representing orientations and rotations of objects in three dimensions. Compared to Euler angles they are simpler to compose and avoid the problem of gimbal lock.

Gimbal lock is the loss of one degree of freedom in a three-dimensional, three-gimbal mechanism that occurs when the axes of two of the three gimbals are driven into a parallel configuration, "locking" the system into rotation in a degenerate two-dimensional space. Compared to rotation matrices they are more numerically stable and may be more efficient.

**TODO: Add more stuff**
