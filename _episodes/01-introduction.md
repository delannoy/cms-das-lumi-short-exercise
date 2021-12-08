---
title: "Introduction"
teaching: 10
exercises: 0
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

## Luminosity and its importance

In the context of the LHC, instantaneous luminosity, $$ \mathcal{L}_{inst} $$, corresponds to the number of "interactions" produced when "bunches" of protons are crossed.
Roughly speaking, it corresponds to the "rate of interactions/events/collisions".
During Run 2 of the LHC, groups of ~100 billion protons were crossed as often as 25 million times per second.
This yielded overall an average of 34 interaction per crossing within the CMS detector.

![Interactions per crossing (pileup) for 2015-2018](https://cmslumi.web.cern.ch/publicplots/pileup_allYears_run2.png){:width="50%"}

More precisely, instantaneous luminosity quantifies the ability of particle accelerator to produce a certain number of interactions.
It represents a proportionality factor between rate of interactions ($$ \frac{dN}{dt} $$) and the cross-section ($$ \sigma $$):

$$ \frac{d\mathrm{N}}{dt} = \mathcal{L}_{inst} \dot \sigma $$

Thus, instantaneous luminosity is usually expressed in the cgs units of $$ \mathrm{cm^{-2} s^{-1}} $$.
Units of "barns" are also used frequently, thanks to [two Purdue University physicists working on the Manhattan Project in 1942](https://www.symmetrymagazine.org/article/february-2006/hitting-the-broad-side-of-a-classified-barn), where $$ 1 b = \mathrm{cm^{-24} $$
For example, let's *very roughly* calculate the total Higgs Boson production rate at CMS:

>> ## Total Higgs boson production rate at CMS during 2018
>> During [May 2018](https://cmsoms.cern.ch/cms/fills/summary?cms_date_from=2018-05-01&cms_date_to=2018-05-31&cms_fill_stableOnly=true), the LHC routinely delivered instantanous luminosities of $$ \approx 2 \times 10^{34} \mathrm{cm^{-2} s^{-1}} $$ ($$ 0.02 \frac{\mathrm{pb}}{\mathrm{s}} $$) at CMS.\
>> The total production cross section of Standard Model Higgs boson at $$ \sqrt{s} = 13 \mathrm{TeV} $$ can be somewhat underestimated to be $$ \approx 50 \mathrm{pb} $$ ([see table 11.2 in the 2020 PDG](https://pdg.lbl.gov/2020/reviews/rpp2020-rev-higgs-boson.pdf))\
>> Thus, we *very approximately* get:\
>> $$ \frac{d\mathrm{N_{Higgs}}}{dt} = \mathcal{L}_{inst} \dot \sigma_{\mathrm{Higgs}}^{\mathrm{total}} \approx 0.02 \frac{\mathrm{pb}}{\mathrm{s}} \times 50 \mathrm{pb} \approx 1 \mathrm{Hz} $$
{: .challenge}

{% comment %}
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

{% endcomment %}

{% include links.md %}

