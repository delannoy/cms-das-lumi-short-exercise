---
title: Setup
---


# Install the [BRIL Work Suite](https://cmslumi.web.cern.ch/#prerequisite)


## Setup brilconda3 (python3 virtual environment):
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


## Uninstall brilws if already installed
```bash
python3 -m pip uninstall -y brilws
```
{: .source}

### If brilws is not installed:
```
WARNING: Skipping brilws as it is not installed.
```
{: .output}

### If brilws is already installed:
```
Found existing installation: brilws 3.6.8
Uninstalling brilws-3.6.8:
  Successfully uninstalled brilws-3.6.8
```
{: .output}


## Install brilws
```bash
python3 -m pip install --user brilws # pip will install brilws binaries to "${HOME}/.local/bin/" and libraries to "${HOME}/.local/lib/"
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
python3 -m pip show brilws
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
Location: "${HOME}"/.local/lib/python3.7/site-packages
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
"${HOME}"/.local/bin/brilcalc
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

> ## python hints
> Note that the brilconda3 virtual environment offers a faily recent version of python3 (3.7) and batteries are included (lots of third-party python packages)!
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
