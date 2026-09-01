PixelCSS 2.1

Screenshot → Pixel Analysis → AI → HTML/CSS

PixelCSS is a browser-based screenshot analysis and UI reconstruction tool built with pure HTML, CSS, and JavaScript.

It analyzes screenshots at the pixel level, extracts visual properties, uses browser-side AI for additional detection, and generates an editable HTML/CSS interface from the collected data.

---

Overview

Recreating a web interface from a screenshot usually means manually estimating colors, spacing, layout, typography, borders, radius, and component structure.

PixelCSS automates part of that process.

The project combines deterministic pixel analysis with browser-side machine learning to create a structured representation of a visual interface before generating frontend code.

Pipeline

Screenshot

↓

Pixel Analysis

↓

Visual Structure

↓

Vision AI + OCR

↓

Structured Data

↓

HTML/CSS Generation

↓

Live Preview

---

Features

Pixel Analysis

PixelCSS analyzes the uploaded screenshot using the browser's Canvas and ImageData APIs.

- Dominant color extraction
- Average color detection
- Contrast estimation
- Edge/change detection
- Layout inference
- Border-radius estimation
- Basic component detection
- Screenshot dimension analysis

Browser-Side AI

PixelCSS can run machine-learning models directly inside the browser.

Current AI capabilities:

- Object detection
- Confidence scoring
- OCR
- AI result visualization
- AI-assisted interface reconstruction

No application backend is required.

Code Generation

PixelCSS generates editable frontend code from the analysis results.

Available outputs:

- HTML
- CSS
- Combined HTML document
- JSON analysis
- Live preview

---

Why PixelCSS?

PixelCSS isn't designed to simply throw a screenshot into an AI model and hope for usable code.

The project takes a different approach:

Analyze first. Generate second.

The screenshot is processed through multiple stages:

- Raw pixel analysis
- Color extraction
- Geometry analysis
- Layout heuristics
- Object detection
- OCR
- Structured data generation
- HTML/CSS generation

This makes PixelCSS more of an experimental visual reconstruction engine than a simple screenshot-to-code generator.

---

Architecture

                         ┌───────────────┐
                         │   Screenshot  │
                         └───────┬───────┘
                                 │
                                 ▼
                      ┌────────────────────┐
                      │   Pixel Analyzer   │
                      └─────────┬──────────┘
                                │
               ┌────────────────┼────────────────┐
               │                │                │
               ▼                ▼                ▼
            Colors          Geometry         Contrast
               │                │                │
               └────────────────┼────────────────┘
                                │
                                ▼
                       ┌────────────────┐
                       │   Layout AI    │
                       └───────┬────────┘
                               │
                 ┌─────────────┴─────────────┐
                 ▼                           ▼
          ┌──────────────┐            ┌──────────────┐
          │  Vision AI   │            │     OCR      │
          └──────┬───────┘            └──────┬───────┘
                 │                           │
                 └─────────────┬─────────────┘
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
                     ┌────────┴────────┐
                     ▼                 ▼
                  HTML/CSS        Live Preview

---

Tech Stack

Technology| Purpose
HTML5| Application structure
CSS3| Interface and generated styling
JavaScript| Core engine
Canvas API| Image processing
ImageData API| Pixel analysis
Transformers.js| Browser-side machine learning
DETR| Object detection
TrOCR| OCR
WebAssembly| Local model execution

---

AI Models

PixelCSS currently uses browser-compatible models through Transformers.js.

Object Detection

"Xenova/detr-resnet-50"

Used to detect objects in screenshots and return confidence scores and bounding-box information.

OCR

"Xenova/trocr-small-printed"

Used to extract visible text from image content.

AI models are loaded only when required and may be cached by the browser.

---

How It Works

1. Upload

Upload a screenshot or drag one into the application.

Supported formats:

- PNG
- JPG
- JPEG
- WEBP

2. Analyze

PixelCSS processes the image and extracts information such as:

- Colors
- Contrast
- Geometry
- Layout
- Radius
- Visual changes

3. Run AI

The optional AI pipeline performs:

- Object detection
- OCR
- Confidence analysis

4. Inspect

Review the generated:

- HTML
- CSS
- JSON
- Combined document

5. Preview

The generated interface is rendered directly inside the browser.

6. Copy

Copy the generated code and continue developing it as a normal frontend project.

---

Example Analysis

A screenshot may produce structured data similar to:

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

The generated structure is then used to build an editable HTML/CSS interface.

---

Running Locally

PixelCSS works entirely on the client side.

For the best compatibility, especially when loading browser-side AI models, run the project through a local HTTP server.

Python

Run:

"python -m http.server 8000"

Then open:

"http://localhost:8000"

VS Code

You can also use a local development extension such as Live Server.

Open "index.html" through the local server and start using PixelCSS.

---

Project Structure

PixelCSS is intentionally distributed as a single-file application.

PixelCSS/
│
├── index.html
│
└── README.md

The application logic, styling and interface are contained inside "index.html".

This keeps the project easy to:

- Clone
- Inspect
- Modify
- Fork
- Experiment with
- Deploy

---

Privacy

PixelCSS is designed around client-side processing.

The core screenshot analysis does not require an application backend.

The browser performs the pixel analysis locally, while the AI pipeline is also designed to execute inside the browser.

External libraries and AI model files are loaded from their configured CDN when required.

---

Performance

Browser-side machine learning can be resource-intensive.

The first AI execution may take longer because models need to be downloaded and initialized.

Performance depends on:

- CPU
- RAM
- Browser
- Screenshot resolution
- WebAssembly performance
- AI model size

PixelCSS also reduces image resolution for certain pixel-analysis operations to keep processing practical.

---

Limitations

PixelCSS is an experimental reconstruction engine.

It does not guarantee pixel-perfect recreation of every screenshot.

A screenshot contains visual information, but it does not contain the original source code or application logic.

Therefore, PixelCSS cannot reliably recover:

- Original DOM structure
- Original CSS architecture
- Exact font files
- Responsive breakpoints
- Hidden elements
- JavaScript behavior
- Animations
- Hover states
- Component states
- Complex application logic

AI models may also produce incorrect detections.

Generated code should be considered an editable starting point rather than a guaranteed final implementation.

---

Roadmap

2.2

- [ ] Improved component detection
- [ ] Better text-region detection
- [ ] More accurate spacing analysis
- [ ] Font estimation
- [ ] Improved bounding-box reconstruction
- [ ] Better color clustering

2.5

- [ ] Flexbox inference
- [ ] CSS Grid inference
- [ ] Component tree generation
- [ ] Region-based OCR
- [ ] Visual similarity scoring
- [ ] Improved responsive reconstruction

3.0

- [ ] Advanced Vision-Language Model
- [ ] Semantic UI understanding
- [ ] Multi-pass code generation
- [ ] Component-level reconstruction
- [ ] Visual diff system
- [ ] Screenshot-to-component pipeline

---

Development Philosophy

PixelCSS follows a simple principle:

«Don't just look at the screenshot. Analyze it.»

Instead of relying entirely on generative AI, the project combines deterministic algorithms with machine learning.

Pixel Data
    +
Image Analysis
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

---

Contributing

Contributions and technical experiments are welcome.

Potential areas for improvement include:

- Computer vision
- Image processing
- Browser ML
- OCR
- Layout detection
- CSS generation
- UI reconstruction
- Frontend tooling

If you find a bug or have an idea that could improve the reconstruction pipeline, feel free to open an issue or submit a pull request.

---

License

This project currently does not specify a license.

If you want others to freely use, modify, and distribute the project, consider adding an open-source license such as MIT.

---

Author

KILLERDUTCH

PixelCSS is built as an experiment combining frontend engineering, image analysis, computer vision, OCR, and browser-based machine learning.

---

<p align="center">
    <strong>PixelCSS 2.1</strong>
    <br>
    <sub>See the pixels. Understand the structure. Generate the code.</sub>
</p>
