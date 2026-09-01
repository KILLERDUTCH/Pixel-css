# PixelCSS 2.1

<p align="center">
  <strong>PixelCSS</strong><br>
  <sub>Screenshot → Pixel Analysis → AI → HTML/CSS</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Version-2.1-8b5cf6?style=for-the-badge" alt="Version">
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5">
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
  <img src="https://img.shields.io/badge/Browser--AI-Transformers.js-8b5cf6?style=for-the-badge" alt="Browser AI">
</p>

---

## Overview

**PixelCSS** is a browser-based screenshot analysis and UI reconstruction engine built entirely with **HTML, CSS, and JavaScript**.

It analyzes screenshots at the pixel level, extracts visual properties, optionally uses browser-side AI for object detection and OCR, and generates editable HTML/CSS from the collected data.

> **Don't just look at the screenshot. Analyze it.**

PixelCSS is designed as a developer-focused experiment in visual reconstruction, combining deterministic pixel analysis with browser-side machine learning.

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
    ┌────┴────┐
    │         │
    ▼         ▼
 Colors    Geometry
    │         │
    └────┬────┘
         │
         ▼
┌─────────────────┐
│  Layout Engine  │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│    Vision AI    │
└────────┬────────┘
         │
    ┌────┴────┐
    ▼         ▼
Detection    OCR
    │         │
    └────┬────┘
         │
         ▼
┌─────────────────┐
│ Structured Data │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ HTML/CSS Engine │
└────────┬────────┘
         │
    ┌────┴────┐
    ▼         ▼
 HTML/CSS   Preview
