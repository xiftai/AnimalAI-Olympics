# Animal-AI Olympics

## Overview

Welcome to the repository for the Animal-AI Olympics competition where you will find all the code needed to compete in 
this new challenge. Note that for the moment this repo contains **only the training environment** (v0.1) that will be used for the competition and **does not contain any competition tests or information for entering**. If everything goes well the competition will be live on June 30th. Until then we will be continually updating with bug fixes and small changes to environment. However, the general structure will stay the same so it's not too early to start working with the environment. For more information on the competition itself and to stay updated with any developments, head to the [Competition Website](http://www.animalaiolympics.com/) and follow [@MacroPhilosophy](https://twitter.com/MacroPhilosophy) and [@BenBeyret](https://twitter.com/BenBeyret) on twitter.

The environment contains an agent enclosed in a fixed sized arena. Objects can spawn in this arena, including positive and negative rewards (green, yellow and red spheres). All of the hidden tests that will appear in the competition are made using the objects in the training environment. We have provided some sample environment configurations that should be useful for training, but part of the challenge will be experimenting and designing new configurations.

The goal of this first release is to **seek feedback from the community** as well as to provide the environment for research prior to the launch of the competition itself. The competition version of the environment will be similar to this one, however we are open to suggestion (for minor changes) and especially bug reports! Head over to the [issues page](https://github.com/beyretb/AnimalAI-Olympics/issues) and open a ticket using the `suggestion` or `bug` labels 
respectively.

To get started install the requirements below, and then follow the [Quick Start Guide](documentation/quickstart.md). 
A more in depth documentation <!--, including a primer on animal cognition,--> can be found on the 
[Documentation Page](documentation/README.md).

## Development Blog

You can read the development blog [here](https://mdcrosby.com/blog). It covers further details about the competition as well as part of the development process.

1. [Why Animal-AI?](https://mdcrosby.com/blog/animalai1.html)

2. [The Syllabus (Part 1)](https://mdcrosby.com/blog/animalai2.html)

## Requirements

The Animal-AI package works on most platforms. <!--, for cloud engines check out [this cloud documentation](documentation/cloud.md).-->

First of all your will need `python3.6` installed. You will find a list of requirements in the `requirements*.txt` files. 
Using `pip` you can run:

on Linux and mac:
```
pip install -r requirementsOthers.txt
```

on windows:
```
pip install -r requirementsWindows.txt
```
**Note:** `python3.6` is required to install `tensorflow>=1.7,<1.8` which is only used for the training script we provide as an example. Should you wish to use another version of python you can remove the first line from the requirement files. You will still be able to use the `visualizeArena.py` script, but not the `train.py` one.  

Finally download the environment for your system:

| OS | Environment link |
| --- | --- |
| Linux |  [download v0.4](https://www.doc.ic.ac.uk/~bb1010/animalAI/env_linux_v0.4.zip) |
| MacOS |  [download v0.4](https://www.doc.ic.ac.uk/~bb1010/animalAI/env_mac_v0.4.zip) |
| Windows | [download v0.4](https://www.doc.ic.ac.uk/~bb1010/animalAI/env_windows_v0.4.zip)  |

You can now unzip the content of the archive to the `env` folder and you're ready to go! Make sure the executable 
`AnimalAI.*` is in `env/`. On linux you may have to make the file executable by running `chmod +x env/AnimalAI.x86_64`. 
Head over to [Quick Start Guide](documentation/quickstart.md) for a quick overview of how the environment works.

## Manual Control

If you launch the environment directly from the executable or through the VisualizeArena script it will launch in player 
mode. Here you can control the agent with the following:

| Keyboard Key  | Action    |
| --- | --- |
| W   | move agent forwards |
| S   | move agent backwards|
| A   | turn agent left     |
| D   | turn agent right    |
| C   | switch camera       |
| R   | reset environment   |

**Note**: on some platforms, playing manually in full screen makes the environment slow, keep the environment in window 
mode for better performance.

## Competition Tests

We will be releasing further details about the tests in the competition over the coming weeks. The tests will be split into multiple categories from the very simple (e.g. **food retrieval**, **preferences**, and **basic obstacles**) to the more complex (e.g. **working memory**, **spatial memory**, **object permanence**, and **object manipulation**). For now we have included multiple example config files that each relate to a different category. As we release further details we will also specify the rules for the type of tests that can appear in each category. Note that the example config files are just simple examples to be used as a guide. An agent that solves even all of these perfectly may still not be able to solve all the tests in the categories but it would be off to a very good start.

## Citing

For now please cite the [Nature: Machine Intelligence piece](https://rdcu.be/bBCQt): 

Crosby, M., Beyret, B., Halina M. [The Animal-AI Olympics](https://www.nature.com/articles/s42256-019-0050-3) Nature Machine Intelligence 1 (5) p257 2019.

## Unity ML-Agents

The Animal-AI Olympics was built using [Unity's ML-Agents Toolkit.](https://github.com/Unity-Technologies/ml-agents)

The Python library located in [animalai](animalai) is almost identical to 
[ml-agents v0.7](https://github.com/Unity-Technologies/ml-agents/tree/master/ml-agents-envs). We only added the possibility to change the configuration of arenas between episodes. The documentation for ML-Agents can be found [here](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Python-API.md).

Juliani, A., Berges, V., Vckay, E., Gao, Y., Henry, H., Mattar, M., Lange, D. (2018). [Unity: A General Platform for 
Intelligent Agents.](https://arxiv.org/abs/1809.02627) *arXiv preprint arXiv:1809.02627*

## Known Bugs

Occasionally will spawn an empty arena in play mode. Temporary fix: just press R to respawn.

Occasional slow frame rates in play mode. Temporary fix: reduce screen size. 

## TODO

- [ ] Offer a gym wrapper for training
- [ ] Add protobuf for arena spawning feedback
- [x] Improve the way the agent spawns
- [x] Add lights out configurations.
- [x] Improve environment framerates
- [x] Add moving food

## Version History

- v0.4 - Lights off moved to Unity, colors configurations, proportional goals, bugs fixes
    - The light is now directly switched on/off within Unity, configuration files stay the same
    - Blackouts now work with infinite episodes (`t=0`)
    - The `rand_colors` configurations have been removed and the user can now pass `RGB` values, see [here](documentation/configFile.md#objects)
    - Rewards for goals are now proportional to their size (except for the `DeathZone`), see [here](documentation/definitionsOfObjects.md#rewards)
    - The agent is now a ball rather than a cube
    - Increased safety for spawning the agent to avoid infinite loops
    - Bugs fixes
    
- v0.3 - Lights off, remove Beams and add cylinder
    - We added the possibility to switch the lights off at given intervals, see [here](documentation/configFile.md#blackouts)
    - visualizeLightsOff.py displays an example of lights off, from the agent's point of view
    - Beams objects have been removed
    - A `Cylinder` object has been added (similar behaviour to the `Woodlog`)
    - The immovable `Cylinder` tunnel has been renamed `CylinderTunnel`
    - `UnityEnvironment.reset()` parameter `config` renamed to `arenas_configurations_input`
    
- v0.2 - New moving food rewards, improved Unity performance and bug fixes 
    - Moving rewards have been added, two for each type of reward, see 
    [the details here](documentation/definitionsOfObjects.md#rewards).
    - Added details for the maze generator.
    - Environment performance improved.
    - [Issue #7](../../issues/7) (`-inf` rewards for `t: 0` configuration) is fixed.

- v0.1 - Initial Release

