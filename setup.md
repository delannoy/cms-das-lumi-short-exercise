---
title: Setup
---


# Installation of [BRIL Work Suite](https://cmslumi.web.cern.ch/#prerequisite) (brilws)

> ## Important
> **This exercise is meant to be run from lxplus.cern.ch.**
{: .callout}

<!--
## Brilconda3 (centrally-installed Python3 virtual environment)
Brilconda3 is a "centrally-installed" (available via [cvmfs](https://cvmfs.readthedocs.io/en/stable/)) Python3 [virtual environment](https://realpython.com/python-virtual-environments-a-primer/)

```bash
ssh lxplus
[[ "${SHELL##*/}" != 'bash' ]] && bash # spawn a bash shell if not in a bash shell
export PATH="${HOME}/.local/bin:/cvmfs/cms-bril.cern.ch/brilconda3/bin:${PATH}" # prepend prerequisites to $PATH
command -v python3
python3 --version
```
{: .source}
```
/cvmfs/cms-bril.cern.ch/brilconda3/bin/python3
Python 3.7.6
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
/cvmfs/cms-bril.cern.ch/brilconda3/bin/python3 -m pip install --user --upgrade brilws
```
{: .source}
```
Processing ./.cache/pip/wheels/c8/76/af/24ad46bc1e6d1d927aba8c36e194f0e7514533b92455d29394/brilws-3.6.8-cp37-none-any.whl
Installing collected packages: brilws
Successfully installed brilws-3.6.8
```
{: .output}

### Verify `brilws` pip info
```bash
/cvmfs/cms-bril.cern.ch/brilconda3/bin/python3 -m pip show brilws
```
{: .source}
```
Name: brilws
Version: 3.6.8
Summary: bril worksuite
Home-page: https://github.com/xiezhen/brilws
Author: Zhen Xie
Author-email: UNKNOWN
License: MIT
Location: "${HOME}/.local/lib/python3.7/site-packages"
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
3.6.8
```
{: .output}

> ## Troubleshooting `brilws` and `brilcalc`
> In case of trouble, `brilws` can be uninstalled and reinstalled:
> ```bash
> /cvmfs/cms-bril.cern.ch/brilconda3/bin/python3 -m pip uninstall -y brilws
> /cvmfs/cms-bril.cern.ch/brilconda3/bin/python3 -m pip install --user --upgrade brilws
> ~/.local/bin/brilcalc --version
> ```
> {: .source}
> If this doesn't work, the `"${HOME}/.local/"` area may need to be cleaned up by hand:
> ```bash
> rm -iv "${HOME}/.local/bin/bril"*
> rm -rv "${HOME}/.local/lib/python3.7/site-packages/brilws"*
> /cvmfs/cms-bril.cern.ch/brilconda3/bin/python3 -m pip install --user --upgrade brilws
> ~/.local/bin/brilcalc --version
> ```
> {: .source}
> If things are still broken, a "private" brilconda3-based virtual environment can be set up (see ["bonus Python tips"](https://delannoy.github.io/cms-das-lumi-short-exercise/setup.html#bonus-python-hints) below):
> ```bash
> /cvmfs/cms-bril.cern.ch/brilconda3/bin/python3 -m venv --system-site-packages "${HOME}/.local/brilconda3"
> source "${HOME}/.local/brilconda3/bin/activate"
> python3 -m pip install --upgrade brilws
> ~/.local/brilconda3/bin/brilcalc --version
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

> ## Bonus Python hints!
> Note that the brilconda3 virtual environment offers a faily recent version of Python (3.7) and batteries are included (lots of third-party Python packages)!
> You might consider defining a `brilconda3` alias in your `~/.bashrc` to prepend brilconda3 to the `$PATH` environment variable:
> ```bash
> echo 'alias brilconda3="[[ -d /cvmfs/cms-bril.cern.ch/brilconda3 ]] && export PATH=/cvmfs/cms-bril.cern.ch/brilconda3/bin:${PATH}"' >> "${HOME}/.bashrc"
> ```
> {: .source}
> You might also find it useful to set up a brilconda3-based Python3 virtual environment (each virtual environment lives "portably" inside a directory; it includes its own Python binary and can have an independent set of Python packages).
The `--system-site-packages` flag gives your virtual environment access to the brilconda3 packages.
> ```bash
> /cvmfs/cms-bril.cern.ch/brilconda3/bin/python3 -m venv --system-site-packages "${HOME}/.local/brilconda3"
> source "${HOME}/.local/brilconda3/bin/activate"
> command -v python3
> python3 -m pip freeze | xargs
> ```
> {: .source}
> ```
> "${HOME}/.local/brilconda3/bin/python3"
> beautifulsoup4==4.9.0 brilws==3.6.9 certifi==2020.4.5.1 cffi==1.14.0 chardet==3.0.4 cheroot==8.3.0 CherryPy==16.0.2 click==7.1.2 conda==4.5.13 conda-build==3.18.10 conda-package-handling==1.7.0 contextlib2==0.5.5 cryptography==2.9.2 cx-Oracle==7.2.3 cycler==0.10.0 Cython==0.29.17 docopt==0.6.2 filelock==3.0.12 Flask==1.1.2 Flask-SocketIO==4.3.0 glob2==0.7 h5py==2.10.0 idna==2.9 itsdangerous==1.1.0 jaraco.functools==3.0.1 Jinja2==2.11.2 kiwisolver==1.2.0 libarchive-c==2.9 MarkupSafe==1.1.1 matplotlib==3.1.3 mock==4.0.2 more-itertools==8.3.0 numexpr==2.7.1 numpy==1.18.1 pandas==1.0.3 pkginfo==1.5.0.1 portend==2.5 prettytable==0.7.2 psutil==5.7.0 pycosat==0.6.3 pycparser==2.20 pyOpenSSL==19.1.0 pyparsing==2.4.7 PySocks==1.7.1 python-dateutil==2.8.1 python-engineio==3.11.2 python-socketio==4.5.1 pytz==2020.1 PyYAML==5.3.1 pyzmq==18.1.1 requests==2.23.0 ruamel-yaml==0.15.87 schema==0.7.2 scipy==1.4.1 sip==4.19.13 six==1.14.0 soupsieve==2.0.1 SQLAlchemy==1.3.16 tables==3.6.1 tempora==3.0.0 tornado==6.0.4 tqdm==4.46.0 urllib3==1.25.8 Werkzeug==1.0.1
> ```
> {: .output}
{: .solution}

{% include links.md %}
