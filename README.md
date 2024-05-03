# Tölvera

[Tölvera](https://tolvera.is) is a library for exploring musical performance with artificial life (ALife) and self-organising systems. The word is an Icelandic [kenning](https://en.wikipedia.org/wiki/Kenning):

- Tölva = computer, from tala (number) + völva (prophetess)
- Vera = being
- Tölvera = number being

Tölvera is written in [Taichi](https://www.taichi-lang.org/), a domain-specific language embedded in Python.

This is experimental software and everything is currently subject to change.

Join us on the Tölvera [Discord](https://discord.gg/ER7tWds9vM).

## Showcase

[Visit the YouTube Playlist](https://www.youtube.com/embed/ahSXjnYHZLU?&list=PL8bdQleKUA1vNez5gw-pfQB21Q1-vHn3x) (if you'd like to add a video, please get in touch).

![type:video](https://www.youtube.com/embed/ahSXjnYHZLU?&list=PL8bdQleKUA1vNez5gw-pfQB21Q1-vHn3x)

<!-- [![](assets/images/tolvera.jpg)](https://www.youtube.com/watch?v=ahSXjnYHZLU&list=PL8bdQleKUA1vNez5gw-pfQB21Q1-vHn3x&pp=gAQBiAQB) -->

## Features

- `tv.v`: a collection of "vera" (beings) including Move, Flock, Slime and Swarm, with more being continuously added. Vera can be combined and composed in various ways.
- `tv.p`: extensible particle system. Particles are divided into multiple species, where each species has a unique relationship with every other species, including itself
- `tv.s`: n-dimensional state structures that can be used by "vera", including built-in OSC and IML creation (see below).
- `tv.px`: drawing library including various shapes and blend modes, styled similarly to p5.js etc.
- `tv.osc`: Open Sound Control (OSC) via [iipyper](https://github.com/Intelligent-Instruments-Lab/iipyper), including automated export of OSC schemas to JSON, XML, Pure Data (Pd), Max/MSP (SuperCollider TBC).
- `tv.iml`: Interactive Machine Learning via [anguilla](https://github.com/Intelligent-Instruments-Lab/anguilla).
- `tv.ti`: Taichi-based simulation and rendering engine. Can be run "headless" (without graphics).
- `tv.cv`: computer vision integration based on OpenCV and Mediapipe.

## Examples

Examples can be found at [iil-examples/tolvera](https://github.com/Intelligent-Instruments-Lab/iil-examples/tree/main/tolvera).
When run as a script, Tölvera program looks like this:

```py
from tolvera import Tolvera, run

def main(**kwargs):
    tv = Tolvera(**kwargs)

    @tv.render
    def _():
        return tv.px

if __name__ == '__main__':
    run(main)
```

## Install

Taichi [supports numerous operating systems and backends](https://docs.taichi-lang.org/docs/hello_world#supported-systems-and-backends).
If you plan on using Vulkan for graphics (recommended for macOS), you may need to [install the Vulkan SDK](https://docs.taichi-lang.org/docs/hello_world#supported-systems-and-backends) first and restart your machine.
```

Tölvera is [registered on PyPI](https://pypi.org/project/tolvera) and can be installed via a Python package manager such as `pip`:

```sh
pip install tolvera
```

## Develop

Fork/clone this repository and install the package with [`poetry`](https://python-poetry.org/):

```sh
git clone https://github.com/Intelligent-Instruments-Lab/tolvera # (or clone your own fork)
cd tolvera
poetry install
```

## Known Issues & Limitations

- Tölvera currently [does not support Python 3.12 and above](https://github.com/taichi-dev/taichi/issues/8365) - a Python 3.11 installation is recommended.
This can be created in the following way using [miniconda](https://docs.anaconda.com/free/miniconda/index.html):
```sh
conda create -n tolvera python=3.11
conda activate tolvera
```
- Tölvera does not support Intel-based Apple devices (due to [`anguilla`](https://github.com/Intelligent-Instruments-Lab/anguilla)'s FAISS dependency, and Mediapipe not supporting Intel Macs).
- On macOS, [an OpenMP issue](https://github.com/pytorch/pytorch/issues/78490) may prevent Tölvera programs from running, which can be addressed by adding the following environment variable:
```sh
export KMP_DUPLICATE_LIB_OK=TRUE
```
- Sonification via [SignalFlow](https://signalflow.dev) does not work on Windows.
- Mediapipe versions [may need to be downgraded](https://github.com/google/mediapipe/issues/5168) in order to work on macOS and Windows.

## Contribute

We welcome [Pull Requests](https://github.com/Intelligent-Instruments-Lab/tolvera/pulls) across all areas of the project:

- Addressing [Issues](https://github.com/Intelligent-Instruments-Lab/tolvera/issues)
- Adding features (see [Issues](https://github.com/Intelligent-Instruments-Lab/tolvera/issues) and [Discussion](https://github.com/Intelligent-Instruments-Lab/tolvera/discussion))
- [Examples](https://github.com/Intelligent-Instruments-Lab/iil-examples/tolvera)
- [Tests](https://github.com/Intelligent-Instruments-Lab/tolvera/tests)
- [Documentation](https://github.com/Intelligent-Instruments-Lab/tolvera/docs)

## Community

To discuss Tölvera with developers and other users:

- Use GitHub [Issues](https://github.com/Intelligent-Instruments-Lab/tolvera/issues) to report bugs and make specific feature requests.
- Use GitHub [Discussions](https://github.com/Intelligent-Instruments-Lab/tolvera/discussions) to share ideas and ask questions.
- Use [Discord](https://discord.gg/ER7tWds9vM) for further support, sharing your work, and general chat.

Across the project, we follow the [Berlin Code of Conduct](https://berlincodeofconduct.org/). 
Please get in touch if you experience or witness any conduct issues.

## Roadmap

See [Discussion](https://github.com/Intelligent-Instruments-Lab/tolvera/discussion).

## Citing

Tölvera is being written about and used in a number of contexts (see [references.bib](https://github.com/Intelligent-Instruments-Lab/tolvera/blob/main/references.bib)).
The current canonical citation is:

```bibtex
@inproceedings{armitageTolveraComposingBasal2024,
  title = {T{\"o}lvera: {{Composing With Basal Agencies}}},
  booktitle = {Proc. {{New Interfaces}} for {{Musical Expression}}},
  author = {Armitage, Jack and Shepardson, Victor and Magnusson, Thor},
  year = {2024},
  address = {Utrecht, NL},
}
```

## Inspiration

- [SwissGL](https://swiss.gl)
- [Lenia](https://chakazul.github.io/lenia.html)
- Particle Life (attributed to various, see for example [Clusters](https://www.ventrella.com/Clusters/))
- [Journey to the Microcosmos](https://www.youtube.com/@journeytomicro)
- [Complexity Explorables](https://www.complexity-explorables.org/)

## Contact

`tolvera` is developed by the [Intelligent Instruments Lab](https://iil.is/about). Get in touch to [collaborate](https://iil.is/collaborate):

 ◦ <a href="https://iil.is" target="_blank" title="Intelligent Instrumets Lab">iil.is</a> ◦ 
<a href="https://facebook.com/intelligentinstrumentslab" target="_blank" title="facebook.com">Facebook</a> ◦ 
<a href="https://instagram.com/intelligentinstruments" target="_blank" title="instagram.com">Instagram</a> ◦ 
<a href="https://x.com/_iil_is" target="_blank" title="x.com">X (Twitter)</a> ◦ 
<a href="https://youtube.com/@IntelligentInstruments" target="_blank" title="youtube.com">YouTube</a> ◦ 
<a href="https://discord.gg/fY9GYMebtJ" target="_blank" title="discord.gg">Discord</a> ◦ 
<a href="https://github.com/intelligent-instruments-lab" target="_blank" title="github.com">GitHub</a> ◦ 
<a href="https://www.linkedin.com/company/intelligent-instruments-lab" target="_blank" title="www.linkedin.com">LinkedIn</a> ◦ 
<a href="mailto:iil@lhi.is" target="_blank" title="">Email</a> ◦ 

## Funding

The Intelligent Instruments project (INTENT) is funded by the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (Grant agreement No. 101001848).
