Vulkan Flocking: compute and shading in one pipeline!
======================

**University of Pennsylvania, CIS 565: GPU Programming and Architecture, Project 6**

* Kaixiang Miao
* Tested on: Windows 7, i7-3630QM @ 2.40GHz 8GB, GTX 660M 2GB (Lenovo Y580 laptop, personal computer)

### ScreenShots

![](img/72.gif)


### Analysis

* Why do you think Vulkan expects explicit descriptors for things like generating pipelines and commands? 

Vulkan is a explicit low-level graphics API. It uses command buffer pool, which stores the pre-allocated command buffers. Thus, in order to use these buffers correctly, descriptors are needed to be bound to them so that GPU knows which buffer to use and what the memory layout is.

* Describe a situation besides flip-flop buffers in which you may need multiple descriptor sets to fit one descriptor layout.

For example, we can use different descriptor sets to describe different texture buffers. Thus we can bind the texture we want into the pipeline.

* What are some problems to keep in mind when using multiple Vulkan queues?

When using multiple Vulkan queues, synchronization is important. Race-condition occurs when different queues are requesting the same memory. In this situation, one queue must wait for the other one until it stop occupying the buffers. Programmers has to deal with these issues correctly and it's the thing we should keep in mind.

* What is one advantage of using compute commands that can share data with a rendering pipeline?

Save time spent on I/O since you can reuse the data.


### Credits

* [Vulkan examples and demos](https://github.com/SaschaWillems/Vulkan) by [@SaschaWillems](https://github.com/SaschaWillems)
