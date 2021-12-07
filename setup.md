---
title: Setup
---


# Installation of [BRIL Work Suite](https://cmslumi.web.cern.ch/#prerequisite) (brilws)


## Set up brilconda3 (centrally-installed python3 virtual environment):
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

## Install brilws
The `--user` flag will install brilws binaries to `"${HOME}/.local/bin/"` and libraries to `"${HOME}/.local/lib/"`
> ## Important!
> It's always a good idea to include the `--upgrade` flag.
> **If your brilcalc installation stops working, running the command below will fix it in 99% of cases.**
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

### Verify brilws pip info
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

### Check brilcalc installation location
```bash
command -v brilcalc
```
{: .source}
```
"${HOME}/.local/bin/brilcalc"
```
{: .output}

### Check brilcalc version
```bash
brilcalc --version
```
{: .source}
```
3.6.8
```
{: .output}

> ## Troubleshooting brilws and brilcalc
> In case of trouble, brilws can be uninstalled and reinstalled:
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
> If thigs are still broken, a brilconda3-based virtual environment could be set up (see ["bonus python tips"](https://delannoy.github.io/cms-das-lumi-short-exercise/setup.html#bonus-python-hints) below):
> ```bash
> /cvmfs/cms-bril.cern.ch/brilconda3/bin/python3 -m venv --system-site-packages "${HOME}/.local/brilconda3"
> source "${HOME}/.local/brilconda3/bin/activate"
> python3 -m pip install --upgrade brilws
> ~/.local/brilconda3/bin/brilcalc --version
> ```
> {: .source}
{: .solution}

> ## Bonus python hints!
> Note that the brilconda3 virtual environment offers a faily recent version of python (3.7) and batteries are included (lots of third-party python packages)!
> You might consider defining a `brilconda3` alias in your `~/.bashrc` to prepend brilconda3 to the `$PATH` environment variable:
> ```bash
> echo 'alias brilconda3="[[ -d /cvmfs/cms-bril.cern.ch/brilconda3 ]] && export PATH=/cvmfs/cms-bril.cern.ch/brilconda3/bin:${PATH}"' >> "${HOME}/.bashrc"
> ```
> {: .source}
> You might also find it useful to set up a brilconda3-based python3 virtual environment. The `--system-site-packages` flag gives your virtual environment access to the brilconda3 packages.
> ```bash
> /cvmfs/cms-bril.cern.ch/brilconda3/bin/python3 -m venv --system-site-packages "${HOME}/.local/brilconda3"
> source "${HOME}/.local/brilconda3/bin/activate"
> command -v python3
> python3 -m pip freeze | awk 'BEGIN{FS="="}; {printf("%s ", $1)} END{print}'
> ```
> {: .source}
> ```
> "${HOME}/.local/brilconda3/bin/python3"
> beautifulsoup4 brilws certifi cffi chardet cheroot CherryPy click conda conda-build conda-package-handling contextlib2 cryptography cx-Oracle cycler Cython docopt filelock Flask Flask-SocketIO glob2 h5py idna itsdangerous jaraco.functools Jinja2 kiwisolver libarchive-c MarkupSafe matplotlib mock more-itertools numexpr numpy pandas pkginfo portend prettytable psutil pycosat pycparser pyOpenSSL pyparsing PySocks python-dateutil python-engineio python-socketio pytz PyYAML pyzmq requests ruamel-yaml schema scipy sip six soupsieve SQLAlchemy tables tempora tornado tqdm urllib3 Werkzeug
> ```
> {: .output}
{: .solution}

{% include links.md %}
