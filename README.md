# AI Agents for Image and Video Generation

This workspace contains a hands-on collection of Jupyter notebooks for learning prompt engineering, image and video generation, evaluation, and agent orchestration with Google's Gen AI and Vertex AI SDKs.

The material progresses from direct image and video prompting to autonomous agents that generate ideas, create assets, evaluate results, and assemble a final video.

## Learning path

| Module | Notebook | Main topics |
|---|---|---|
| Prompt Engineering for Image Generation | `Prompt Engineering for Image Generation/Prompt Engineering for Image Generation.ipynb` | Gemini image generation, prompt structure, negative constraints, reference images |
| Prompt Engineering for Video Generation | `Prompt Engineering for Video Generation/vide_generation.ipynb` | Veo prompts, image-to-video generation, prompt enhancement, generated audio |
| Evaluation | `Evaluation/Evaluation Techniques.ipynb` | Generated-content rubrics, visual alignment, Gemini and SigLIP-style evaluation |
| Image Generation Agent | `Image Generation Agent/image_generation.ipynb` | Google ADK agents, tools, design concepts, generated idea images |
| Video Generation Agent | `Video Generation Agent/vid_generation.ipynb` | Multi-scene planning, scene images, scene videos, narration, FFmpeg assembly |

## Repository layout

```text
AI Agents for Image and Video Generation/
├── credentials.json                         # Google service-account credentials
├── helper.py                               # Shared authentication and utility helpers
├── requirements.txt                        # Shared Python dependencies
├── Prompt Engineering for Image Generation/
├── Prompt Engineering for Video Generation/
├── Evaluation/
├── Image Generation Agent/
└── Video Generation Agent/
```

Each module includes:

- A Jupyter notebook for the main lesson.
- A `helper.py` with authentication and notebook utilities.
- A `requirements.txt` listing required Python packages.
- Example input or generated output assets.

## Prerequisites

- Python 3.11 is recommended for compatibility with the notebook environment.
- JupyterLab or VS Code with the Jupyter extension.
- Access to Google Cloud Vertex AI APIs.
- A Google Cloud project with billing enabled and permission to use Gemini, Veo, and Vertex AI evaluation resources.
- FFmpeg for the video agent's final concatenation step.

## Installation

Create and activate a virtual environment from the workspace root:

### Windows PowerShell

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m pip install jupyterlab
```

### macOS/Linux

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m pip install jupyterlab
```

To install dependencies for an individual module, run the equivalent command from that module directory, for example:

```powershell
python -m pip install -r "Prompt Engineering for Image Generation\requirements.txt"
```

## Google Cloud authentication

The notebooks use service-account credentials through `GOOGLE_APPLICATION_CREDENTIALS`. The included helper functions first read that environment variable and then fall back to `credentials.json` in the current or parent directory.

For a standard local setup:

```powershell
$env:GOOGLE_APPLICATION_CREDENTIALS = (Resolve-Path ".\credentials.json").Path
jupyter lab
```

macOS/Linux:

```bash
export GOOGLE_APPLICATION_CREDENTIALS="$PWD/credentials.json"
jupyter lab
```

Alternatively, use the Google Cloud CLI:

```bash
gcloud auth application-default login
gcloud auth application-default set-quota-project YOUR_PROJECT_ID
```

Set `GOOGLE_CLOUD_PROJECT` and `GOOGLE_CLOUD_LOCATION` explicitly when required by a notebook or SDK call. The helper normally derives the project ID from the service-account JSON and sets the Vertex AI mode for the notebook session.

## Security warning

`credentials.json` is a private service-account credential file. Do not commit it, share it, upload it to public notebooks, or print its contents. Before publishing or sharing this workspace:

1. Remove or exclude `credentials.json`.
2. Rotate the key if it has been exposed.
3. Use environment variables or Application Default Credentials instead.
4. Add the credential file to `.gitignore`.

Generated media and credentials can also incur cloud costs. Confirm billing, quotas, and model availability before running generation cells.

## Running the notebooks

1. Start JupyterLab from the repository root:

   ```bash
   jupyter lab
   ```

2. Open the notebooks in the learning-path order listed above.
3. Run cells top to bottom. Several generation and evaluation cells take minutes to complete.
4. Use the asset files in each module directory as expected inputs or examples.
5. Review the notebook output; AI-generated results are probabilistic and may differ between runs.

The notebooks contain `authenticate(...)` calls and compatibility notes for the image and video model IDs. If a model ID or API method is deprecated, update it according to the installed SDK and Google Cloud documentation rather than editing helper behavior alone.

## FFmpeg

The Video Generation Agent uses FFmpeg to concatenate generated scenes. Install it and ensure `ffmpeg` is available on `PATH`.

- Windows: install from a package manager or https://ffmpeg.org/download.html
- macOS: `brew install ffmpeg`
- Linux: use your distribution package (`apt`, `dnf`, or `pacman`)

Verify the installation:

```bash
ffmpeg -version
```

## Troubleshooting

### Credentials not found

- Confirm `GOOGLE_APPLICATION_CREDENTIALS` points to an existing JSON file.
- Confirm `credentials.json` is at the workspace root or the module working directory.
- Restart the kernel after changing environment variables.

### Permission denied or quota errors

- Verify the service account or user has Vertex AI permissions.
- Enable the required APIs in the selected Google Cloud project.
- Check billing, quota, region, and model availability.

### `ModuleNotFoundError`

Activate the virtual environment and reinstall the module requirements:

```bash
python -m pip install -r requirements.txt
```

Restart the kernel after installing packages.

### Media generation is slow or times out

Generation operations are asynchronous and may take several minutes. Keep the kernel running, do not terminate the operation prematurely, and retry only if the API reports a failed or expired operation.

### FFmpeg command is not found

Install FFmpeg and open a new terminal or notebook session so the updated `PATH` is available.

## Module documentation

- [Prompt Engineering for Image Generation](Prompt%20Engineering%20for%20Image%20Generation/README.md)
- [Prompt Engineering for Video Generation](Prompt%20Engineering%20for%20Video%20Generation/README.md)
- [Evaluation](Evaluation/README.md)
- [Image Generation Agent](Image%20Generation%20Agent/README.md)
- [Video Generation Agent](Video%20Generation%20Agent/README.md)
