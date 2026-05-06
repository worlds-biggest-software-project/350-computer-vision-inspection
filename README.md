# Computer Vision Inspection

> Part of the [worlds-biggest-software-project](https://github.com/worlds-biggest-software-project) initiative.
>
> An AI-native, open-source platform for custom model training and visual quality inspection on the production line.

Computer Vision Inspection is a candidate open-source platform for manufacturers, quality engineers, and inspection service providers who need to automate visual quality control without the cost and rigidity of legacy machine vision systems or the lock-in of cloud-only SaaS. It combines supervised defect detection, unsupervised anomaly detection, and natural-language defect specification in one tool.

---

## Why Computer Vision Inspection?

- Industrial machine vision systems (Cognex, Keyence, Omron) deliver reliability but start at USD 5,000–50,000+ per inspection station and require specialist integrators, putting them out of reach for many SMB manufacturers.
- Cloud SaaS platforms (Roboflow, Landing AI, AWS Lookout for Vision, Azure Custom Vision) impose recurring costs, vendor lock-in, and round-trip latency that is incompatible with high-speed inline inspection.
- Leading open-source detection frameworks such as Ultralytics YOLO are AGPL-3.0, creating IP friction for embedding in commercial products and offering no built-in annotation, anomaly detection, or production feedback tooling.
- No current platform productises natural-language defect specification, automated continuous learning from production feedback, or root-cause analysis across multi-station production lines — all identified as underserved areas in the market survey.
- Modern vision foundation models have compressed labelled-image requirements from ~50,000 (2023) to 2,000–5,000, making a data-efficient open-source alternative technically viable for the first time.

---

## Key Features

### Image Ingestion and Inspection Core

- Batch image upload, live camera streams (RTSP/USB), and REST API trigger for on-demand inspection.
- Supervised defect detection and classification with fine-tunable object detection models.
- Unsupervised anomaly detection trained from normal (good) images only — no labelled defects required.
- Pass/fail output with confidence scores, defect coordinates, and per-image result logging.

### Labelling and Training Workflow

- AI-assisted labelling with bounding box and polygon annotation and model-suggested pre-labels.
- Dataset management for image archives, defect type, confidence, timestamp, and pass/fail decision.
- Active learning pipeline that routes low-confidence predictions to a human review queue and retrains on accepted corrections.
- Synthetic defect image generation from a text description via a diffusion-model backend.

### Natural Language and Foundation Models

- Natural language defect query at inference time (e.g. "show me parts with surface scratches larger than 3mm").
- Designed to leverage open-vocabulary detection approaches (e.g. YOLO-World) and vision foundation models (SAM, DINOv2) for low-shot fine-tuning.

### Deployment and Industrial Integration

- REST inference API exposing confidence scores and defect coordinates for integration with production systems.
- Edge deployment package supporting Docker, NVIDIA Jetson, and Raspberry Pi targets.
- OPC UA result output for MES/SCADA integration.
- ONNX export pathway so trained models can run across NVIDIA, Intel OpenVINO, and ARM runtimes.

### Backlog Capabilities

- 3D inspection input from point clouds and depth maps.
- Multi-station defect correlation with root-cause suggestions across production lines.
- Compliance validation workflow for regulated industries (21 CFR Part 11 audit trail, digital signatures).
- Native barcode and OCR inspection alongside defect detection.

---

## AI-Native Advantage

The project's AI-native opportunity is grounded in five capabilities that incumbents do not yet productise: natural-language defect specification, foundation-model fine-tuning with 100–500 examples instead of thousands, automated continuous learning from production override feedback, synthetic generation of rare defect images, and multi-station inspection graphs that connect defects back to upstream process steps. Together these compress the data-collection burden that has historically been the primary barrier to deploying custom inspection models.

---

## Tech Stack & Deployment

The platform targets both self-hosted and edge deployment, with Docker containers and packaging for NVIDIA Jetson and ARM SoCs to support latency-sensitive inline inspection. Open standards in scope include ONNX for model interchange, OPC UA for MES/SCADA connectivity, GS1/ISO 15415 for barcode and 2D symbol verification where relevant, and SEMI E187/E188 for semiconductor inspection contexts. Integration is exposed through a REST inference API alongside SDK access patterns familiar to developers using Roboflow, Ultralytics, and the major cloud vision services.

---

## Market Context

The global computer vision market was valued at approximately USD 32 billion in 2026, with manufacturing quality inspection a major sub-segment growing at a double-digit CAGR (Lasting Dynamics, 2026). Incumbent pricing bifurcates between hardware-centric industrial systems at USD 5,000–50,000+ per station (Cognex, Keyence) and SaaS platforms (Roboflow from USD 249/mo; AWS Lookout at USD 4–8 per 1,000 images; Landing AI enterprise-only). Primary buyers are QA engineers and operations directors at electronics, automotive, food, and pharmaceutical manufacturers, plus third-party inspection service providers seeking to scale without adding headcount.

---

## Project Status

> This project is in the **research and specification phase**.  
> Contributions, feedback, and domain expertise are welcome.

---

## Contributing

We welcome contributions from developers, domain experts, and potential users.
See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Important:** All contributions must be your own original work or clearly attributed
open-source material with a compatible licence. Copyright infringement and licence
violations will not be tolerated and will result in immediate removal of the offending
contribution. If you are unsure whether a piece of code, text, or other material is
safe to contribute, open an issue and ask before submitting.

---

## Licence

Licence to be determined. See [discussion](#) for context.
