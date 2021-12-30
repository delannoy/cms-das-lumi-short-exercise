---
title: "[OPTIONAL] brilcalcpandas"
teaching: 10
exercises: 10
questions:
- "What tools are available to query the delivered and recorded luminosity?"
- "Is there a more convenient way to query `brilcalc` and organize its response?"
objectives:
- "Introduce `brilcalcpandas` as a wrapper for `brilcalc`."
keypoints:
- "`brilcalc` is a command-line tool provided by the CMS BRIL group for querying luminosity information."
---

> ## Important
> **This exercise is meant to be run from lxplus.cern.ch.**
>
> Please follow the [setup instructions](https://delannoy.github.io/cms-das-lumi-short-exercise/setup.html) before getting started.
{: .prereq}

# brilcalcpandas

`brilcalcpandas` is an unofficial [`pandas.DataFrame`](https://realpython.com/pandas-dataframe/) wrapper for `brilcalc` queries.
All [currently-documented](https://cmslumi.web.cern.ch/#brilcalc) `brilcalc` options are supported as keyword arguments.

> ## Setup
> ```bash
> ssh lxplus
> /cvmfs/cms-bril.cern.ch/brilconda3/bin/python3 -m venv --system-site-packages 'brilconda3' && source 'brilconda3/bin/activate' # (optionally, create a python3 virtualenv with access to brilconda3 packages)
> git clone ssh://git@gitlab.cern.ch:7999/adelanno/brilcalcpandas.git && cd brilcalcpandas/
> [[ -n "${VIRTUAL_ENV}" ]] && python3 -m pip install --requirement requirements.txt || /cvmfs/cms-bril.cern.ch/brilconda3/bin/python3 -m pip install --user --requirement requirements.txt # [brilws installation](https://cms-service-lumi.web.cern.ch/cms-service-lumi/brilwsdoc.html#Installation-of-brilws)
> ```
> {: .source}
{: .checklist}

## Usage examples:

### Main function:

The `main` function reproduces delivered/recorded lumi in [LumiPOG Summary Table](https://twiki.cern.ch/twiki/bin/view/CMS/TWikiLUM#SummaryTable)

```bash
/cvmfs/cms-bril.cern.ch/brilconda3/bin/python3 -m brilcalcDF
```
{: .source}

> ## Output
> ```
> DEBUG: brilcalc lumi --output-style csv --tssec -b 'STABLE BEAMS' --amodetag PROTPHYS --beamenergy 6500 -u /fb --normtag /cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_BRIL.json --begin '01/01/15 00:00:00' --end '12/31/15 23:59:59'                                                                                                           > INFO: total 2015 delivered luminosity: 4.308588532 /fb
> ________________________________________________________________________________
> DEBUG: brilcalc lumi --output-style csv --tssec -b 'STABLE BEAMS' --amodetag PROTPHYS --beamenergy 6500 -u /fb --normtag /cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_BRIL.json --begin '01/01/16 00:00:00' --end '12/31/16 23:59:59'
> INFO: total 2016 delivered luminosity: 41.578962968 /fb
> ________________________________________________________________________________
> DEBUG: brilcalc lumi --output-style csv --tssec -b 'STABLE BEAMS' --amodetag PROTPHYS --beamenergy 6500 -u /fb --normtag /cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_BRIL.json --begin '01/01/17 00:00:00' --end '12/31/17 23:59:59'
> INFO: total 2017 delivered luminosity: 49.807263743 /fb
> ________________________________________________________________________________
> DEBUG: brilcalc lumi --output-style csv --tssec -b 'STABLE BEAMS' --amodetag PROTPHYS --beamenergy 6500 -u /fb --normtag /cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_BRIL.json --begin '01/01/18 00:00:00' --end '12/31/18 23:59:59'
> INFO: total 2018 delivered luminosity: 67.85891887 /fb
> ________________________________________________________________________________
> DEBUG: brilcalc lumi --output-style csv --tssec -u /fb --normtag /cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_PHYSICS.json -i /afs/cern.ch/cms/CAF/CMSCOMM/COMM_DQM/certification/Collisions15/13TeV/Reprocessing/Cert_13TeV_16Dec2015ReReco_Collisions15_25ns_JSON_v2.txt
> INFO: total 2015 legacy recorded luminosity: 2.2737730369999998 /fb
> ________________________________________________________________________________
> DEBUG: brilcalc lumi --output-style csv --tssec -u /fb --normtag /cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_PHYSICS.json -i /afs/cern.ch/cms/CAF/CMSCOMM/COMM_DQM/certification/Collisions16/13TeV/Legacy_2016/Cert_271036-284044_13TeV_Legacy2016_Collisions16_JSON.txt
> INFO: total 2016 legacy recorded luminosity: 36.333380074000004 /fb
> ________________________________________________________________________________
> DEBUG: brilcalc lumi --output-style csv --tssec -u /fb --normtag /cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_PHYSICS.json -i /afs/cern.ch/cms/CAF/CMSCOMM/COMM_DQM/certification/Collisions17/13TeV/Legacy_2017/Cert_294927-306462_13TeV_UL2017_Collisions17_GoldenJSON.txt
> INFO: total 2017 legacy recorded luminosity: 41.479680529 /fb
> ________________________________________________________________________________
> DEBUG: brilcalc lumi --output-style csv --tssec -u /fb --normtag /cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_PHYSICS.json -i /afs/cern.ch/cms/CAF/CMSCOMM/COMM_DQM/certification/Collisions18/13TeV/Legacy_2018/Cert_314472-325175_13TeV_Legacy2018_Collisions18_JSON.txt
> INFO: total 2018 legacy recorded luminosity: 59.832475339 /fb
> ________________________________________________________________________________
> DEBUG: brilcalc lumi --output-style csv --tssec -u /fb --normtag /cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_PHYSICS.json -i /afs/cern.ch/cms/CAF/CMSCOMM/COMM_DQM/certification/Collisions15/13TeV/Reprocessing/Cert_13TeV_16Dec2015ReReco_Collisions15_25ns_JSON_v2.txt
> INFO: total 2015 prelegacy recorded luminosity: 2.2737730369999998 /fb
> ________________________________________________________________________________
> DEBUG: brilcalc lumi --output-style csv --tssec -u /fb --normtag /cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_PHYSICS.json -i /afs/cern.ch/cms/CAF/CMSCOMM/COMM_DQM/certification/Collisions16/13TeV/ReReco/Final/Cert_271036-284044_13TeV_ReReco_07Aug2017_Collisions16_JSON.txt
> INFO: total 2016 prelegacy recorded luminosity: 36.32645008 /fb
> ________________________________________________________________________________
> DEBUG: brilcalc lumi --output-style csv --tssec -u /fb --normtag /cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_PHYSICS.json -i /afs/cern.ch/cms/CAF/CMSCOMM/COMM_DQM/certification/Collisions17/13TeV/ReReco/Cert_294927-306462_13TeV_EOY2017ReReco_Collisions17_JSON_v1.txt
> INFO: total 2017 prelegacy recorded luminosity: 41.528995402 /fb
> ________________________________________________________________________________
> DEBUG: brilcalc lumi --output-style csv --tssec -u /fb --normtag /cvmfs/cms-bril.cern.ch/cms-lumi-pog/Normtags/normtag_PHYSICS.json -i /afs/cern.ch/cms/CAF/CMSCOMM/COMM_DQM/certification/Collisions18/13TeV/ReReco/Cert_314472-325175_13TeV_17SeptEarlyReReco2018ABC_PromptEraD_Collisions18_JSON.txt
> INFO: total 2018 prelegacy recorded luminosity: 59.740565202 /fb
> ________________________________________________________________________________
>                                 2015       2016       2017       2018   2015-2018   2016-2018
> delivered luminosity (/fb)  4.308589  41.578963  49.807264  67.858919  163.553734  159.245146
> legacy luminosity (/fb)     2.273773  36.333380  41.479681  59.832475  139.919309  137.645536
> prelegacy luminosity (/fb)  2.273773  36.326450  41.528995  59.740565  139.869784  137.596011
> ```
> {: .output}
{: .solution}

### Interactive usage:

```python
from brilcalcDF import Query
```

```python
Query.lumi(r=325000, byls=True, minBiasXsec=80000, type='hfet', precision='2f', hltpath='HLT_ZeroBias_v6')[1]
```
{: .source}
> ## Output
> ```
> DEBUG: brilcalc lumi --output-style csv --tssec -r 325000 --byls --minBiasXsec 80000 --type hfet --precision 2f --hltpath HLT_ZeroBias_v6
>                            dt        time  deliveredLS  recordedLS     run  fill  delivered(/ub)  recorded(/ub)  avgpu source
> 0   2018-10-21 08:03:55+00:00  1540109035            1           1  325000  7324            0.32           0.29   35.3   HFET
> 1   2018-10-21 08:04:18+00:00  1540109058            2           2  325000  7324            0.32           0.21   35.4   HFET
> 2   2018-10-21 08:04:42+00:00  1540109082            3           3  325000  7324            0.32           0.31   35.3   HFET
> 3   2018-10-21 08:05:05+00:00  1540109105            4           4  325000  7324            0.32           0.21   35.3   HFET
> 4   2018-10-21 08:05:28+00:00  1540109128            5           5  325000  7324            0.32           0.30   35.3   HFET
> ..                        ...         ...          ...         ...     ...   ...             ...            ...    ...    ...
> 366 2018-10-21 10:26:07+00:00  1540117567          367         367  325000  7324            0.26           0.25   28.8   HFET
> 367 2018-10-21 10:26:30+00:00  1540117590          368         368  325000  7324            0.26           0.25   28.8   HFET
> 368 2018-10-21 10:26:53+00:00  1540117613          369         369  325000  7324            0.26           0.25   28.8   HFET
> 369 2018-10-21 10:27:17+00:00  1540117637          370         370  325000  7324            0.26           0.25   28.8   HFET
> 370 2018-10-21 10:27:40+00:00  1540117660          371         371  325000  7324            0.26           0.21   28.8   HFET
> 
> [371 rows x 10 columns]
> ```
> {: .output}
{: .solution}


```python
(summary, data) = Query.lumi(fill=6666, beamstatus='STABLE BEAMS', type='pltzero', byls=True)
summary
data
```
{: .source}

> ## Output
> ```
> DEBUG: brilcalc lumi --output-style csv --tssec -f 6666 -b 'STABLE BEAMS' --type pltzero --byls
> Data tag                    19v3
> Norm tag                    None
> nfill                          1
> nrun                           6
> nls                         1966
> ncms                        1926
> totdelivered(/ub)    4.50713e+08
> totrecorded(/ub)     4.18091e+08
> dtype: object
>                             dt        time  deliveredLS  recordedLS     run  fill  delivered(/ub)  recorded(/ub)  avgpu  E(GeV)    beamstatus   source
> 0    2018-05-10 21:13:39+00:00  1525986819           32          32  316109  6666   366233.213965  358491.897262   44.0    6500  STABLE BEAMS  PLTZERO
> 1    2018-05-10 21:14:02+00:00  1525986842           33          33  316109  6666   366037.872369  123206.539042   43.9    6500  STABLE BEAMS  PLTZERO
> 2    2018-05-10 21:14:25+00:00  1525986865           34          34  316109  6666   365729.232190       0.000000   43.9    6500  STABLE BEAMS  PLTZERO
> 3    2018-05-10 21:14:49+00:00  1525986889           35          35  316109  6666   328216.224407       0.000000   39.4    6500  STABLE BEAMS  PLTZERO
> 4    2018-05-10 21:15:12+00:00  1525986912           36          36  316109  6666    74180.419333       0.000000    8.9    6500  STABLE BEAMS  PLTZERO
> ...                        ...         ...          ...         ...     ...   ...             ...            ...    ...     ...           ...      ...
> 1961 2018-05-11 09:54:54+00:00  1526032494         1576        1576  316114  6666   135914.146076  133960.675502   16.3    6500  STABLE BEAMS  PLTZERO
> 1962 2018-05-11 09:55:17+00:00  1526032517         1577        1577  316114  6666   135810.351646  133861.500315   16.3    6500  STABLE BEAMS  PLTZERO
> 1963 2018-05-11 09:55:40+00:00  1526032540         1578        1578  316114  6666   135627.336989  133677.464474   16.3    6500  STABLE BEAMS  PLTZERO
> 1964 2018-05-11 09:56:04+00:00  1526032564         1579        1579  316114  6666   135447.930495  133500.365030   16.3    6500  STABLE BEAMS  PLTZERO
> 1965 2018-05-11 09:56:27+00:00  1526032587         1580        1580  316114  6666   135538.498791  133592.922141   16.3    6500  STABLE BEAMS  PLTZERO
>·
> [1966 rows x 12 columns]
> ```
> {: .output}
{: .solution}

```python
Query.lumi(run=314848, beamstatus='STABLE BEAMS', xing=True, xingTr=0.5, expandBX=True)[1]
```
{: .source}

> ## Output
> ```
> DEBUG: brilcalc lumi --output-style csv --tssec -r 314848 -b 'STABLE BEAMS' --xing --xingTr 0.5
> INFO: BCID: [4, 451, 1201, 1501, 1786, 2101, 2451, 2801, 3118]
>                            dt        time  deliveredLS  ...  bx2451_recorded(/ub)  bx2801_recorded(/ub)  bx3118_recorded(/ub)
> 0   2018-04-21 21:16:22+00:00  1524345382          303  ...             98.747116             81.036247             85.137383
> 1   2018-04-21 21:16:46+00:00  1524345406          304  ...            148.928726            122.231300            128.472565
> 2   2018-04-21 21:17:09+00:00  1524345429          305  ...            164.264313            134.837982            141.743805
> 3   2018-04-21 21:17:32+00:00  1524345452          306  ...            164.194458            134.556137            141.515793
> 4   2018-04-21 21:17:56+00:00  1524345476          307  ...            163.825027            134.330048            141.284210
> ..                        ...         ...          ...  ...                   ...                   ...                   ...
> 435 2018-04-22 00:08:29+00:00  1524355709          746  ...             98.313850             78.557487             82.477425
> 436 2018-04-22 00:08:52+00:00  1524355732          747  ...            165.477814            132.100494            138.753906
> 437 2018-04-22 00:09:16+00:00  1524355756          748  ...            165.278717            132.042389            138.571884
> 438 2018-04-22 00:09:39+00:00  1524355779          749  ...            165.179626            131.935623            138.617996
> 439 2018-04-22 00:10:02+00:00  1524355802          750  ...            124.072205             98.972488            104.007950
> 
> [440 rows x 30 columns]
> ```
> {: .output}
{: .solution}


```python
Query.beam(begin='2018-07-01', end='2018 jul 31', beamstatus='stable beams', perFill=True)[1]
```
{: .source}

> ## Output
> ```
> DEBUG: brilcalc beam --output-style csv --tssec --begin '07/01/18 00:00:00' --end '07/31/18 00:00:00' -b 'stable beams'
> INFO:
> Data tag    19v3
>     fill                        dt        time  ...                                                run    intensity1    intensity2
> 0   6868 2018-07-01 00:00:15+00:00  1530403215  ...  [319018, 319018, 319018, 319018, 319018, 31901...  1.012031e+13  1.042060e+13
> 1   6874 2018-07-01 23:26:59+00:00  1530487619  ...  [319077, 319077, 319077, 319077, 319077, 31907...  1.660039e+14  1.681219e+14
> 2   6877 2018-07-02 08:06:42+00:00  1530518802  ...  [319097, 319097, 319097, 319097, 319097, 31909...  7.261122e+12  7.300276e+12
> 3   6879 2018-07-02 14:47:43+00:00  1530542863  ...  [319124, 319124, 319124, 319124, 319124, 31912...  2.144090e+13  2.148350e+13
> 4   6881 2018-07-03 05:08:46+00:00  1530594526  ...  [319159, 319159, 319159, 319159, 319159, 31915...  5.152460e+13  5.006465e+13
> 5   6882 2018-07-03 15:54:32+00:00  1530633272  ...  [319173, 319173, 319173, 319173, 319173, 31917...  4.922644e+13  5.008399e+13
> 6   6884 2018-07-04 10:20:57+00:00  1530699657  ...  [319189, 319189, 319189, 319189, 319189, 31918...  2.686615e+13  2.717161e+13
> 7   6885 2018-07-04 20:13:30+00:00  1530735210  ...  [319222, 319222, 319222, 319222, 319222, 31922...  5.751975e+13  5.697277e+13
> 8   6890 2018-07-05 12:09:24+00:00  1530792564  ...  [319254, 319254, 319254, 319254, 319254, 31925...  1.104024e+14  1.136937e+14
> 9   6891 2018-07-06 14:23:45+00:00  1530887025  ...  [319297, 319297, 319297, 319297, 319297, 31929...  1.129159e+14  1.132540e+14
> 10  6892 2018-07-07 00:42:20+00:00  1530924140  ...  [319310, 319310, 319310, 319310, 319310, 31931...  9.778030e+13  9.824706e+13
> 11  6901 2018-07-08 02:05:04+00:00  1531015504  ...  [319337, 319337, 319337, 319337, 319337, 31933...  8.299723e+13  8.554400e+13
> 12  6904 2018-07-08 19:52:32+00:00  1531079552  ...  [319347, 319347, 319347, 319347, 319347, 31934...  2.307476e+14  2.359878e+14
> 13  6909 2018-07-09 20:58:45+00:00  1531169925  ...  [319449, 319449, 319449, 319449, 319449, 31944...  2.013432e+14  2.040904e+14
> 14  6911 2018-07-11 09:09:58+00:00  1531300198  ...  [319486, 319486, 319486, 319486, 319486, 31948...  2.357316e+14  2.459484e+14
> 15  6912 2018-07-11 22:26:43+00:00  1531348003  ...  [319524, 319524, 319524, 319524, 319524, 31952...  2.187870e+14  2.304280e+14
> 16  6913 2018-07-12 18:29:04+00:00  1531420144  ...  [319557, 319557, 319557, 319557, 319557, 31955...  1.160668e+12  1.124557e+12
> 17  6919 2018-07-13 04:42:30+00:00  1531456950  ...  [319579, 319579, 319579, 319579, 319579, 31957...  2.078140e+14  2.145636e+14
> 18  6921 2018-07-14 14:05:05+00:00  1531577105  ...  [319625, 319625, 319625, 319625, 319625, 31962...  2.439112e+14  2.459997e+14
> 19  6923 2018-07-14 18:51:27+00:00  1531594287  ...  [319639, 319639, 319639, 319639, 319639, 31963...  2.111103e+14  2.233223e+14
> 20  6924 2018-07-15 07:23:18+00:00  1531639398  ...  [319656, 319656, 319656, 319656, 319656, 31965...  2.263233e+14  2.296885e+14
> 21  6925 2018-07-15 15:19:26+00:00  1531667966  ...  [319678, 319678, 319678, 319678, 319678, 31967...  2.429124e+14  2.497445e+14
> 22  6927 2018-07-15 22:27:18+00:00  1531693638  ...  [319687, 319687, 319687, 319687, 319687, 31968...  2.634214e+14  2.691051e+14
> 23  6929 2018-07-16 02:16:54+00:00  1531707414  ...  [319697, 319697, 319697, 319697, 319697, 31969...  9.206933e+13  9.604443e+13
> 24  6931 2018-07-16 15:38:18+00:00  1531755498  ...  [319756, 319756, 319756, 319756, 319756, 31975...  2.003244e+14  2.140037e+14
> 25  6939 2018-07-17 22:27:06+00:00  1531866426  ...  [319840, 319840, 319840, 319840, 319840, 31984...  9.331841e+13  9.845540e+13
> 26  6940 2018-07-18 04:01:43+00:00  1531886503  ...  [319847, 319847, 319847, 319847, 319847, 31984...  2.284896e+14  2.373708e+14
> 27  6942 2018-07-19 02:38:42+00:00  1531967922  ...  [319907, 319907, 319907, 319907, 319908, 31990...  2.084886e+14  2.197406e+14
> 28  6944 2018-07-19 19:58:49+00:00  1532030329  ...  [319941, 319941, 319941, 319941, 319941, 31994...  2.575465e+14  2.579312e+14
> 29  6946 2018-07-20 02:44:44+00:00  1532054684  ...  [319950, 319950, 319950, 319950, 319950, 31995...  2.588241e+14  2.623835e+14
> 30  6953 2018-07-20 15:48:05+00:00  1532101685  ...  [319991, 319991, 319991, 319991, 319991, 31999...  2.009583e+14  2.102614e+14
> 31  6956 2018-07-21 08:16:45+00:00  1532161005  ...  [320002, 320002, 320002, 320002, 320002, 32000...  2.106681e+14  2.148840e+14
> 32  6957 2018-07-21 21:32:17+00:00  1532208737  ...  [320023, 320023, 320023, 320023, 320023, 32002...  2.327795e+14  2.407821e+14
> 33  6960 2018-07-22 07:08:17+00:00  1532243297  ...  [320038, 320038, 320038, 320038, 320038, 32003...  2.222567e+14  2.303848e+14
> 34  6961 2018-07-22 18:31:54+00:00  1532284314  ...  [320058, 320058, 320058, 320058, 320058, 32005...  2.220188e+14  2.352438e+14
> 35  6998 2018-07-30 08:28:12+00:00  1532939292  ...  [320500, 320500, 320500, 320500, 320500, 32050...  2.694008e+11  2.482165e+11
>
> [36 rows x 7 columns]
> ```
> {: .output}
{: .solution}

```python
Query.trg(run=325000, prescale=True, hltpath='HLT_ZeroBias_v6')
```
{: .source}

> ## Output
> ```
> DEBUG: brilcalc trg --output-style csv -r 325000 --prescale --hltpath HLT_ZeroBias_v6
>       run cmsls prescidx totprescval    hltpath/prescval logic     l1bit/prescval
> 0  325000     1        5      929812  HLT_ZeroBias_v6/52   ONE  L1_ZeroBias/17881
> 1  325000   261        6      929812  HLT_ZeroBias_v6/52   ONE  L1_ZeroBias/17881
> ```
> {: .output}
{: .solution}
