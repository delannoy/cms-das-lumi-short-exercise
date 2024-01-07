---
title: "Normtags and Data Certification"
teaching: 10
exercises: 20
questions:
- "What is a normtag?"
- "What is data certification?"
objectives:
- "Learn what is a normtag and how to use it"
- "Learn about data certification and how it relates to physics analyses"
keypoints:
- "Make sure to use a normtag when querying brilcalc for your analysis"
- "Data collected by CMS needs to be evaluated and a subset is certified as good quality data to be used for physics analysis"
---

> ## Important
> **This exercise is meant to be run from lxplus.cern.ch.**
>
> Please follow the [setup instructions](https://delannoy.github.io/cms-das-lumi-short-exercise/setup.html) before getting started.
{: .prereq}

# Normtags

A normtag is a file that defines the official luminosity calibrations and detectors to use for a given period.
The normtag files are maintained by the Lumi POG and periodically updated as the calibrations are improved.
It is important to always use the latest normtag in order to get the best results.

> ## Important
> **Never run `brilcalc` without a `--normtag` argument unless you know exactly what you are doing.**\
> Running brilcalc without `--normtag` will give you the online luminosity, which can change significantly by improvements in calibration.
> It is neither accurate, nor precise, nor stable.
{: .callout}

The Run 2 physics normtag is **`/cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_PHYSICS.json`**.
**Always use this normtag for pp runs.**
**This is the only normtag which can be used for physics analyses.**
It covers all of Run 2 for which there is a final approved number for physics (which includes all pp running and some special runs).

> ## 3.1 Query fill 6666 using the physics normtag
>
> Using the physics normtag, what is the recorded luminosity in picobarns for fill 6666?
> Vote for the corect answer in the [short lumi exercise Mattermost channel](https://mattermost.web.cern.ch/cmsdaslpc2024/pl/k4ohf4fx93bm78jcig48dntckc).
{: .challenge}

# Data Certification

<!--
> ## Note
> This section has some overlap with [Excercise 6 from the PPD offline lesson](https://twiki.cern.ch/twiki/bin/view/CMS/SWGuideCMSDataAnalysisSchool2022PPDExercise#Exercise_6_Compute_the_integrate) and [Exercise 14 from the third Pre-Exercise Set](https://fnallpc.github.io/cms-das-pre-exercises/03-CMSDataAnalysisSchoolPreExerciseThirdSet/index.html)
{: .callout}
-->

Data collected by CMS is *certified* on a luminosity-section basis to determine the subset of *data of good quality to be included in physics analyses*.
Data certification is carried out by taking into account both the operational health of the sub-detectors and scrutiny of the reconstructed physics objects by DPG and POG experts.
The outcome of the certification process is regularly updated as more data gets collected, and for each new version of the data processing, by the [DQM-DataCertification](https://twiki.cern.ch/twiki/bin/view/CMS/DQM).
One of the main deliverables of this process are JSON files listing runs and lumisection which are good for physics analysis.

<!--
> ## 3.2 Query processedLumis.json to determine the recorded luminosity for your crab job datset
>
> Refer to your submitted crab job as part of the [third set of the Pre-Exercises](https://fnallpc.github.io/cms-das-pre-exercises/03-CMSDataAnalysisSchoolPreExerciseThirdSet/index.html).
> Recall that you had to transfer the resulting `processedLumis.json` file to lxplus.
> 
> Using the physics normtag, what is the recorded luminosity in inverse femtobarns for your crab job datset?
> Please write the correct answer in the [short lumi exercise Mattermost channel](https://mattermost.web.cern.ch/cmsdaslpc2022/channels/offlineshortexlumi).
{: .challenge}
-->
