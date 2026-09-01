# PixelCSS 2.1

> **Screenshot → Pixel Analysis → AI → HTML/CSS**

PixelCSS is a browser-based screenshot analysis and UI reconstruction tool built with pure HTML, CSS, and JavaScript.

It analyzes the visual structure of a screenshot, extracts useful pixel-level information, optionally uses browser-side AI for object detection and OCR, and generates an editable HTML/CSS interface from the results.

---

## Overview

Rebuilding a web interface from a screenshot normally requires manually estimating:

- Colors
- Spacing
- Layout
- Border radius
- Components
- Contrast
- Positioning
- Text
- Visual hierarchy

PixelCSS attempts to automate part of this process.

Instead of treating a screenshot as a simple image, PixelCSS analyzes it as a collection of visual signals and converts those signals into structured data that can be used for code generation.

```text
Screenshot
     │
     ▼
┌──────────────────┐
│  Pixel Analyzer  │
└────────┬─────────┘
         │
         ├── Colors
         ├── Contrast
         ├── Geometry
         ├── Layout
         └── Visual Features
                  │
                  ▼
           ┌─────────────┐
           │  Vision AI  │
           └──────┬──────┘
                  │
                  ├── Objects
                  └── Confidence
                         │
                         ▼
                    ┌────────┐
                    │   OCR  │
                    └────┬───┘
                         │
                         ▼
                Structured Results
                         │
                         ▼
                 HTML/CSS Generator
                         │
                ┌────────┴────────┐
                ▼                 ▼
           Generated Code     Live Preview


---

Features

Pixel Analysis

PixelCSS performs client-side image analysis using the browser's Canvas and ImageData APIs.

Current analysis includes:

Dominant color extraction

Average color detection

Contrast estimation

Edge/change detection

Basic layout inference

Border-radius estimation

Component heuristics

Screenshot dimensions



---

Browser-Side AI

PixelCSS can optionally run machine-learning models directly inside the browser.

The AI pipeline currently supports:

Object detection

Confidence scoring

OCR

AI result visualization

Integration with generated code


No application backend is required.


---

HTML & CSS Generation

PixelCSS converts the analysis results into editable frontend code.

Generated output includes:

HTML

CSS

Combined standalone HTML

Structured JSON

Live preview


The generated code is intended to be a starting point that developers can continue editing.


---

Why PixelCSS?

Most screenshot-to-code systems focus entirely on generating code.

PixelCSS takes a more experimental approach:

Pixels
  ↓
Analysis
  ↓
Structure
  ↓
AI
  ↓
Code

The goal is not simply to generate random HTML that looks vaguely similar.

The project explores how traditional image processing, heuristics, computer vision and browser-side machine learning can work together to reconstruct a visual interface.


---

Architecture

┌──────────────────────────────────────────────┐
│                  PixelCSS                    │
├──────────────────────────────────────────────┤
│                                              │
│                 Screenshot                   │
│                      │                       │
│                      ▼                       │
│                Canvas / Pixels               │
│                      │                       │
│          ┌───────────┴───────────┐           │
│          ▼                       ▼           │
│    Pixel Analyzer             Vision AI      │
│          │                       │           │
│          │                 Object Detection  │
│          │                       │           │
│          └───────────┬───────────┘           │
│                      ▼                       │
│                     OCR                      │
│                      │                       │
│                      ▼                       │
│              Structured Results              │
│                      │                       │
│                      ▼                       │
│               Code Generator                 │
│                      │                       │
│              ┌───────┴───────┐               │
│              ▼               ▼               │
│            HTML             CSS              │
│              │               │               │
│              └───────┬───────┘               │
│                      ▼                       │
│                 Live Preview                 │
│                                              │
└──────────────────────────────────────────────┘


---

Tech Stack

Technology	Purpose

HTML5	Application structure
CSS3	UI and generated styling
JavaScript	Core application logic
Canvas API	Image processing
ImageData API	Pixel-level analysis
Transformers.js	Browser-side machine learning
DETR	Object detection
TrOCR	OCR
WebAssembly	Local model execution



---

AI Models

PixelCSS uses browser-compatible models through Transformers.js.

Object Detection

Xenova/detr-resnet-50

Used for detecting objects inside the uploaded screenshot and returning bounding-box information and confidence scores.

OCR

Xenova/trocr-small-printed

Used for extracting text from image content.

> AI models are downloaded when required and may be cached by the browser.




---

How It Works

1. Upload a Screenshot

Drop an image into PixelCSS or select one using the upload button.

Supported formats include:

PNG
JPG
JPEG
WEBP


---

2. Pixel Analysis

PixelCSS reads the screenshot through the browser's Canvas API and extracts visual information.

Example:

{
    "width": 1440,
    "height": 900,
    "average": "#101218",
    "contrast": 182,
    "radius": 12
}


---

3. Layout Inference

The analyzer examines visual changes across horizontal and vertical regions to estimate the overall layout.

Possible results include:

centered
stacked
multi-column
sidebar / content


---

4. Vision AI

The optional AI engine analyzes the image and returns detected objects with confidence scores.

Example:

{
    "label": "laptop",
    "score": 87,
    "box": {
        "xmin": 320,
        "ymin": 180,
        "xmax": 920,
        "ymax": 620
    }
}


---

5. OCR

The OCR layer attempts to extract visible text from the screenshot.

Example:

{
    "text": "Continue"
}


---

6. Code Generation

The collected information is passed into the HTML/CSS generator.

The result can be viewed, copied and edited directly from the interface.


---

Example Output

A simplified PixelCSS result can look like this:

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
    ],

    "pixelElements": [
        {
            "type": "header",
            "confidence": 80
        },
        {
            "type": "sidebar",
            "confidence": 76
        },
        {
            "type": "card",
            "confidence": 78
        }
    ]
}


---

Running Locally

PixelCSS is a client-side application, but running it through an HTTP server is recommended, especially when browser-side AI models are being loaded.

VS Code

Open the project with VS Code and run index.html using a local server such as Live Server.

Python

python -m http.server 8000

Then open:

http://localhost:8000


---

Project Structure

The current version intentionally uses a single HTML file.

PixelCSS/
│
├── index.html
│
└── README.md

Everything required by the application is contained inside index.html, while external browser-side AI libraries and models are loaded when needed.


---

Performance

Browser-side AI can be resource-intensive.

The first AI execution may take longer because the browser needs to download and initialize the models.

Performance depends on:

CPU

RAM

Browser

Screenshot resolution

WebAssembly performance

Model size


PixelCSS also performs some analysis on a reduced-resolution copy of the screenshot to keep pixel processing manageable.


---

Privacy

PixelCSS is designed around client-side processing.

The core application does not require an application backend to process screenshots.

Screenshots can be analyzed directly inside the browser, while the AI pipeline is also designed to run locally.

> Note: external libraries and model files are loaded from their configured CDNs when required.




---

Limitations

PixelCSS is an experimental reconstruction tool.

It does not guarantee a pixel-perfect recreation of every interface.

Some information cannot reliably be recovered from a screenshot alone.

For example:

Exact DOM structure

Original CSS architecture

Semantic HTML

Exact font files

Responsive breakpoints

Hidden elements

JavaScript behavior

Animations

Hover states

Component state

Complex nested layouts


AI models may also produce incorrect classifications.

Generated code should therefore be treated as an editable starting point rather than a guaranteed final implementation.


---

Roadmap

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

[ ] Better responsive reconstruction


PixelCSS 3.0

[ ] Advanced Vision-Language Model

[ ] Semantic UI understanding

[ ] Multi-pass code generation

[ ] Component-level reconstruction

[ ] Visual diff system

[ ] Screenshot-to-component pipeline



---

Development Philosophy

PixelCSS is built around a simple idea:

> Don't just look at the screenshot. Analyze it.



The project intentionally combines deterministic algorithms with AI rather than depending entirely on a generative model.

Traditional Analysis
        +
Computer Vision
        +
OCR
        +
Browser ML
        ↓
   PixelCSS

This makes the project useful as both a practical frontend utility and an experiment in browser-based computer vision.


---

Contributing

Contributions, ideas and experiments are welcome.

Areas that could benefit from experimentation include:

Computer vision

Image processing

Browser ML

OCR

CSS generation

UI reconstruction

Layout detection

Frontend tooling


If you find a bug or have an idea for improving the reconstruction pipeline, feel free to open an issue or submit a pull request.


---

License

This project is currently released without a specified license.

If you plan to make the repository publicly reusable, adding an appropriate open-source license such as MIT is recommended.


---

Author

KILLERDUTCH

Built with:

HTML
CSS
JavaScript
Canvas
Computer Vision
OCR
Browser-side AI


---

Final

PixelCSS is an experiment in turning visual interfaces into structured frontend code.

SEE THE PIXELS.
UNDERSTAND THE STRUCTURE.
GENERATE THE CODE.

<p align="center">PixelCSS 2.1

<br><sub>Created by KILLERDUTCH</sub>

</p>
```
