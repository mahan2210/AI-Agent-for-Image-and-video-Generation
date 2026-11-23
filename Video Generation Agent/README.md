# Video Generation Agent

This module builds an agent workflow that turns a brief into scene images and videos, validates the result, repairs problems, and concatenates a final production sequence.

## Contents

- `vid_generation.ipynb`: agent workflow notebook
- `helper.py`: authentication and media helpers
- `requirements.txt`: Python dependencies
- `scene_1_ref.png`, `scene_2_ref.png`, `scene_3_ref.png`: reference images
- `scene_1.mp4`, `scene_2.mp4`, `scene_3.mp4`: generated scene clips
- `rag_explainer.mp4`: generated or example final media

## Workflow

The notebook demonstrates an end-to-end pipeline:

1. Plan or accept a sequence of scenes.
2. Generate a consistent reference image for each scene.
3. Generate a video clip from that scene prompt and image.
4. Add narration or dialogue instructions.
5. Inspect for errors in timing, visuals, or narration.
6. Re-run a faulty scene with corrected instructions.
7. Concatenate all scenes with FFmpeg.

The workflow intentionally includes a bad narration example so the agent or notebook can detect and repair the audio direction.

## Setup

```powershell
python -m pip install -r "Video Generation Agent\requirements.txt"
```

Install FFmpeg and verify it is on `PATH`:

```powershell
ffmpeg -version
```

Configure Google Cloud credentials, then open:

```powershell
jupyter lab "Video Generation Agent\vid_generation.ipynb"
```

## Running

Run setup, helper imports, scene planning, and tool definitions first. Scene generation cells are asynchronous and may take several minutes per scene.

The final concatenation cell combines scene clips in their intended order. Keep scene filenames and durations stable before running it.

## Scene consistency

For coherent sequences:

- Reuse visual attributes across scene prompts.
- Use one consistent reference-image style.
- Describe continuity in location, palette, character appearance, and camera scale.
- Match narration timing to each clip's action.
- Keep transitions and pacing explicit.

## Troubleshooting

- If scene generation fails, verify that the selected Veo model is enabled and available in the configured location.
- If generated audio is wrong, correct the scene prompt or narration instructions and re-run only that scene.
- If concatenation fails, confirm that every scene file exists and is a valid MP4.
- If FFmpeg reports incompatible streams, inspect codecs and convert clips to a common format before concatenation.
