# Phy Analysis

**phy** is an open-source Python library providing a graphical user interface for visualization and manual curation of large-scale electrophysiological data. It is optimized for high-density multielectrode arrays containing hundreds to thousands of recording sites, especially Neuropixels recordings.

> **Current release:** `phy 2.1.0` is a maintenance-focused release that improves installation and GUI reliability on current systems. See the release notes for details and compatibility notes.

## Current status

As of July 2026, `phy 2.1.0` is the current stable release for the 2.x line.

The main goals of this release are:

* dependency and packaging modernization
* replacing a fragile legacy web-based GUI component with a Qt-native implementation
* improving display reliability on modern systems
* incorporating fixes identified during release-candidate testing

Dataset formats are unchanged. Some plugins that relied on internal HTML or web-based GUI components may need updates.

Please report any issues or compatibility regressions on GitHub issues.

## Supported workflows

phy currently provides three main entry points:

* **Template GUI**: the main and recommended workflow for datasets sorted with KiloSort and Spyking Circus
* **Kwik GUI**: a legacy workflow for datasets sorted with klusta and klustakwik2
* **Trace GUI**: an experimental raw-data viewer for opening continuous electrophysiology recordings directly

Current testing and maintenance work is focused on modern Linux, macOS, and Windows environments. Linux is still the best-covered platform.

## Installation

The recommended installation uses
`uv`, which installs
phy and its Python dependencies in an isolated environment:

```bash
uv tool install --python 3.12 phy
phy --version
```

This installs the GUI runtime dependencies as part of the main package.

The legacy Kwik GUI needs a regular virtual environment because one of its
dependencies requires special build handling. See the installation guide for
the tested `uv` commands.

See the installation guide
for instructions to install `uv`, legacy Kwik support, a `venv`/pip alternative,
source checkouts, and installation verification.

## Quick start

Open the Template GUI on a spike sorting output directory containing `params.py`:

```bash
cd path/to/my/spikesorting/output
phy template-gui params.py
```

Other useful commands:

```bash
phy template-describe params.py
phy kwik-gui path/to/file.kwik
phy trace-gui path/to/raw.bin --sample-rate 30000 --dtype int16 --n-channels 384
```

Before curating your own data, review the
dataset requirements and follow
the first-ten-minutes guide.

## Available GUIs and commands

### Template GUI

Use the Template GUI for current template-based workflows such as KiloSort and Spyking Circus.

```bash
phy template-gui params.py
```

To inspect a dataset from the terminal without launching the GUI:

```bash
phy template-describe params.py
```

### Kwik GUI

The Kwik GUI is still available for legacy kwik datasets, but it is no longer the primary workflow.

```bash
phy kwik-gui path/to/file.kwik
```

### Trace GUI

The Trace GUI is still experimental and opens raw electrophysiology recordings directly.

```bash
phy trace-gui path/to/raw.bin --sample-rate 30000 --dtype int16 --n-channels 384
```

## Running phy from Python

You can also launch phy from Python or IPython, which can be useful for debugging or profiling:

```python
from phy.apps.template import template_gui

template_gui("params.py")
```

## Developer setup

For a fresh editable installation using the latest commits of both phylib and phy:

```bash
mkdir phy-source
cd phy-source

git clone https://github.com/cortex-lab/phylib.git
git clone https://github.com/cortex-lab/phy.git

cd phy
uv sync --dev
uv pip install --editable ../phylib
```

Windows PowerShell instructions, update commands, and verification of the exact commits are in the
source installation guide.

## Documentation and help

* Documentation home
* Installation
* Preparing a dataset
* First-ten-minutes quickstart
* Using the GUI
* Performance and spike sampling
* Changelog
* Release notes
* Troubleshooting
* GitHub issues
* Mailing list
* Code of Conduct

## Credits

**phy** is developed and maintained by Cyrille Rossant.

* International Brain Laboratory
* Cortex Lab (UCL) (Kenneth Harris and Matteo Carandini)

Contributors to the repository are:

* Maxime Beau
* Alessio Buccino
* Thad Czuba
* Michael Economo
* Einsied
* Cedric Gestes
* Yaroslav Halchenko
* Max Hunter
* Shabnam Kadir
* Zach McKenzie
* Sam Minkowicz
* Christopher Nolan
* Jesús Peñaloza
* Luke Shaheen
* Martin Spacek
* Nick Steinmetz
* Olivier Winter
* szapp
* ycanerol

## Repository Maintainer

Ajay Verma

## Attribution

This repository is based on an open-source project distributed under its original license. The original work is by the authors of cortex-lab/phy.

All original copyright notices and the LICENSE file are preserved. This copy adds only repository-level metadata; the source code remains the work of the original authors.
