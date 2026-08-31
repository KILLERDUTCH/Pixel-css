PixelCSS 2.1

Screenshot → Pixels → AI → HTML/CSS

PixelCSS is a browser-based UI reconstruction tool that analyzes screenshots and turns visual information into a structured, editable HTML/CSS interface.

It combines traditional pixel analysis with browser-side AI to make the reconstruction process more intelligent — without requiring a backend.

---

✦ What is PixelCSS?

Recreating a web interface from a screenshot usually means manually estimating:

- colors
- spacing
- borders
- radius
- layout
- typography
- components
- positioning

PixelCSS automates a large part of that process.

Give it a screenshot.

PixelCSS analyzes it.

Then it builds an editable HTML/CSS starting point.

Screenshot
     │
     ▼
┌─────────────────┐
│  Pixel Analyzer │
└────────┬────────┘
         │
         ├── Colors
         ├── Geometry
         ├── Contrast
         └── Layout
                  │
                  ▼
          ┌──────────────┐
          │   Vision AI  │
          └──────┬───────┘
                 │
                 ├── Objects
                 └── Confidence
                         │
                         ▼
                    ┌─────────┐
                    │   OCR   │
                    └────┬────┘
                         │
                         ▼
                 Structured Result
                         │
                         ▼
                HTML + CSS Generator
                         │
                         ▼
                    Live Preview

---

Features

Pixel Analysis

PixelCSS extracts visual information directly from the uploaded image.

- Dominant color extraction
- Average image color
- Contrast estimation
- Edge/change detection
- Layout heuristics
- Border-radius estimation
- Basic component inference

Browser-side AI

PixelCSS can run AI models directly in the browser using Transformers.js.

Current AI pipeline:

- Object Detection
- OCR
- Confidence scoring
- AI result integration
- Browser-side model caching

No application backend is required.

HTML/CSS Generation

The analyzer converts its findings into a clean editable starting point.

Generated output includes:

- HTML
- CSS
- Combined standalone document
- Structured JSON
- Live preview

The generated code is intentionally editable rather than being treated as a final pixel-perfect copy.

---

Why PixelCSS?

Most screenshot-to-code tools hide the interesting part behind an API.

PixelCSS takes a different approach.

The project is designed around the idea of:

«Understanding the pixels before generating the code.»

Instead of blindly generating markup, PixelCSS first builds a representation of the screenshot:

Image
  ↓
Pixel data
  ↓
Visual features
  ↓
Layout inference
  ↓
AI detection
  ↓
Structured data
  ↓
Code generation

This makes the project useful not only as a tool, but also as an experiment in browser-based computer vision and UI reconstruction.

---

Architecture

┌─────────────────────────────────────────┐
│              PixelCSS 2.1               │
├─────────────────────────────────────────┤
│                                         │
│  Screenshot                             │
│      │                                  │
│      ▼                                  │
│  Canvas / ImageData                     │
│      │                                  │
│      ├───────────────┐                  │
│      ▼               ▼                  │
│ Pixel Analysis    Vision AI             │
│      │               │                  │
│      │               ├── Objects        │
│      │               └── Confidence     │
│      │                                  │
│      └──────────┐                       │
│                 ▼                       │
│                OCR                      │
│                 │                       │
│                 ▼                       │
│          Structured Result              │
│                 │                       │
│                 ▼                       │
│          HTML/CSS Generator             │
│                 │                       │
│          ┌──────┴──────┐                │
│          ▼             ▼                │
│        Code        Live Preview         │
│                                         │
└─────────────────────────────────────────┘

---

Tech Stack

PixelCSS is intentionally lightweight.

Technology| Purpose
HTML5| Application structure
CSS3| Interface & generated styling
JavaScript| Core engine
Canvas API| Pixel processing
ImageData API| Raw pixel analysis
Transformers.js| Browser-side ML
DETR| Object detection
TrOCR| OCR
WebAssembly| Local model execution

No framework is required.

No build system is required.

No database is required.

No backend is required for the core application.

---

AI Models

PixelCSS currently uses browser-compatible models through Transformers.js.

Object Detection

Xenova/detr-resnet-50

Used to identify visual objects and provide bounding-box information with confidence scores.

OCR

Xenova/trocr-small-printed

Used for extracting text from visual content.

Models are downloaded when required and can be cached by the browser.

«Model performance depends heavily on the screenshot, device, browser, and available resources.»

---

Running Locally

Because browser ML modules and model loading work better through an HTTP server, don't open the project directly with:

file://

Instead, use a local server.

VS Code

Install Live Server, then open:

index.html

with Live Server.

Python

python -m http.server 8000

Then open:

http://localhost:8000

---

Usage

1. Upload

Drop a screenshot into PixelCSS or select one manually.

2. Analyze

Run the pixel analyzer.

PixelCSS extracts:

Colors
Geometry
Contrast
Layout
Components
Radius

3. Run AI

Run the browser-side AI pipeline.

The system performs:

Vision Detection
        +
OCR

4. Inspect

Review the generated:

- HTML
- CSS
- JSON
- Combined document

5. Export

Copy the generated code and continue editing it like a normal web project.

---

Example Result

A screenshot might produce a structure similar to:

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
    "vision": [
        {
            "label": "laptop",
            "score": 87
        }
    ]
}

That structured representation is then used by the code generator.

---

Project Goals

PixelCSS is not trying to replace a professional frontend developer.

The goal is different:

Reduce the distance between a visual reference and editable code.

The project explores how much of a UI can be reconstructed using:

- deterministic image analysis
- heuristics
- computer vision
- OCR
- structured data
- procedural code generation

---

Limitations

PixelCSS is an experimental reconstruction engine.

It will not perfectly reproduce every screenshot.

Complex interfaces can contain information that cannot reliably be inferred from pixels alone.

For example:

- exact font identification
- hidden DOM structure
- semantic HTML
- responsive behavior
- interactions
- animations
- inaccessible content
- complex nested layouts

AI detection can also produce incorrect classifications.

The generated code should therefore be treated as a starting point, not a guaranteed final implementation.

---

Roadmap

2.2

- [ ] Better UI component detection
- [ ] Improved text region detection
- [ ] Better bounding-box reconstruction
- [ ] More accurate spacing inference
- [ ] Typography estimation
- [ ] Better responsive layout generation

2.5

- [ ] Component tree generation
- [ ] Grid/Flexbox inference
- [ ] Improved CSS reconstruction
- [ ] Region-based OCR
- [ ] Smarter visual similarity scoring

3.0

- [ ] Advanced Vision-Language model
- [ ] Semantic UI understanding
- [ ] Component-level reconstruction
- [ ] Multi-pass code generation
- [ ] Visual diff / similarity mode

---

Performance

AI models can be relatively large.

The first AI execution may take longer because the browser needs to download and initialize the models.

After caching, subsequent executions can be significantly faster.

Performance depends on:

- CPU
- RAM
- browser
- screenshot resolution
- WebAssembly performance
- model size

For large screenshots, PixelCSS downsamples the image for some pixel-analysis operations to keep processing reasonable.

---

Privacy

PixelCSS is designed around browser-side processing.

Screenshots are processed locally by the application.

There is no required application backend for the core analyzer.

AI inference is also designed to run locally in the browser.

This means the project can be useful for analyzing screenshots without automatically uploading them to a remote application server.

---

Project Structure

PixelCSS/
│
├── index.html
│
└── README.md

The current version intentionally keeps the project as a single-file application.

This makes it easy to:

- fork
- inspect
- modify
- experiment with
- deploy

---

Contributing

Ideas, improvements, experiments and pull requests are welcome.

If you're interested in:

- computer vision
- frontend tooling
- browser ML
- CSS generation
- OCR
- image processing
- UI reconstruction

this project is a good place to experiment.

---

License

Add your preferred license here.

For example:

MIT License

---

Author

KILLERDUTCH

Built as an experiment in combining frontend engineering, pixel analysis and browser-based machine learning.

HTML
CSS
JavaScript
+
Computer Vision
+
AI
=
PixelCSS

---

<p align="center">PixelCSS 2.1

<sub>See the pixels. Understand the structure. Generate the code.</sub>

</p>
