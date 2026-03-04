# QC Detector

<div class="project-hero qc-hero">
  <div class="project-hero-content">
    <div class="project-hero-badge">Computer Vision · Industrial AI · Python</div>
    <h1>🔍 QC Detector System</h1>
    <p class="project-tagline">AI-powered Quality Control for manufacturing — detecting product size, shape, and color in real-time with sub-pixel measurement accuracy.</p>
    <div class="project-links">
      <a href="https://github.com/Aditya1614/QC-Detector" target="_blank" class="btn-primary">View on GitHub ↗</a>
    </div>
  </div>
</div>

---

## Overview

QC Detector is a **production-grade quality control automation system** developed for footwear manufacturing. It uses multiple AI detection pipelines to measure product dimensions in real-time, comparing them against SKU profiles and tolerances — replacing manual inspection with computer vision.

> Built as part of my initiative at **PT Porto Indonesia Sejahtera** to automate quality control using AI.

---

## Core Capabilities

<div class="card-grid">
  <div class="feature-card">
    <span class="card-icon">📸</span>
    <h3>Multi-Source Detection</h3>
    <p>Supports live camera measurement, static photo analysis, and batch video file processing — all from a single unified GUI.</p>
  </div>
  <div class="feature-card">
    <span class="card-icon">🤖</span>
    <h3>AI Detection Pipeline</h3>
    <p>Four detection modes from traditional OpenCV to the most advanced two-model AI pipeline using YOLOv8x + SAM for pixel-perfect masks.</p>
  </div>
  <div class="feature-card">
    <span class="card-icon">🏭</span>
    <h3>Industrial Integration</h3>
    <p>PLC/Modbus RTU communication for factory-floor automation triggers. Results stored in PostgreSQL for traceability and reporting.</p>
  </div>
  <div class="feature-card">
    <span class="card-icon">📐</span>
    <h3>Metrology-Grade Accuracy</h3>
    <p>Sub-pixel edge detection via Sobel gradients, PCA endpoint analysis, and ArUco marker auto-calibration for real-world mm measurements.</p>
  </div>
</div>

---

## AI Detection Modes

=== "Standard (Contour)"
    Traditional OpenCV approach using **HSV color filtering** and contour detection. Fast, lightweight, ideal for controlled lighting environments.

    - HSV-based color masking
    - OpenCV contour hierarchy
    - Configurable thresholds per SKU

=== "YOLOv8n-seg (AI)"
    **Deep learning segmentation** using YOLOv8 nano-segmentation model. Hybrid ROI approach combines YOLO's object detection with contour refinement.

    - YOLOv8 nano inference
    - Pixel-level segmentation masks
    - ROI-constrained contour fallback

=== "FastSAM (AI)"
    **Fast Segment Anything Model** — universal object detection without class-specific training. Works on unseen product types without retraining.

    - Zero-shot segmentation
    - Universal mask generation
    - No product-specific training required

=== "Advanced Multi-AI (YOLOv8x + SAM)"
    The most powerful mode: a **two-model pipeline** where YOLOv8 Extra-Large detects the object bounding box, then SAM produces a pixel-perfect segmentation mask inside the detected region.

    - YOLOv8x-large for accurate detection
    - SAM for boundary-precise masks
    - State-of-the-art measurement accuracy

---

## Measurement Technology

### Sub-Pixel Edge Detection

- Sobel gradient magnitude for sub-pixel precision
- Gradient direction coherence analysis
- Directional edge bridging to prevent over-segmentation

### PCA-Based Endpoint Detection

- Principal Component Analysis on contour points for principal axis alignment
- Linear regression on projected endpoints for robust measurement
- Resistant to noise and manufacturing variations

### Calibration Systems

- **ArUco marker auto-calibration** — real-time mm/pixel ratio from reference markers
- **Lens distortion compensation** — corrects fisheye/barrel distortion
- **Real-time ratio updates** — recalibrates on every frame

---

## Tech Stack

| Layer | Technology |
|---|---|
| GUI | PySide6 (Qt for Python) |
| Computer Vision | OpenCV, YOLOv8 (Ultralytics), FastSAM, SAM |
| Measurement | Sobel, PCA, ArUco Markers |
| Industrial I/O | Modbus RTU (PLC integration) |
| Database | PostgreSQL |
| ML Framework | PyTorch |
| Language | Python 3.10+ |

---

!!! success "Production Impact"
    Deployed as part of an internal initiative at **PT Porto Indonesia Sejahtera**, this system reduced manual QC inspection time, improved measurement consistency, and enabled real-time defect detection on the production line.
