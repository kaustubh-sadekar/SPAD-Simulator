---
layout: default
---

# Simulating Single Photon Cameras for Supervised Depth Estimation

<!-- Place this tag where you want the button to render. -->
<a class="github-button" href="https://github.com/kaustubh-sadekar/SPAD-Simulator" target="blank_" data-color-scheme="no-preference: light; light: light; dark: dark;" data-size="large" aria-label="Star kaustubh-sadekar/SPAD-Simulator on GitHub">Star Repository</a>

## Project in brief
SPAD-based cameras are becoming a popular choice of sensors for direct time-of-flight 3D imaging systems. However, the depth estimates are significantly affected when the ambient light is stronger than the light source used by the 3D imaging system. This project aims to simulate a SPAD sensor and study the effect of laser power, background light strength, scene depth, and albedo on the SPAD sensor measurements.

`*Note: This project page does not cover the basics of time of flight imaging and SPADs. Links to relevant blogs to be updated here soon*`

## SPAD-based time of flight imaging model

A time of flight (ToF) imaging system has three major components - An active light source, a photodetector, and a circuit that records, computes and transfers the time elapsed (time of flight) between the emission and detection of the signal photons. In a SPAD-based direct ToF imaging system, the active light source is a laser, and the photodetector is a SPAD pixel.

The following image illustrates the direct ToF imaging model for a SPAD-based ToF imaging system. The light source (an infrared laser) emits signal photons as periodic laser pulse `$s(t) = \delta(t)$`. The laser pulse interacts with the 3D scene and is reflected back. Finally the SPAD pixel detects the reflected signal photons, and the time elapsed between the emission and detection of the signal is measured as the time of flight ($t_0$). The scene depth is obtained by multiplying $t_0$ with the speed of light and dividng by two.

<p align='center'>
  <img src='images/ToF_Diagram.png' width="60%">
</p>
<p align='center'>
    Figure 1 - Diagram explaining the imaging model for SPAD-based ToF imaging system. <i>Modified version of diagram from [1]</i>.
</p>





## .......This page will be updated soon .....................
---

## References
1. F. Gutierrez-Barragan, A. Ingle, T. Seets, M. Gupta and A. Velten, "Compressive Single-Photon 3D Cameras," 2022 IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), New Orleans, LA, USA, 2022, pp. 17833-17843, doi: 10.1109/
CVPR52688.2022.01733.

2. 
