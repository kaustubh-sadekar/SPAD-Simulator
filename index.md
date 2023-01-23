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

A time of flight (ToF) imaging system has three major components - An active light source, a photodetector, and a circuit that records, computes, and transfers the time elapsed (time of flight) between the emission and detection of the signal photons. In a SPAD-based direct ToF imaging system, the active light source is a laser, and the photodetector is a SPAD pixel.

The following image illustrates the direct ToF imaging model for a SPAD-based ToF imaging system. The light source (an infrared laser) emits signal photons as periodic laser pulse s(t) = &delta; (t). The laser pulse interacts with the 3D scene and is reflected back. Finally, the SPAD pixel detects the reflected signal photons, and the time elapsed between the emission and detection of the signal is measured as the time of flight ( t<sub>0</sub> ). The scene depth is obtained by multiplying $t_0$ with the speed of light and dividing by two.

<p align='center'>
  <img src='images/ToF_Diagram.png' width="80%">
</p>
<p align='center'>
    Figure 1 - Diagram explaining the imaging model for SPAD-based ToF imaging system. <i>Modified version of the diagram from [1]</i>.
</p>

`So why is it so difficult to estimate depth? - we can start the timer as the laser emits the signal and stop the timer when the signal is detected.`
<p align='center'>
  <img src='https://user-images.githubusercontent.com/42736936/213940266-6c7e6413-c015-4146-b4a7-4f5addc33840.png' width="80%">
</p>
<p align='center'>
    <a href="https://user-images.githubusercontent.com/42736936/213940266-6c7e6413-c015-4146-b4a7-4f5addc33840.png"> <i> Image source </i> </a>.
</p>

Theoretically, we can estimate time of flight ( t_0 ) by measuring the delay between the peak of the source signal s(t) and the received signal r(t). As the source signal is in our control its peak can be set to t = 0 hence the real challenge is in finding the accurate peak location of the received signal. There are multiple factors that make this a challenging task.

1. SPAD measurements are discrete.
  SPAD measurements are discrete hence we cannot measure the full continuous waveform of the recieved signal but only sample it and try to estimate or approximate it. The technique used in SPAD-based single photon cameras to sample r(t) is called timecorrelated single-photon counting(TCSPC). The timestamps for each detected photons are recorded for multiple laser cycles and finally a histogram of photon timestamps is created denoted by h[n].

2. Photon arrival is nondeterministic in nature.
  SPADs are fast enough to capture individual photons hence we can achive high sampling rate using SPADs. However, it is important to note that $\Phi(t)$ represents the expected received signal and not the actual photon timestamp histogram. Hence, even if we are able to avoid the pile-up effect and capture every photon incident on the SPAD pixel, the photon timestamp histogram would still not look like a quantised/ sampled version of $\Phi(t)$. This is because the photon timestamps follow a Poisson distribution where the value of $\Phi(t)$ represents the expected number of photons detected in a given time interval but the actual photon counts may vary. Hence, if the photon timestamps are not recorded for sufficient number of laser cycles the peak of the photon timestamp histogram may not correspond to the received signal $\Phi(t)$ resulting in inacurate depth estimates. The following GIF illustrates this phenomenon for a single SPAD pixel using our SPAD simulator.

<p align='center'>
  <img src='images/photon_hist.png' width="80%">
</p>
<p align='center'>
    Figure 2 - GIF illustrating the effect of photon randomness on the measure photon timestamp histogram and its deviation form the expected recieved signal. We clearly observe that increasing the number of laser cycles takes measured histogram closer to the return signal waveform.</i>.
</p>

3. Poor signal to background ratio (SBR).
  SBR is the ratio of expected number of signal photons ($Phi_{sig}$) to the expected number of background photons ($\Phi_{bg}$). In case of poor SBR scenarios the difference between expected number of signal photons and background photons is less hence there is a high probability that the SPAD pixel measures more background photons than the signal photons resulting in noisy histograms with inacurate peak and hence noisy depth estimates. The following GIF illustrates the effect of SBR on the measured histogram and the depth estimates.
  
  
<p align='center'>
  <img src='images/effect_of_SBR.png' width="80%">
</p>
<p align='center'>
    Figure 3 - GIF illustrating the effect of SBR on the measured histogram and the corresponding depth estimates.</i>.
</p>


  
  


## .......This page will be updated soon .....................
---

## References
1. F. Gutierrez-Barragan, A. Ingle, T. Seets, M. Gupta and A. Velten, "Compressive Single-Photon 3D Cameras," 2022 IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), New Orleans, LA, USA, 2022, pp. 17833-17843, doi: 10.1109/
CVPR52688.2022.01733.

2. 
