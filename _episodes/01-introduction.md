---
title: "Introduction"
teaching: 30
exercises: 10
questions:
- "What is luminosity?"
- "What is the difference between instantaneous and integrated luminosity?"
- "Why is knowing the luminosity important?"
- "How is luminosity measured?"
objectives:
- "Know what luminosity is and why it is important"
- "Know how luminosity is measured"
keypoints:
- "Luminosity is a measure of how many collisions are delivered to and recorded by the detector."
- "Instantaneous luminosity is usually expressed as the number of collisions per square centimeter per second."
- "Integrated luminosity is the integral of instantaneous luminosity over time and is a measurement of data size. It is usually expressed in units of inverse cross section."
- "Knowing the luminosity is important to determining and measuring accelerator and detector performance and operation. It is also an essential component for measuring cross sections and for setting limits on beyond-SM processes."
- "Measurement of luminosity is done with several systems in the detector."
---

> ## References
> You can find several [papers](https://delannoy.github.io/cms-das-lumi-short-exercise/reference.html#papers) with much more technical detail and several [articles](https://delannoy.github.io/cms-das-lumi-short-exercise/reference.html#articles) with additional (less formal) information in the [References](https://delannoy.github.io/cms-das-lumi-short-exercise/reference.html).
{: .callout}

## Instantanous Luminosity

In the context of the LHC, instantaneous luminosity, $$ \mathcal{L}_{inst} $$, corresponds to the number of "interactions" produced when "bunches" of protons are crossed.
Roughly speaking, it corresponds to the "real-time rate of interactions/events/collisions".
During Run 2 of the LHC, groups of ~100 billion protons were crossed as often as 40 million times per second yielding an overall average of 34 interactions per crossing within the CMS detector.

![Interactions per crossing (pileup) for 2015-2018](https://cmslumi.web.cern.ch/publicplots/pileup_allYears_run2.png){:width="50%"}

More precisely, instantaneous luminosity quantifies the ability of particle accelerator to produce a certain number of interactions.
It represents a proportionality factor between rate of interactions $$ \left( \frac{dN}{dt} \right) $$ and the cross-section ($$ \sigma $$):

$$ \frac{d\mathrm{N}}{dt} = \mathcal{L}_{inst} \cdot \sigma $$

Thus, instantaneous luminosity is usually expressed in the cgs units of $$ \mathrm{cm^{-2} s^{-1}} $$.
Units of "barns" are also used frequently, where $$ 1 \mathrm{b} = \mathrm{10^{-24} cm^{2}} $$, thanks to [two Purdue University physicists working on the Manhattan Project in 1942](https://www.symmetrymagazine.org/article/february-2006/hitting-the-broad-side-of-a-classified-barn).
As an example, let's *very approximately* calculate the total Higgs Boson production rate at CMS:

> ## 1.1 Total Higgs boson production rate at CMS
> * During [May 2018](https://cmsoms.cern.ch/cms/fills/summary?cms_date_from=2018-05-01&cms_date_to=2018-05-31&cms_fill_stableOnly=true), the LHC routinely delivered instantanous luminosities of $$ \approx 2 \times 10^{34} \mathrm{cm^{-2} s^{-1}} $$ $$ \left( 0.02 \mathrm{pb^{-1} s^{-1}} \right) $$ at CMS
> * The total production cross section of Standard Model Higgs boson at $$ \sqrt{s} = 13 \mathrm{TeV} $$ can be slightly underestimated as $$ \approx 50 \mathrm{pb} $$ ([see table 11.2 in the 2022 PDG](https://pdg.lbl.gov/2022/reviews/rpp2022-rev-higgs-boson.pdf))
>
> What is the rate of Higgs production at CMS?
> Vote for the corect answer in the [short lumi exercise Mattermost channel](https://mattermost.web.cern.ch/cmsdaslpc2022/pl/ug8kin56kpg17q7r3339fb8rua).
>
> $$ \frac{d\mathrm{N_{Higgs}}}{dt} = \mathcal{L}_{inst}^{\mathrm{peak}} \cdot \sigma_{\mathrm{Higgs}}^{\mathrm{total}} $$
> 
<!--
> > ## Solution
> > $$ \approx 0.02 \mathrm{pb^{-1} s^{-1}} \times 50 \mathrm{pb} \approx 1 \mathrm{Hz} $$
> {: .solution}
-->
{: .challenge}

## Integrated Luminosity

Instantaneous luminosity is aggregated over a certain period of time to obtain integrated luminosity:

$$ \mathcal{L}_{int} = \int \mathcal{L}_{inst} dt $$

It is commonly used to quantify the "amount of data" delivered by the accelerator or recorded by the experiment.
Units of inverse femtobars $$ \mathrm{fb^{-1}} $$ are frequently used in CMS.

![Cumulative delivered and recorded luminosity versus time for 2015-2018 (pp data only)](https://cmslumi.web.cern.ch/publicplots/int_lumi_animated_4x_pp_run2.gif){:width="50%"}

To illustrate, we can *very roughly* estimate the total number of Higgs bosons produced during 24 hours at CMS:

> ## 1.2 Total Higgs bosons produced at CMS during 24 hours
> * During [Nov 2017](https://cmsoms.cern.ch/cms/fills/report?cms_fill=6360), CMS recorded $$ \approx 600 \mathrm{pb^{-1}} $$ during a 24-hour period of stable beams
> * The total production cross section of Standard Model Higgs boson at $$ \sqrt{s} = 13 \mathrm{TeV} $$ can be slightly underestimated as $$ \approx 50 \mathrm{pb} $$ ([see table 11.2 in the 2022 PDG](https://pdg.lbl.gov/2022/reviews/rpp2022-rev-higgs-boson.pdf))
>
> How many Higgs bosons can be produced at CMS during 24 hours?
> Vote for the corect answer in the [short lumi exercise Mattermost channel](https://mattermost.web.cern.ch/cmsdaslpc2022/pl/rtpm39u1bjrmbpi781d1xshqfe).
>
> $$ \mathrm{N_{Higgs}} = \mathcal{L}_{int}^{\mathrm{24hr}} \cdot \sigma_{\mathrm{Higgs}}^{\mathrm{total}} $$
> 
<!--
> > ## Solution
> > $$ \approx 600 \mathrm{pb^{-1}} \times 50 \mathrm{pb} \approx 30 \times 10^{3} $$
> {: .solution}
-->
{: .challenge}

## Importance of Luminosity

Along with the center of mass energy, instantanous luminosity is the most significant performance parameter for any particle accelerator.
Real-time monitoring of instantaneous luminosity is critical for the accelerator to carry out beam tuning and collision optimization.
It is also essential for the CMS trigger system in order to scale or throttle the data throughput.

Measurement of integrated luminosity is also incredibly crucial since its limited precision represents a contribution to the systematic uncertainty for most physics searches and measurements.
The uncertainty in the integrated luminosity is often the dominant systematic uncertainty in EWK cross-section measurements.
We can emphasize the impact of the integrated luminosity uncertainty by considering a relatively rare process:

> ## 1.3 Total Higgs bosons decaying to muon pairs at CMS during 2018
> * During 2018, CMS recorded around $$ \approx 60 \mathrm{fb^{-1}} $$ of good-quality data with 2.5% uncertainty (see the [CMS Lumi POG "quick summary table"](https://twiki.cern.ch/twiki/bin/view/CMS/LumiRecommendationsRun2))
> * The total production cross section of Standard Model Higgs boson at $$ \sqrt{s} = 13 \mathrm{TeV} $$ can be slightly underestimated as $$ \approx 50 \mathrm{pb} $$ ([see Table 11.2 in the 2022 PDG](https://pdg.lbl.gov/2022/reviews/rpp2022-rev-higgs-boson.pdf))
> * The branching ratio for $$ H \rightarrow \mu \mu $$ can be approximated as $$ \approx 2 \times 10^{-4} $$ ([see Table 11.3 in the 2022 PDG](https://pdg.lbl.gov/2022/reviews/rpp2022-rev-higgs-boson.pdf))
>
> What is the minimum and maximum expected event yield given the uncertainty in integrated luminosity?
> Vote for the corect answer in the [short lumi exercise Mattermost channel](https://mattermost.web.cern.ch/cmsdaslpc2022/pl/9gg4eh5mmf81pfiagrp64c4ero).
>
> $$ \mathrm{N}_{H \rightarrow \mu \mu}^{2018} = \left( \mathcal{L}_{int}^{2018} \pm \delta \right) \cdot \sigma_{\mathrm{Higgs}}^{\mathrm{total}} \cdot \mathcal{B}_{H \rightarrow \mu \mu} $$
> 
<!--
> 
> [![](https://api.gh-polls.com/poll/01FPCNXDGM7M4K4D8ES1PXYB2J/%5B297.5%2C%20302.5%5D)](https://api.gh-polls.com/poll/01FPCNXDGM7M4K4D8ES1PXYB2J/%5B297.5%2C%20302.5%5D/vote)
> [![](https://api.gh-polls.com/poll/01FPCNXDGM7M4K4D8ES1PXYB2J/%5B292.5%2C%20307.5%5D)](https://api.gh-polls.com/poll/01FPCNXDGM7M4K4D8ES1PXYB2J/%5B292.5%2C%20307.5%5D/vote)
> [![](https://api.gh-polls.com/poll/01FPCNXDGM7M4K4D8ES1PXYB2J/%5B299.875%2C%20300.125%5D)](https://api.gh-polls.com/poll/01FPCNXDGM7M4K4D8ES1PXYB2J/%5B299.875%2C%20300.125%5D/vote)
>
-->
<!--
> > ## Solution
> > $$ \leq \left( 60 + \frac{2.5}{100} \cdot 60 \right) \cdot 10^{3} \mathrm{pb^{-1}} \cdot 50 \mathrm{pb} \cdot 2 \times 10^{-4} = 615 $$\
> > $$ \geq \left( 60 - \frac{2.5}{100} \cdot 60 \right) \cdot 10^{3} \mathrm{pb^{-1}} \cdot 50 \mathrm{pb} \cdot 2 \times 10^{-4} = 585 $$
> {: .solution}
-->
{: .challenge}

## Luminosity Measurement

CMS has two dedicated systems for measuring luminosity, both located $$ z \approx \pm 1.8 \mathrm{m} $$ from the interaction point and radius $$ \approx 6 \mathrm{cm}$$:

Fast Beam Condition Monitor (BCM1F)
: C-shaped PCBs arranged into two rings at each side of CMS with double-pad silicon sensors
: Real-time histogramming with 6.25 ns per-bin facilitates measurement of machine-induced background

![BCM1F C-shape](https://cds.cern.ch/record/2765247/files/2021-05-20%2015.19.28.jpg?subformat=icon-1440){:width="50%"}

Pixel Luminosity Telescope (PLT)
: 16 "telescopes" (8 per side of CMS) with three hybrid silicon pixel sensors per telescope
: Fast cluster-counting signal (40 MHz) in addition to full pixel info readout

![Pixel Luminosity Telescope](https://cds.cern.ch/record/2777045/files/2021-06-29%2011.19.34.jpg?subformat=icon-1440){:width="50%"}

In addition, several sub-detectors are used for luminosity measurement, among them:

PCC (Pixel Cluster Counting)
: Counts the mean number of pixel clusters in the most "stable" modules of the silicon pixel detector

Hadronic Forward (HF)
: Steel absorber with quartz fibers to detect Cherenkov light histogrammed as function of bunch crossing

> ## Which detector is more photogenic?
> This is the *most important* poll!
> [![](https://api.gh-polls.com/poll/01FPDCW35SGWA9YWV70HN8G1Y4/PLT)](https://api.gh-polls.com/poll/01FPDCW35SGWA9YWV70HN8G1Y4/PLT/vote)
> [![](https://api.gh-polls.com/poll/01FPDCW35SGWA9YWV70HN8G1Y4/BCM1F)](https://api.gh-polls.com/poll/01FPDCW35SGWA9YWV70HN8G1Y4/BCM1F/vote)
{: .challenge}

## Luminosity Calibration

The precise determination of integrated luminosity is particularly challenging at hadron colliders, in part due to the theoretical predictions (e.g. uncertainties in the parton distribution functions and precision of parton-level cross-section calculations) being generally less precise compared to $$ e^{+} e^{−} $$ colliders.
A sub-detector can measure "relative" luminosity on an arbitrary scale based on the reported event rate.
The determination of "absolute" luminosity involes re-scaling the measured event rate by a proportionality factor, $$ \sigma_{vis} $$, derived from the properties of the colliding beams.
This scaling factor may be thought of as a way to account for the sub-detector's particular acceptance and response.

At the LHC, the primary technique to determine the absolute luminosity scale is the van der Meer (vdM) scan method, based on dedicated beam-separation scans.
The size and shape of the interaction region is measured by recording the relative interaction rates as a function of the transverse beam separation.
After adopting several assumptions (e.g. transverse and longitudinal beam densities are Gaussian, density functions are factorizable into $$x$$- and $$y$$-dependent components, etc.), the visible cross-section can be expressed as

$$ \sigma_{vis} = \mu_{vis}^{\mathrm{max}} \frac{2 \pi \Sigma_{x} \Sigma_{y}}{n_{1} n_{2}} $$

where $$ \mu_{vis}^{\mathrm{max}} $$ is the peak visible interaction rate,
$$ n_{1} $$ and $$ n_{2} $$ are the numbers of particles in each of the two bunches,
and $$ \Sigma_{x} $$ and $$ \Sigma_{y} $$ correspond to the effective beam overlap widths in each scan plane.

### Corrections to vdM scan data

Several systematic effects can affect the measurement of $$ \sigma_{vis} $$.
These represent a significant contribution to the final uncertainty in the measurement of integrated luminosity.

Orbit drift corrections
: Potential bias from beam positions monitors (DOROS, Arc BPM) at the $$ \mu \mathrm{m} $$ scale

Beam-beam effects
: EM interaction between colliding bunches (deflection & shape)

Length scale calibration
: Possible differences in the absolute scale between the nominal beam separation (produced by the steering of the LHC magnets) and the actual separation

Transverse factorizability
: Non-factorizability of $$x$$ and $$y$$ components measured and corrected with the beam-image method
: Beam-imaging method: the distributions of reconstructed vertices during beam-imaging scans are used to obtain an image of the transverse bunch profiles integrated over the scanning direction

Other corrections
: "Spurious" charges present outside the nominally filled bunches (ghosts👻 in empty bunch slots and out-of-time satellite🛰 charges adjacent to the main bunch)

> ## Dominant uncertainties in the absolute luminosity scale ($$ \sigma_{vis} $$)
> * beam position monitoring
> * transverse factorizability
> * beam-beam effects
{: .callout}

### Rate corrections under physics running conditions

Several corrections must be applied to luminometer rates to ensure that the final luminosity values are accurate.

Out-of-time pileup corrections
: Most detectors have out-of-time contributions that do not arise from the main colliding bunch (spillover of electronic signals and real additional response from material activation)

Efficiency corrections
: Radiation damage can affect the detector response by reducing efficiency, increasing noise, or both

Nonlinear response
: Over- or under-counting as a function of instantaneous luminosity

Detector stability and linearity
: Determined from comparisons between luminometers

<!--

The luminosity of a collider is the number of collisions per area (i.e. cross section) per time. The typical unit is $$ \mathrm{cm^{-2} s^{-1}} $$. This luminosity is sometimes referred to
as the "instantaneous" luminosity $$ \mathcal{L}_{inst} $$. The "integrated" luminosity is the integral of the instantaneous luminosity over time:

$$ \mathcal{L}_{int} = \int \mathcal{L}_{inst} dt $$

The integrated luminosity is a measurement of data size and is usually expressed in units of inverse cross section such as $$ \mathrm{fb^{-1}} $$.

The importance of knowing the integrated luminosity cannot be overstated. It is an esssential component for measuring cross sections and for setting upper limits on new physics processes beyond
the Standard Model. You can't determine well how much you see (or don't see) coming out of the collisions if you don't know accurately and precisely what came in.

## Measuring luminosity
CMS has several systems for measuring luminosity including making use of the hadronic forward calorimeter and the pixel detector. There have also been several dedicated luminometers installed over the course of operation of CMS.

The readout rate of quantities like hits in a detector (like a luminometer) is given by $$ R $$ and is given by the product of the instantaneous luminosity $$ \mathcal{L}_{inst} $$ and the visible cross section $$ \sigma_{vis} $$:

$$ R = \mathcal{L}_{inst} \sigma_{vis}$$

The determination of $$ \sigma_{vis} $$ is carried out in so-called van der Meer (VdM) scans. In these scans the two colliding beams are separated and then moved across each other.
The rate $$ R $$ is then determined as a function of beam separation to measure the beam overlap width.

The instantaneous luminosity $$ \mathcal{L}^{i}_{inst} $$ for
a single colliding bunch $$ i $$ can be determined from the beam overlap width and
known beam parameters such as the number of protons in each colliding bunch for each beam and the LHC orbit frequency. Then a value for $$ \sigma_{vis} $$ can be obtained.

A VdM scan is a special beam condition but this value of $$ \sigma_{vis} $$ still holds for regular colliding beam conditions (since the detector acceptance has in-principle not changed). Therefore this value along with $$ R $$ can be used to subsequently determine $$ \mathcal{L}_{inst} $$.

In practice the performance of the luminometers can degrade over time due to effects such as radiation damage. CMS is capable of conducting fast luminosity scans with small beam separation, so-called "emmittance scans". These scans, performed similarly to VdM scans,
can take just a few minutes and are typically performed at the beginning and at the end of a fill.

-->

{% include links.md %}

