---
title: "Using brilcalc"
teaching: 10
exercises: 20
questions:
- "What tools are available to query the delivered and recorded luminosity?"
objectives:
- "Learn how to use brilcalc to query luminosity information."
keypoints:
- "`brilcalc` is a command-line tool provided by the CMS BRIL group for querying luminosity information."
---

> ## Important
> **This exercise is meant to be run from lxplus.cern.ch.**
>
> Please follow the [setup instructions](https://delannoy.github.io/cms-das-lumi-short-exercise/setup.html) before getting started.
{: .prereq}

# brilcalc

`brilcalc` is the official tool for querying CMS luminosity information.
It currently has three subcommands: `lumi`, `beam`, and `trg`.
The official brilcalc documentation can be found here: [https://cmslumi.web.cern.ch/](https://cmslumi.web.cern.ch/).

## brilcalc lumi

This lesson will focus on the `brilcalc lumi` subcommand, which can query the delivered and recorded CMS luminosity.
Let's try a few examples:

> ## Glossary
> If you are unfamiliar with "fills", "runs", "lumisections", etc, you can find their definitions in the [Glossary](https://delannoy.github.io/cms-das-lumi-short-exercise/reference.html#glossary)
{: .callout}

> ## Run brilcalc for [fill 6666](https://cmsoms.cern.ch/cms/fills/report?cms_fill=6666)
> ```bash
> brilcalc lumi -f 6666
> ```
> {: .source}
> > ## Output
> > ```
> > #Data tag : 19v3 , Norm tag: onlineresult
> > +-------------+-------------------+------+------+---------------------+---------------------+
> > | run:fill    | time              | nls  | ncms | delivered(/ub)      | recorded(/ub)       |
> > +-------------+-------------------+------+------+---------------------+---------------------+
> > | 316108:6666 | 05/10/18 20:54:10 | 20   | 7    | 405.423497145       | 107.184508306       |
> > | 316109:6666 | 05/10/18 21:01:36 | 54   | 45   | 10039605.429211318  | 3542879.861587470   |
> > | 316110:6666 | 05/10/18 21:22:27 | 217  | 210  | 84147739.992830962  | 79017103.630366772  |
> > | 316111:6666 | 05/10/18 22:46:45 | 59   | 48   | 20773266.833208650  | 14573457.533706700  |
> > | 316112:6666 | 05/10/18 23:09:31 | 19   | 10   | 6499507.705982770   | 228.928666450       |
> > | 316113:6666 | 05/10/18 23:16:41 | 68   | 64   | 22720996.040678266  | 19663097.809963763  |
> > | 316114:6666 | 05/10/18 23:42:59 | 1647 | 1647 | 371661976.624663532 | 362106384.976257861 |
> > +-------------+-------------------+------+------+---------------------+---------------------+
> > #Summary:
> > +-------+------+------+------+---------------------+---------------------+
> > | nfill | nrun | nls  | ncms | totdelivered(/ub)   | totrecorded(/ub)    |
> > +-------+------+------+------+---------------------+---------------------+
> > | 1     | 7    | 2084 | 2031 | 515843498.050072670 | 478903259.925057292 |
> > +-------+------+------+------+---------------------+---------------------+
> > ```
> > {: .output}
> {: .solution}
{: .challenge}

> ## Run brilcalc for [run 325000](https://cmsoms.cern.ch/cms/runs/report?cms_run=325000)
> ```bash
> brilcalc lumi -r 325000
> ```
> {: .source}
> > ## Output
> > ```
> > #Data tag : 19v3 , Norm tag: onlineresult
> > +-------------+-------------------+-----+------+---------------------+--------------------+
> > | run:fill    | time              | nls | ncms | delivered(/ub)      | recorded(/ub)      |
> > +-------------+-------------------+-----+------+---------------------+--------------------+
> > | 325000:7324 | 10/21/18 08:03:56 | 376 | 371  | 100027429.112490401 | 95257794.416809484 |
> > +-------------+-------------------+-----+------+---------------------+--------------------+
> > #Summary:
> > +-------+------+-----+------+---------------------+--------------------+
> > | nfill | nrun | nls | ncms | totdelivered(/ub)   | totrecorded(/ub)   |
> > +-------+------+-----+------+---------------------+--------------------+
> > | 1     | 1    | 376 | 371  | 100027429.112490401 | 95257794.416809484 |
> > +-------+------+-----+------+---------------------+--------------------+
> > ```
> > {: .output}
> {: .solution}
{: .challenge}

### `brilcalc` options

`brilcalc` provides a generous number of command line options.
You can get a summary by running `brilcalc lumi --help`.
But the [official documentation](https://cmslumi.web.cern.ch/#brilcalc) is much more comprehensive.

> ## brilcalc common command options
> Selections
> : select period to query (fill, run, start & end timestamps, etc.)
> Filters
> : filter conditions to query (stable beams, proton physics, etc.)
> Output/Display
> : specify output file, table/csv/html output format, utc/local time, etc.
> Database connection
> : connect to a database, such as a web cache


> ## `brilcalc --output-style`
> The stdout (display output) of `brilcalc` can be specified with the `--output-style` flag.
> Note that this in a "common" or "global" option, meaning that it is also available for the `brilcalc beam` and `brilcalc trg` subcommands.
> Let's reproduce the above output in csv format:
> ```bash
> brilcalc lumi -r 325000 --output-style csv
> ```
> {: .source}
> > ## Output
> > ```
> > #Data tag : 19v3 , Norm tag: None
> > #run:fill,time,nls,ncms,delivered(/ub),recorded(/ub)
> > 325000:7324,10/21/18 08:03:56,376,371,100027429.112490401,95257794.416809484
> > #Summary:
> > #nfill,nrun,nls,ncms,totdelivered(/ub),totrecorded(/ub)
> > #1,1,376,371,100027429.112490401,95257794.416809484
> > ```
> > {: .output}
> {: .solution}
{: .challenge}

> ## Query luminosity info for fill corresponding to run 325000
> > ## Solution
> > Determine the fill number given a run number using overly-complicated `awk` syntax:
> > ```bash
> > fill="$(brilcalc lumi -r 325000 --output-style csv | awk 'BEGIN{FS="[,:]"}; /run:fill/{getline;print $2}')"
> > echo "${fill}"
> > ```
> > {: .source}
> > ```
> > 7324
> > ```
> > {: .output}
> > Or, determine the fill number given a run number "by hand" using simpler `grep` syntax:
> > ```bash
> > brilcalc lumi -r 325000 --output-style csv | grep --after-context=1 'run:fill'
> > fill=7324
> > ```
> > {: .source}
> > ```
> > #run:fill,time,nls,ncms,delivered(/ub),recorded(/ub)
> > 325000:7324,10/21/18 08:03:56,376,371,100027429.112490401,95257794.416809484
> > ```
> > {: .output}
> > Run the `brilcalc lumi` command for the fill (7324) corresponding to run 325000:
> > ```bash
> > brilcalc lumi -f "${fill}"
> > ```
> > {: .source}
> > ```
> > #Data tag : 19v3 , Norm tag: onlineresult
> > +-------------+-------------------+-----+------+---------------------+---------------------+
> > | run:fill    | time              | nls | ncms | delivered(/ub)      | recorded(/ub)       |
> > +-------------+-------------------+-----+------+---------------------+---------------------+
> > | 324993:7324 | 10/21/18 04:13:52 | 4   | 0    | 57.418615708        | 0                   |
> > | 324997:7324 | 10/21/18 04:27:42 | 144 | 135  | 52975599.000250138  | 45212110.272690363  |
> > | 324998:7324 | 10/21/18 05:23:15 | 371 | 362  | 124730512.764399797 | 114778149.184397712 |
> > | 324999:7324 | 10/21/18 07:47:05 | 44  | 38   | 13126573.110420927  | 3909932.614611583   |
> > | 325000:7324 | 10/21/18 08:03:56 | 376 | 371  | 100027429.112490401 | 95257794.416809484  |
> > | 325001:7324 | 10/21/18 10:29:40 | 601 | 601  | 126213437.566453755 | 121487548.568495035 |
> > +-------------+-------------------+-----+------+---------------------+---------------------+
> > #Summary:
> > +-------+------+------+------+---------------------+---------------------+
> > | nfill | nrun | nls  | ncms | totdelivered(/ub)   | totrecorded(/ub)    |
> > +-------+------+------+------+---------------------+---------------------+
> > | 1     | 6    | 1540 | 1507 | 417073608.972630739 | 380645535.057004213 |
> > +-------+------+------+------+---------------------+---------------------+
> > ```
> > {: .output}
> {: .solution}
{: .challenge}
