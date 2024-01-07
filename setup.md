---
title: Setup
---


# Installation of [BRIL Work Suite](https://cmslumi.web.cern.ch/#prerequisite) (brilws)

> ## Important
> **This exercise is meant to be run from lxplus.cern.ch.**
{: .callout}

<!--
## Brilconda (centrally-installed Python3 virtual environment)
Brilconda is a "centrally-installed" (available via [cvmfs](https://cvmfs.readthedocs.io/en/stable/)) Python3 [virtual environment](https://realpython.com/python-virtual-environments-a-primer/)

```bash
ssh lxplus
[[ "${SHELL##*/}" != 'bash' ]] && bash # spawn a bash shell if not in a bash shell
export PATH="${HOME}/.local/bin:/cvmfs/cms-bril.cern.ch/brilconda310/bin:${PATH}" # prepend prerequisites to $PATH
command -v python3
python3 --version
```
{: .source}
```
/cvmfs/cms-bril.cern.ch/brilconda310/bin/python3
Python 3.10.12
```
{: .output}
-->


## Install `brilws`
The `--user` flag will install `brilws` binaries to `"${HOME}/.local/bin/"` and libraries to `"${HOME}/.local/lib/"`
> ## Important!
> It's always a good idea to include the `--upgrade` flag.\
> **If your `brilcalc` installation stops working, running the command below will fix it in 99% of cases.**
{: .checklist}

```bash
/cvmfs/cms-bril.cern.ch/brilconda310/bin/python3 -m pip install --user --upgrade brilws
```
{: .source}
```
Processing ./.cache/pip/wheels/c8/76/af/24ad46bc1e6d1d927aba8c36e194f0e7514533b92455d29394/brilws-3.6.8-cp37-none-any.whl
Collecting brilws
  Downloading brilws-3.8.2.tar.gz (54 kB)
  Preparing metadata (setup.py) ... done
Building wheels for collected packages: brilws
  Building wheel for brilws (setup.py) ... done
  Created wheel for brilws: filename=brilws-3.8.2-py3-none-any.whl size=64908 sha256=3cf887498de2f01b12cba517811ff391dc33054ed21efb1b4a38dff8dc17925c
  Stored in directory: /afs/cern.ch/user/a/adelanno/.cache/pip/wheels/8d/c0/30/a9ece603f27c2a641e8bf13e78de50560ab1ebfdb2d17252d9
Successfully built brilws
Installing collected packages: brilws
Successfully installed brilws-3.8.2
```
{: .output}

### Verify `brilws` pip info
```bash
/cvmfs/cms-bril.cern.ch/brilconda310/bin/python3 -m pip show brilws
```
{: .source}
```
Name: brilws
Version: 3.8.2
Summary: bril worksuite
Home-page: https://github.com/xiezhen/brilws
Author: Zhen Xie
Author-email:
License: MIT
Location: /afs/cern.ch/user/a/adelanno/.local/lib/python3.10/site-packages
Requires:
Required-by:
```
{: .output}

### Check `brilcalc` installation location
```bash
command -v brilcalc
```
{: .source}
```
"${HOME}/.local/bin/brilcalc"
```
{: .output}

### Check `brilcalc` version
```bash
brilcalc --version
```
{: .source}
```
3.8.2
```
{: .output}

> ## Troubleshooting `brilws` and `brilcalc`
> In case of trouble, `brilws` can be uninstalled and reinstalled:
> ```bash
> /cvmfs/cms-bril.cern.ch/brilconda310/bin/python3 -m pip uninstall -y brilws
> /cvmfs/cms-bril.cern.ch/brilconda310/bin/python3 -m pip install --user --upgrade brilws
> ~/.local/bin/brilcalc --version
> ```
> {: .source}
> If this doesn't work, the `"${HOME}/.local/"` area may need to be cleaned up by hand:
> ```bash
> rm -iv "${HOME}/.local/bin/bril"*
> rm -rv "${HOME}/.local/lib/python"*"/site-packages/brilws"*
> /cvmfs/cms-bril.cern.ch/brilconda310/bin/python3 -m pip install --user --upgrade brilws
> ~/.local/bin/brilcalc --version
> ```
> {: .source}
> If things are still broken, a "private" brilconda3-based virtual environment can be set up (see ["bonus Python tips"](https://delannoy.github.io/cms-das-lumi-short-exercise/setup.html#bonus-python-hints) below):
> ```bash
> /cvmfs/cms-bril.cern.ch/brilconda310/bin/python3 -m venv --system-site-packages "${HOME}/.local/brilconda310"
> source "${HOME}/.local/brilconda310/bin/activate"
> python3 -m pip install --upgrade brilws
> ~/.local/brilconda310/bin/brilcalc --version
> ```
> {: .source}
{: .solution}

> ## Set Up `brilcalc` from Container Image in `lxplus`
> On `lxplus`, a container image is provided to give a simple access to the `brilcalc` software for all users.
> This implementation is in an **experimental stage**.
> It should work without issues, in some cases, it will print warnings regarding the use of outdated python functions (these can be ignored).
> In case of problems or inconsistent results, `brilcalc` should be used via setting up the `brilconda` environment, as described above.
> Feedback about the container image is welcome, and can be sent to the LUM POG conveners.
> ```bash
> source /cvmfs/cms-bril.cern.ch/cms-lumi-pog/brilws-docker/brilws-env
> ```
> {: .source}
> The first time the command is run on a node, it can take a bit longer because the files first have to be downloaded in cvmfs.
{: .solution}

{% include links.md %}
