# Image Generation Agent

This module builds a tool-using agent with Google ADK that expands a design request into concepts and generated image ideas.

## Contents

- `image_generation.ipynb`: agent implementation and execution notebook
- `helper.py`: authentication and image utilities
- `requirements.txt`: Python dependencies
- `7876_idea.png`, `8010_idea.png`, `9835_idea.png`: generated example images
- `guide.png`: reference or instructional asset

## Agent flow

The notebook combines:

1. A Gemini-backed ADK agent
2. A design-concept generation tool
3. An image-generation tool
4. An in-memory runner for a single conversation
5. Output extraction and display helpers

The agent is expected to:

- Convert the user's request into useful design concepts.
- Select or structure one or more concepts.
- Call the image tool.
- Return descriptions and generated assets.

## Setup

```powershell
python -m pip install -r "Image Generation Agent\requirements.txt"
```

Configure credentials and open:

```powershell
jupyter lab "Image Generation Agent\image_generation.ipynb"
```

## Running

Run setup and authentication first. Then execute the tool and agent definitions before calling the agent runner. Watch the notebook output for tool calls and timing wrappers.

Example categories demonstrated by the notebook include concept generation and final image rendering. You can replace the example request with a new design brief, but keep the output contract of the tools simple and explicit.

## Implementation notes

- Tool docstrings and parameter descriptions guide the model's tool use.
- Generated image bytes are decoded through `extract_image(...)`.
- `make_display_tool(...)` prints function calls and elapsed time.
- ADK model configuration can change across SDK releases; verify imports and class names against the installed `google-adk` package.
