# Prompt Engineering for Video Generation

This module explores text-to-video and image-to-video generation with Veo, including prompt enhancement and generated audio.

## Contents

- `vide_generation.ipynb`: lesson notebook
- `helper.py`: authentication and media utilities
- `requirements.txt`: Python dependencies
- `original.mp4` and `enhanced.mp4`: example outputs
- `slide-image.png` and `video-image.png`: example image assets

## Topics covered

- Writing motion-oriented prompts
- Controlling shot size, camera movement, pacing, and atmosphere
- Creating an image and using it as a video reference
- Enhancing a basic prompt into a detailed production prompt
- Generating and inspecting audio with video
- Polling long-running video generation operations

## Setup

```powershell
python -m pip install -r "Prompt Engineering for Video Generation\requirements.txt"
```

Configure Google Cloud credentials as described in the root README, then open:

```powershell
jupyter lab "Prompt Engineering for Video Generation\vide_generation.ipynb"
```

## Running

Run the notebook in order. Video operations can take several minutes and the notebook periodically polls the operation until completion. If the SDK reports deprecated prompt or source arguments, replace them with the current `source`-based API shape shown by the installed SDK.

## Prompt structure

A strong video prompt describes:

- Scene subject and setting
- Initial and ending composition
- Visible action
- Camera movement
- Shot duration and pacing
- Lighting and environment
- Sound, dialogue, or generated-audio direction
- Negative constraints

Example:

```text
Slow dolly shot through a futuristic greenhouse at sunrise. Autonomous
watering drones pass between glass panels as vines open toward the light.
Soft atmospheric haze, restrained orange and teal palette, natural mechanical
sounds, no readable text, no abrupt cuts
```

## Output handling

Generated videos are stored in the notebook response or written as MP4 files by the lesson cells. The included helper and notebook functions display video bytes in Jupyter.

Video generation may incur cost and takes longer than image generation. Preserve useful source prompts and generated files for reproducible comparisons.
