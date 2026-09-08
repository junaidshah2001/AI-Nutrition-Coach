# AI Nutrition Coach

A multimodal AI nutrition analysis system that analyzes food images and produces structured nutritional estimates using a vision-language model.

## Overview

This project demonstrates an end-to-end multimodal AI pipeline for food image understanding and nutrition estimation.

The system:

1. Accepts a food image
2. Uses a vision-language model to identify visible food
3. Estimates the visible portion
4. Estimates protein, carbohydrates, fat, and fiber
5. Calculates calories deterministically from macronutrients
6. Performs structural and consistency validation
7. Detects suspicious outputs
8. Calibrates model confidence
9. Flags uncertain cases for human review

## Model

**Hugging Face SmolVLM2-2.2B-Instruct**

Model: `HuggingFaceTB/SmolVLM2-2.2B-Instruct`

The model is downloaded automatically at runtime.

## Architecture

```text
Food Image
    |
    v
Vision-Language Model
    |
    +-- Food identification
    +-- Portion estimation
    +-- Protein
    +-- Carbohydrates
    +-- Fat
    +-- Fiber
    |
    v
Structured JSON
    |
    v
Deterministic Calorie Calculation
    |
    v
Reference-Free Reliability Audit
    |
    +-- Zero-macro detection
    +-- Generic-label detection
    +-- Very-low-calorie detection
    +-- Macro consistency
    +-- Confidence calibration
    +-- Human-review flag
    |
    v
Final Nutrition Estimate
```

## Calorie Calculation

Calories are calculated deterministically using the standard macronutrient energy factors:

```text
Calories = 4 × Protein(g)
         + 4 × Carbohydrates(g)
         + 9 × Fat(g)
```

This prevents mathematical inconsistency between reported macronutrients and calories.

## Validation

The project includes reference-free validation for:

- JSON validity
- Structured output completeness
- Numeric validity
- Macro-calorie consistency
- Zero-major-macro detection
- Generic food-label detection
- Suspiciously low calorie detection
- Confidence calibration
- Human-review requirements

## Important Limitation

**Reference-free validation is not nutritional accuracy.**

Actual nutritional accuracy requires a ground-truth dataset containing verified food portions and nutrient values.

Therefore, this project does not claim that the model's estimated calories or macronutrients are medically or nutritionally exact.

## Hardware

The system was developed and tested in Google Colab using:

- NVIDIA Tesla T4 GPU
- CUDA acceleration
- PyTorch
- Hugging Face Transformers

## Repository Structure

```text
AI-Nutrition-Coach/
|
+-- AI_Nutrition_Coach.ipynb
+-- README.md
+-- requirements.txt
+-- results/
    +-- validation_results.csv
```

## Running the Project

Open the notebook in Google Colab and run the cells from top to bottom.

The model will automatically download from Hugging Face.

## Technologies

- Python
- PyTorch
- Hugging Face Transformers
- SmolVLM2
- Computer Vision
- Vision-Language Models
- Multimodal AI
- Prompt Engineering
- Structured JSON Generation
- Model Validation
- Confidence Calibration
- Google Colab

## Project Purpose

This project demonstrates practical skills in:

- Multimodal AI
- Vision-Language Models
- Prompt engineering
- Structured model outputs
- Deterministic post-processing
- AI reliability engineering
- Model evaluation
- GPU inference

## Disclaimer

This is an experimental AI research and portfolio project.

The generated nutrition estimates should not be treated as medical, dietary, or clinical advice.
