# PixelCSS 2.1

<p align="center">
  <img src="https://img.shields.io/badge/PixelCSS-2.1-8b5cf6?style=for-the-badge" alt="PixelCSS 2.1">
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5">
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
  <img src="https://img.shields.io/badge/Browser_AI-Transformers.js-8b5cf6?style=for-the-badge" alt="Browser AI">
</p>

<p align="center">
  <strong>Screenshot → Pixel Analysis → AI → HTML/CSS</strong>
</p>

<p align="center">
  A browser-based visual reconstruction engine for developers.
</p>

---

## Overview

**PixelCSS** is a browser-based screenshot analysis and UI reconstruction tool built with pure **HTML, CSS, and JavaScript**.

It analyzes screenshots at the pixel level, extracts visual properties, optionally uses browser-side AI for object detection and OCR, and generates editable HTML/CSS from the collected data.

The project is built around one idea:

> **Don't just look at the screenshot. Analyze it.**

Instead of simply sending an image to an external service and generating markup, PixelCSS analyzes the visual information first and creates a structured representation of the interface.

---

## Core Pipeline

```text
┌─────────────────┐
│   Screenshot    │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Pixel Analysis  │
└────────┬────────┘
         │
         ├──── Colors
         ├──── Geometry
         ├──── Contrast
         ├──── Edges
         └──── Layout
                  │
                  ▼
          ┌──────────────┐
          │   Vision AI  │
          └──────┬───────┘
                 │
          ┌──────┴──────┐
          ▼             ▼
      Detection        OCR
          │             │
          └──────┬──────┘
                 │
                 ▼
        ┌──────────────────┐
        │ Structured Data  │
        └────────┬─────────┘
                 │
                 ▼
       ┌────────────────────┐
       │  HTML/CSS Engine   │
       └─────────┬──────────┘
                 │
          ┌──────┴──────┐
          ▼             ▼
       HTML/CSS     Live Preview


---

Features

Pixel Analysis

PixelCSS uses the browser's Canvas API and ImageData API to inspect screenshots.

Dominant color extraction

Average color detection

Contrast estimation

Pixel change detection

Horizontal edge analysis

Vertical edge analysis

Basic layout inference

Border-radius estimation

Component heuristics

Screenshot dimension analysis


Browser-Side AI

PixelCSS can run machine-learning models directly inside the browser.

Current AI capabilities:

Object detection

Confidence scoring

Bounding-box detection

OCR

AI result visualization

AI-assisted reconstruction


HTML & CSS Generation

PixelCSS converts collected analysis data into editable frontend code.

Generated output includes:

HTML

CSS

Combined standalone HTML

JSON analysis

Live preview



---

Why PixelCSS?

Most screenshot-to-code systems focus primarily on generating markup.

PixelCSS focuses on the analysis process before code generation.

Raw Pixels
    ↓
Image Analysis
    ↓
Visual Structure
    ↓
Computer Vision
    ↓
OCR
    ↓
Structured Data
    ↓
HTML/CSS Generation

This makes PixelCSS an experimental visual reconstruction engine rather than a simple screenshot-to-code wrapper.


---

Tech Stack

Technology	Purpose

HTML5	Application structure
CSS3	UI and generated styling
JavaScript	Core application engine
Canvas API	Image processing
ImageData API	Pixel-level analysis
Transformers.js	Browser-side machine learning
DETR	Object detection
TrOCR	OCR
WebAssembly	Local model execution


No Framework Required

PixelCSS intentionally uses browser-native technologies.

HTML
CSS
JavaScript
Canvas
Web APIs

No frontend framework is required.

No database is required.

No application backend is required.

No package manager is required.


---

AI Models

PixelCSS uses browser-compatible machine-learning models through Transformers.js.

Object Detection

Xenova/detr-resnet-50

Used to detect objects inside screenshots and return:

Object labels

Confidence scores

Bounding boxes


OCR

Xenova/trocr-small-printed

Used to extract visible text from screenshots.

> AI models are loaded when required and may be cached by the browser.




---

How It Works

1. Upload a Screenshot

Upload a screenshot or drag an image into PixelCSS.

Supported formats:

PNG

JPG

JPEG

WEBP


2. Image Processing

The screenshot is rendered through the browser's Canvas API.

Pixel data is extracted using ImageData.

PixelCSS then processes the image to identify visual properties.

3. Color Analysis

The analyzer extracts dominant and average colors.

Example:

{
  "palette": [
    "#0b0d12",
    "#151821",
    "#8b5cf6"
  ]
}

4. Geometry Analysis

PixelCSS examines significant visual changes across horizontal and vertical regions.

This helps estimate possible page structures such as:

Centered
Stacked
Multi-column
Sidebar / Content

5. Component Detection

Visual signals are used to estimate possible interface components.

Examples:

Header
Sidebar
Card
Button
Text
Container

6. Vision AI

The optional AI layer performs object detection.

Example:

{
  "label": "laptop",
  "score": 87
}

7. OCR

The OCR engine attempts to extract visible text.

Example:

{
  "text": "Continue"
}

8. Code Generation

The collected information is passed into the HTML/CSS generator.

PixelCSS produces:

HTML
CSS
JSON
Combined HTML


---

Example Analysis Result

{
  "engine": "PixelCSS 2.1",
  "generatedBy": "KILLERDUTCH",
  "image": {
    "width": 1440,
    "height": 900
  },
  "layout": {
    "type": "sidebar / content",
    "confidence": 76
  },
  "radius": 12,
  "palette": [
    "#0b0d12",
    "#151821",
    "#8b5cf6"
  ]
}


---

Running Locally

PixelCSS is a standalone browser-based application.

No Python, Node.js, package manager, build tool, or backend is required.

Simply open:

index.html

in a modern web browser.

> Some browser-side AI features may require an internet connection to load external libraries and AI models.




---

Project Structure

PixelCSS/
│
├── index.html
└── README.md

The entire application is contained inside index.html.

No installation.

No dependencies to install.

No build process.

No backend.

Just open the HTML file and run PixelCSS.


---

Performance

Browser-side machine learning can be resource-intensive.

The first AI execution may take longer because models need to be downloaded and initialized.

Performance depends on:

CPU

RAM

Browser

Screenshot resolution

WebAssembly performance

AI model size



---

Privacy

PixelCSS is designed around client-side processing.

The core screenshot analysis does not require an application backend.

Pixel data is processed directly inside the browser.

The AI pipeline is also designed to execute locally in the browser.

External libraries and model files are loaded from their configured CDN when required.


---

Limitations

PixelCSS is an experimental visual reconstruction engine.

It does not guarantee a pixel-perfect recreation of every screenshot.

A screenshot contains visual information, but it does not contain the original source code, DOM structure, CSS architecture, or application logic.

PixelCSS cannot reliably recover:

Original DOM structure

Original CSS architecture

Exact font files

Responsive breakpoints

Hidden elements

JavaScript behavior

Animations

Hover states

Component states

Application logic

Original assets

Accessibility structure


AI models may also produce incorrect detections or OCR results.

Generated code should therefore be treated as an editable starting point.


---

Future Updates

PixelCSS 2.1 is a complete working release.

Development will continue with a focus on improving reconstruction accuracy, visual understanding, AI integration, and generated code quality.

PixelCSS 2.2

[ ] Improved component detection

[ ] Better text-region detection

[ ] More accurate spacing analysis

[ ] Font estimation

[ ] Improved bounding-box reconstruction

[ ] Better color clustering


PixelCSS 2.5

[ ] Flexbox inference

[ ] CSS Grid inference

[ ] Component tree generation

[ ] Region-based OCR

[ ] Visual similarity scoring

[ ] Improved responsive reconstruction


PixelCSS 3.0

[ ] Advanced Vision-Language Model

[ ] Semantic UI understanding

[ ] Multi-pass code generation

[ ] Component-level reconstruction

[ ] Visual diff system

[ ] Screenshot-to-component pipeline



---

Development Philosophy

> See the pixels. Understand the structure. Generate the code.



Pixel Data
    +
Image Processing
    +
Computer Vision
    +
OCR
    +
Browser ML
    ↓
PixelCSS
    ↓
HTML + CSS

The goal is to explore how much useful frontend structure can be recovered from visual information alone.


---

Contributing

Contributions, technical ideas, experiments, and improvements are welcome.

Potential areas for contribution include:

Computer vision

Image processing

Browser ML

OCR

Layout detection

CSS generation

UI reconstruction

Frontend tooling

Visual similarity algorithms

Performance optimization


If you find a bug or have an idea for improving PixelCSS, feel free to open an issue or submit a pull request.


---

License

This project currently does not specify a license.

If you want others to freely use, modify, and redistribute the project, consider adding an appropriate open-source license such as MIT.


---

Author

KILLERDUTCH

PixelCSS was created as an experiment combining:

HTML
CSS
JavaScript
Canvas
Image Processing
Computer Vision
OCR
Browser-side AI


---

Status

Version: 2.1
Status: Complete Working Release
Architecture: Single-file
Frontend: HTML / CSS / JavaScript
AI: Browser-side
Backend: Not Required


---

<p align="center"><strong>PixelCSS 2.1</strong>

<br><br>

<sub>See the pixels. Understand the structure. Generate the code.</sub>

<br><br>

<strong>Created by KILLERDUTCH</strong>

</p>
