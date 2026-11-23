# Evaluation Techniques

This module demonstrates how to evaluate generated images with rubric-based and similarity-oriented techniques.

## Contents

- `Evaluation Techniques.ipynb`: evaluation notebook
- `misaligned_image.png`: deliberately mismatched example
- `helper.py`: authentication, image extraction, rubric, and visualization helpers
- `requirements.txt`: Python dependencies

## Topics covered

- Creating evaluation rubrics
- Comparing aligned and misaligned generated images
- Asking a multimodal model for structured quality scores
- Inspecting per-criterion image scores
- Comparing Gemini-based judgments with similarity metrics
- Visualizing results with radar charts

## Setup

```powershell
python -m pip install -r "Evaluation\requirements.txt"
```

Configure Google Cloud credentials and run:

```powershell
jupyter lab "Evaluation\Evaluation Techniques.ipynb"
```

## Evaluation workflow

1. Define a set of observable evaluation criteria.
2. Provide each image and its intended prompt or reference context.
3. Generate rubric-based scores from Gemini.
4. Calculate the supporting similarity metric for the same cases.
5. Compare structured scores and similarity values.
6. Inspect disagreements, especially for nuanced concepts such as composition or style.

The notebook uses both a rubric prompt and an aligned/misaligned example. The radar chart helper provides a side-by-side visual comparison of overall and criterion-level results.

## Interpreting scores

Scores are a diagnostic aid, not an objective guarantee of quality. A high score can coexist with a factual or policy issue, and a low similarity score can still describe a valid creative interpretation.

When changing criteria:

- Keep descriptions observable and mutually distinct.
- Use the same scale for every criterion.
- Include examples or anchors for borderline scores.
- Review several examples manually before tuning prompts.
