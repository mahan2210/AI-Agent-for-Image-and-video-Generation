# Prompt Engineering for Image Generation

This module demonstrates how to turn descriptive text prompts into generated images and how prompt choices affect the final output.

## Contents

- `Prompt Engineering for Image Generation.ipynb`: lesson notebook
- `helper.py`: authentication and image/display utilities
- `requirements.txt`: Python dependencies
- `slide-template.png`: template or reference asset

## Topics covered

- Writing clear subject, style, composition, and lighting instructions
- Adding material, camera, color, and mood constraints
- Using negative instructions to exclude unwanted elements
- Generating from text prompts
- Exploring variations from a shared concept

## Setup

From the repository root:

```powershell
python -m pip install -r "Prompt Engineering for Image Generation\requirements.txt"
```

Set `GOOGLE_APPLICATION_CREDENTIALS` or place `credentials.json` at the workspace root, then open the notebook and run it from top to bottom.

## Running

```powershell
jupyter lab "Prompt Engineering for Image Generation\Prompt Engineering for Image Generation.ipynb"
```

Wait for the notebook kernel to initialize, then execute the setup and authentication cells before image-generation cells. Generated assets are returned in the notebook and can be saved through the helper utilities or normal Python file-writing code.

## Prompt structure

A useful image prompt separates the request into:

1. Subject and main action
2. Environment and setting
3. Camera framing and lens
4. Lighting
5. Visual style or medium
6. Palette and atmosphere
7. Explicit exclusions or constraints

Example:

```text
A cinematic aerial photograph of a glass observatory in a snowy mountain valley,
small hikers below for scale, soft blue-hour lighting, 35mm lens, detailed
snow texture, quiet and scientific mood, no text or people near the building
```

## Tips

- Use singular, specific subjects for the first experiment.
- Change one prompt dimension at a time when comparing outputs.
- Record prompt and seed/model settings with each result.
- Treat model refusals or unexpected details as prompt and policy feedback.
- Test the same prompt multiple times if consistency matters.
