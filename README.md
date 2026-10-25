# EdgeInspect

**Real-Time Edge AI Quality Inspection for Smart Manufacturing**

EdgeInspect is a computer-vision system that detects manufacturing defects, classifies their severity, and produces an immediate quality-control decision (**Pass / Review / Reject**) at the edge, on or near the production line.

| | |
|---|---|
| **Hackathon Theme** | AI in Hardware & Manufacturing |
| **Sub-theme** | Computer Vision & Smart Quality Inspection |
| **Core Technology** | Computer Vision, Object Detection, Edge AI, Real-time Analytics |
| **Primary Users** | Manufacturing operators, quality inspectors, production engineers |

---

## Table of Contents

- [Problem Statement](#problem-statement)
- [Solution](#solution)
- [Key Features](#key-features)
- [System Workflow](#system-workflow)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Implementation Plan](#implementation-plan)
- [Evaluation Metrics](#evaluation-metrics)
- [Safety and Human-in-the-Loop Design](#safety-and-human-in-the-loop-design)
- [Scalability and Future Work](#scalability-and-future-work)
- [Innovation Advantage](#innovation-advantage)
- [Limitations](#limitations)
- [Team](#team)
- [License](#license)

---

## Problem Statement

Manual quality inspection in manufacturing is time-consuming, inconsistent, hard to scale, and dependent on continuous human attention. Small defects such as cracks, scratches, missing components, incorrect assembly, or surface abnormalities can be overlooked. This leads to rejected products, rework, material waste, production delays, and safety or reliability issues.

> **In one sentence:** Manufacturing units need a fast, consistent, and scalable way to detect product defects in real time without relying entirely on manual inspection.

## Solution

EdgeInspect places an AI-powered vision system directly on or near the production line. A camera captures each product, a computer-vision model analyzes the image, and the system identifies defects in real time. Results are shown on a dashboard so an operator can immediately see whether a product passes inspection or needs rework or rejection.

## Key Features

- **Real-time capture and preprocessing** of images from a production-line camera
- **AI-based defect detection** using a trained object-detection model (e.g., YOLO)
- **Defect classification, localization, and confidence score** for every detection
- **Severity-based decision:** Pass, Review/Rework, or Reject
- **Visual dashboard** with inspected units, detected defects, and quality statistics
- **Edge inference** for low latency and operation even with limited cloud connectivity
- **Inspection history and analytics** to identify recurring defect patterns

## System Workflow

```
Camera → Image Preprocessing → AI/YOLO Inference → Defect Detection
       → Severity Analysis → Quality Decision → Dashboard / Alert
```

### User Journey

| Step | Stage | Output |
|---|---|---|
| 1 | Product | Manufactured unit arrives at the station |
| 2 | Capture | Camera image |
| 3 | AI Analysis | Defect type, location, confidence |
| 4 | Decision | Pass / Review / Reject |
| 5 | Analytics | Results logged to the quality dashboard |

**Before EdgeInspect:** product arrives → inspector checks visually → defect may be missed → decision recorded manually → recurring problems are hard to analyze.

**With EdgeInspect:** product arrives → camera captures image → AI analyzes it → defect is localized and classified → Pass/Review/Reject decision → dashboard records the result → quality team analyzes recurring defects.

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Python |
| Image processing | OpenCV |
| Model | YOLO / PyTorch |
| Backend / API | FastAPI |
| Frontend | HTML, CSS, JavaScript |
| Database | SQLite / PostgreSQL |
| Deployment | Edge-capable computing device |

## Project Structure

> Suggested layout. Adjust it to match your actual repository.

```
EdgeInspect/
├── data/                  # Datasets (raw, annotated, train/val/test splits)
├── models/                # Trained weights and exported/optimized models
├── notebooks/             # Training and evaluation experiments
├── src/
│   ├── capture/           # Camera / image-source handling
│   ├── preprocessing/     # Image preprocessing utilities
│   ├── inference/         # Model loading and defect detection
│   ├── decision/          # Severity analysis and Pass/Review/Reject logic
│   ├── api/               # FastAPI application
│   └── db/                # Database models and inspection history
├── dashboard/             # Frontend (HTML/CSS/JS)
├── docs/                  # Architecture diagram, evaluation report
├── requirements.txt
└── README.md
```

## Getting Started

> The commands below are a template. Update file names and paths to match your code.

### Prerequisites

- Python 3.9+
- A webcam, industrial camera, or a folder of sample product images
- (Optional) An edge-capable device for deployment

### Installation

```bash
# Clone the repository
git clone https://github.com/<your-username>/EdgeInspect.git
cd EdgeInspect

# Create and activate a virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Run the Inspection API

```bash
uvicorn src.api.main:app --reload
```

### Open the Dashboard

Open `dashboard/index.html` in your browser, or visit the address served by the API (e.g., `http://localhost:8000`).

### Run a Demo

```bash
python src/inference/demo.py --source path/to/sample_images/
```

## Implementation Plan

| Phase | Focus | Description |
|---|---|---|
| 1 | **Data** | Collect or curate images of acceptable products and representative defects; annotate defect classes |
| 2 | **Model** | Train or fine-tune a lightweight object-detection model for the selected inspection task |
| 3 | **Edge deployment** | Optimize the model for low-latency inference on an edge-capable device |
| 4 | **Application** | Build the dashboard and API showing detections, confidence, defect type, and decision |
| 5 | **Demonstration** | Run sample products through the system and show real-time detection and automated decisions |

## Evaluation Metrics

The prototype is evaluated on:

- Detection **precision** and **recall**
- **Inference latency**
- **False-positive** and **false-negative** rates
- **Throughput** (units per minute)
- Percentage of cases **correctly routed** to Pass / Review / Reject

### Results

| Metric | Value |
|---|---|
| Precision | _TBD_ |
| Recall | _TBD_ |
| Inference latency | _TBD_ |
| False-positive rate | _TBD_ |
| False-negative rate | _TBD_ |
| Throughput (units/min) | _TBD_ |
| Correct routing (%) | _TBD_ |

## Safety and Human-in-the-Loop Design

EdgeInspect is a **decision-support and automated inspection layer**, not an uncontrolled replacement for safety-critical human decisions. Low-confidence detections can be routed to a human inspector for review.

- **Consistency:** the same detection criteria are applied to every product
- **Early defect detection:** visible defects are caught before products move further down the line
- **Reduced repetitive workload:** assists inspectors with high-volume visual checking
- **Low latency:** edge inference reduces dependence on round trips to a cloud service
- **Human-in-the-loop:** ambiguous cases are flagged for manual verification
- **Traceability:** results are stored for quality analysis and process improvement

## Scalability and Future Work

The architecture can be adapted to other manufacturing environments by retraining or fine-tuning the model for new products and defect classes. Planned extensions:

- Multiple cameras and multiple inspection stations
- Integration with PLCs, conveyors, robotic arms, or industrial control systems for automated sorting
- Predictive analytics to find recurring defect patterns and possible process causes
- Model optimization and specialized accelerators for higher edge throughput
- Product-specific inspection profiles selected automatically
- Integration with MES and quality-management workflows
- Dimensional and assembly verification using depth cameras or additional sensors

## Innovation Advantage

EdgeInspect delivers a practical **quality-inspection workflow**, not just a defect-detection model:

- **Edge-first design:** fast local decisions with less reliance on cloud connectivity
- **Actionable output:** reports where the defect is, what type it is, how confident the model is, and the suggested action
- **Human-AI collaboration:** uncertain cases are escalated instead of forced into an automated decision
- **Adaptable architecture:** the same platform can be trained for different products and processes

## Limitations

This is a hackathon prototype for demonstration and validation. Industrial deployment would require domain-specific datasets, calibrated cameras, environmental testing, safety validation, and integration testing with the target production equipment.
