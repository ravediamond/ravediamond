# Ravindu Somawansa

Staff Engineer (Paris) · evaluation & agent harness · research engineer in robot learning

## Shisso Robotics · [shissorobotics.com](https://shissorobotics.com)

**Do robot-learning papers hold up on a real robot under $1,500?**

One engineer, an SO-101 arm and a Jetson Orin NX, about €1,350. Each paper is re-tested against the cheapest baseline first, with the pass mark written down before the run. Verdicts, code and data are public.

*Shisso (質素): modest, frugal.*

### What I found so far

1. On this rig the cheapest baseline matched or beat the learned method, so build it first.
2. Judge a rollout when the arm is still, with fixed rules, before you trust a learned judge.
3. Imagining ahead did not help on this rig, neither to spot failures nor to pick actions.
4. On a Jetson Orin NX, the large models I tried did not fit the control loop.
5. On an asynchronous arm each new chunk starts with a jump, and overwriting the first steps removes most of it, offline.
6. Ten trials on a task every policy solves tell inference engines apart, not policies.

### Papers tried, clear result

| Paper | On this rig | Result |
|---|---|---|
| SmolVLA | works | 9 of 10 trials worked, though I set no pass mark first. |
| LeWorldModel | does not help | The commanded joints alone picked the executed action more often than the world model. |
| DINO-WM | does not help | The commanded joints alone ranked the executed action better. |
| VLA-JEPA | works | 9 of 10 trials, no pass mark set first; robustness was not run. |
| Robometer | does not help | Failure detection scored 0.818, just under my bar: a screen, not a final judge. |
| ContactGuard | does not help | The current camera view detects failures better; imagining ahead scored only 0.70. |
| FAIL-Detect and SAFE | does not help | 9.1 % of successful runs were flagged: more false alarms than promised. |
| LeJEPA identifiability | works | On goal-directed data the latent explained only 0.565 of joint angles: do not read them from it. |
| Adaptive Action Chunking | does not help | Chunk length stayed at 2 in both phases on this policy. |

17 more tests are not settled yet. Full register: [shissorobotics.com/papers](https://shissorobotics.com/papers/)

### Engineering notes

| | |
|---|---|
| **974 → 238 ms** | SmolVLA on a Jetson Orin NX, per chunk, with vla.cpp |
| **0.4 ms** | Why your VLA's actions jump at every chunk boundary on real hardware, and the fix |
| **47 % worse** | A correctness fix upstream and what it did to my checkpoint |
| **p99** | p99 is not a tail: latency numbers that lie about chunked policies |
| **no pip** | LeRobot on a Jetson: why there is no `pip install torch`, and what it took |

### Code and data

- **[paper-vs-hardware](https://github.com/ravediamond/paper-vs-hardware)**: reproduction code for every test on the site
- **[lerobot-jetson](https://github.com/ravediamond/lerobot-jetson)**: CUDA PyTorch for LeRobot on Jetson Orin, built from source; mirrored upstream as a community Dockerfile ([lerobot#4599](https://github.com/huggingface/lerobot/pull/4599)). Write-up: [Why is it so hard to run LeRobot on NVIDIA Jetson?](https://huggingface.co/blog/ravediamond/why-is-it-so-hard-to-run-lerobot-on-nvidia-jetson)
- **[Hugging Face](https://huggingface.co/ravediamond)**: SO-101 rollouts, datasets and checkpoints

## Open source

- **[huggingface/lerobot](https://github.com/huggingface/lerobot)**, reviewer: runtime guard for out-of-bounds action chunks ([#4241](https://github.com/huggingface/lerobot/pull/4241)), future-frame leak fix in VLA-JEPA's world-model objective ([#4381](https://github.com/huggingface/lerobot/pull/4381)), Jetson Dockerfile ([#4599](https://github.com/huggingface/lerobot/pull/4599)), CLI config fixes ([#4260](https://github.com/huggingface/lerobot/pull/4260), [#4265](https://github.com/huggingface/lerobot/pull/4265))
- **[VinRobotics/vla.cpp](https://github.com/VinRobotics/vla.cpp)**: Orin NX benchmark ([#36](https://github.com/VinRobotics/vla.cpp/pull/36)), ACT port ([#38](https://github.com/VinRobotics/vla.cpp/pull/38)), chunk prefix fix ([#60](https://github.com/VinRobotics/vla.cpp/pull/60))
- **[kyutai-labs/reki](https://github.com/kyutai-labs/reki)**: SO-101 onboarding ([#7](https://github.com/kyutai-labs/reki/pull/7))

## Also built

- **[Baby Reachy-Mini Companion](https://github.com/ravediamond/baby-reachy-mini-companion)**: fully local nursery companion on Reachy Mini (7 on-device models, Jetson Orin NX). #2 in the NVIDIA GTC x Hugging Face Golden Ticket community ranking.
- **[MCPH](https://github.com/ravediamond/MCPH)**: artifact storage and sharing over the Model Context Protocol ([mcph.io](https://mcph.io))

## Links

[shissorobotics.com](https://shissorobotics.com) · [LinkedIn](https://www.linkedin.com/in/ravindusomawansa/) · [Hugging Face](https://huggingface.co/ravediamond) · [X](https://twitter.com/RSomaw)
