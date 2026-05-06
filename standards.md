# Standards & API Reference

> Project: Computer Vision Inspection · Generated: 2026-05-04

## Industry Standards & Specifications

### ISO Standards

**ISO/IEC 15415 — 2D bar code symbol print quality test specification**
- URL: https://www.iso.org/standard/76360.html
- Grading standard for 2D barcodes (DataMatrix, QR Code) used when visual inspection includes label and marking verification. Defines the quality parameters (symbol contrast, modulation, reflectance margin, axial non-uniformity, grid non-uniformity, unused error correction) that inspection systems must evaluate.

**ISO/IEC 15416 — Bar code print quality test specification — Linear symbols**
- URL: https://www.iso.org/standard/75480.html
- Companion to ISO 15415 for 1D barcodes. Used in product traceability inspection to verify that barcodes on manufactured goods meet printability standards before shipment.

**ISO 9001:2015 — Quality management systems — Requirements**
- URL: https://www.iso.org/standard/62085.html
- The universal quality management system standard. AI-driven inspection systems are deployed as part of ISO 9001 control plans; inspection results must be documented, traceable, and available for management review. Outputs from any inspection platform must satisfy ISO 9001 record-keeping requirements.

**ISO 13372:2012 — Condition monitoring and diagnostics of machines — Vocabulary**
- URL: https://www.iso.org/standard/57829.html
- Relevant when visual inspection is integrated with a predictive maintenance platform. Defines terminology used to describe machine condition, faults, and monitoring methods. Ensures consistent language between the inspection layer and the wider asset management system.

**ISO/IEC 62541 (OPC UA) — OPC Unified Architecture**
- URL: https://webstore.iec.ch/publication/61114
- The IEC adoption of OPC UA. Multi-part standard covering services, information model, security, historical access, and the Machine Vision companion specification. Part 10 (published 2025) covers the latest additions. The de facto industrial communication standard for connecting vision inspection systems to MES, SCADA, and PLCs in Industry 4.0 environments.

**SEMI E187 — Specification for CIM Framework Substrate/Workpiece Transfer and Handling**
- URL: https://www.semi.org/en/products-services/standards
- Semiconductor industry standard governing wafer and reticle transfer and inspection protocols. Relevant for wafer defect inspection use cases in semiconductor fabs. Defines data exchange formats between inspection equipment and fab management systems.

### W3C & IETF Standards

**RFC 7231 — Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content**
- URL: https://datatracker.ietf.org/doc/html/rfc7231
- Foundational HTTP semantics standard governing REST API design. Inspection platform REST APIs for image submission, inference results, and model management must conform to HTTP semantics for interoperability with industrial automation systems and cloud integrations.

**RFC 8288 — Web Linking**
- URL: https://datatracker.ietf.org/doc/html/rfc8288
- Defines the `Link` header for hypermedia APIs. Used in well-designed REST APIs to express relationships between resources (e.g., linking an inspection result to the model version that produced it, or to the archived image).

**RFC 6749 — The OAuth 2.0 Authorization Framework**
- URL: https://datatracker.ietf.org/doc/html/rfc6749
- OAuth 2.0 is the standard mechanism for authorising third-party integrations (MES systems, ERP, quality dashboards) to access inspection platform APIs without sharing credentials. Mandatory for any multi-tenant SaaS deployment.

**RFC 7519 — JSON Web Token (JWT)**
- URL: https://datatracker.ietf.org/doc/html/rfc7519
- JWT is the standard bearer token format used with OAuth 2.0 / OpenID Connect for stateless API authentication. Inspection platform APIs should issue JWTs scoped to inspection workspace and model version to control access.

**W3C WebRTC**
- URL: https://www.w3.org/TR/webrtc/
- Peer-to-peer real-time communication API used in browser-based live inspection dashboards. Enables direct browser-to-camera stream for real-time inspection without server round-trips, as implemented in Roboflow Workflows.

### Data Model & API Specifications

**ONNX (Open Neural Network Exchange) — Version 1.x / opset 20+**
- URL: https://onnx.ai / https://github.com/onnx/onnx
- The de facto model interchange format for computer vision. Trained inspection models (from PyTorch, TensorFlow, JAX) are exported to ONNX for deployment on NVIDIA TensorRT, Intel OpenVINO, ARM NN, and Microsoft ONNX Runtime across GPU, CPU, and NPU targets. Any platform that produces trained models should support ONNX export as a first-class output.

**OpenAPI Specification 3.1 (OAS 3.1)**
- URL: https://spec.openapis.org/oas/v3.1.0
- The standard for documenting REST APIs. Inspection platform APIs should be described in OpenAPI 3.1 to enable SDK auto-generation (Python, TypeScript, Go) and integration with API management gateways (Kong, AWS API Gateway, Azure APIM). Supports JSON Schema for request/response validation.

**JSON Schema (draft 2020-12)**
- URL: https://json-schema.org/draft/2020-12/json-schema-core.html
- Standard for defining the structure of JSON documents. Used to define inspection result payloads (defect type, bounding box, confidence, image reference, timestamp) and dataset annotation formats (COCO JSON, custom schemas).

**COCO Dataset Format (de facto)**
- URL: https://cocodataset.org/#format-data
- While not a formal ISO/IETF standard, the COCO JSON annotation format is the de facto interchange format for object detection and instance segmentation datasets. All major annotation tools (CVAT, Label Studio, Roboflow) and training frameworks (Ultralytics, Detectron2, MMDetection) support COCO JSON natively.

**GStreamer Pipeline API (de facto)**
- URL: https://gstreamer.freedesktop.org/documentation/
- Open-source multimedia pipeline framework used by NVIDIA DeepStream and other industrial vision systems as the underlying stream processing engine. Relevant for building real-time multi-camera inspection pipelines; GStreamer plugins provide hardware-accelerated decode, colour conversion, and inference integration.

### Security & Authentication Standards

**OAuth 2.0 / OpenID Connect (OIDC)**
- URL: https://openid.net/connect/
- OIDC extends OAuth 2.0 with user identity. Required for any multi-tenant SaaS inspection platform that connects to enterprise identity providers (Azure AD, Okta, Google Workspace) to authenticate quality engineers and control access to models and workspaces.

**OWASP API Security Top 10 (2023)**
- URL: https://owasp.org/www-project-api-security/
- Authoritative guide for securing REST APIs. Particularly relevant for inspection platforms that expose model inference endpoints: Broken Object Level Authorization (BOLA), Broken Authentication, Unrestricted Resource Consumption (rate limiting for inference endpoints), and Server-Side Request Forgery (when accepting image URLs).

**NIST SP 800-53 Rev. 5 — Security and Privacy Controls for Information Systems**
- URL: https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final
- Required framework for inspection systems deployed in US federal manufacturing or defence supply chains. Defines controls for access management, audit logging, configuration management, and incident response.

**21 CFR Part 11 — Electronic Records; Electronic Signatures**
- URL: https://www.ecfr.gov/current/title-21/chapter-I/subchapter-A/part-11
- FDA regulation governing electronic records in pharmaceutical, medical device, and food manufacturing. Inspection platforms used in regulated manufacturing must implement: audit trails for model training and deployment decisions, digital signatures for inspection approvals, and tamper-evident result logs.

**IEC 62443 — Industrial Automation and Control Systems (IACS) Security**
- URL: https://www.iec.ch/iec62443
- Cybersecurity standard for industrial control system environments. Relevant when inspection systems are connected to plant networks; defines security levels (SL 1–4) and zone/conduit models for network segmentation between OT (operational technology) and IT networks.

### MCP Server Specifications

**Model Context Protocol (MCP)**
- URL: https://spec.modelcontextprotocol.io/
- Anthropic's open protocol for connecting AI models to data sources and tools. Directly applicable to a next-generation inspection platform: an MCP server exposing inspection models would allow LLM-based quality agents to query inspection results, trigger re-inspection, or describe defects in natural language. The protocol defines resources (inspection images, result datasets), tools (run inference, annotate image), and prompts (defect summary templates).

**OPC UA Machine Vision Companion Specification (Part 1–3)**
- URL: https://reference.opcfoundation.org/MachineVision/v100/docs/
- OPC Foundation companion spec that defines a standardised information model for all machine vision systems — from simple sensors to complex AI inspection systems. Defines the infrastructure layer (generic machine vision system abstraction), recipe management (inspection configuration), result management (defect data output model), and control/configuration interfaces. Implementing this spec enables plug-and-work integration with any OPC UA-capable MES or SCADA without custom integration code.

---

## Similar Products — Developer Documentation & APIs

### Roboflow

- **Description:** End-to-end computer vision platform covering dataset management, annotation, model training, and multi-target deployment with a REST API and Python SDK.
- **API Documentation:** https://docs.roboflow.com/api-reference/introduction
- **SDKs/Libraries:** Python — https://github.com/roboflow/roboflow-python (PyPI: `roboflow`); Inference engine — https://github.com/roboflow/inference
- **Developer Guide:** https://docs.roboflow.com/developer
- **Standards:** REST/JSON; OpenAPI-documented endpoints; COCO JSON for dataset import/export
- **Authentication:** API Key (passed as query parameter or Authorization header)

### Landing AI (LandingLens)

- **Description:** No-code visual inspection platform for manufacturing quality control, offering supervised classification, detection, and segmentation with a data-efficient training workflow.
- **API Documentation:** https://landing-ai.github.io/public-rest-api/fastapi/
- **SDKs/Libraries:** Python — https://github.com/landing-ai/landingai-python; TypeScript library available (C# planned)
- **Developer Guide:** https://landing-ai.github.io/landingai-python/inferences/getting-started/
- **Standards:** REST/JSON; OpenAPI-documented endpoints
- **Authentication:** API Key (obtained from LandingLens console)

### AWS Lookout for Vision

- **Description:** Managed anomaly detection service that trains on normal-image-only datasets to detect industrial defects, with edge packaging via AWS IoT Greengrass.
- **API Documentation:** https://docs.aws.amazon.com/lookout-for-vision/latest/APIReference/
- **SDKs/Libraries:** Python/Boto3 — https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/lookoutvision.html; JavaScript — https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-lookoutvision/; Go, Java, SAP ABAP also available
- **Developer Guide:** https://aws.amazon.com/lookout-for-vision/resources/
- **Standards:** AWS REST API (Signature V4); JSON payloads
- **Authentication:** AWS IAM (Signature V4 request signing)

### Azure AI Custom Vision / Computer Vision

- **Description:** Managed computer vision service for training custom classification and object detection models, with model export to ONNX/CoreML/TFLite for edge deployment.
- **API Documentation:** https://learn.microsoft.com/en-us/azure/ai-services/custom-vision-service/
- **SDKs/Libraries:** Python — `azure-cognitiveservices-vision-customvision`; C#, Java, JavaScript, Go, Ruby available
- **Developer Guide:** https://learn.microsoft.com/en-us/azure/ai-services/computer-vision/quickstarts-sdk/image-analysis-client-library
- **Standards:** REST/JSON; OpenAPI-documented; ONNX export format
- **Authentication:** Azure AD / API Key

### Google Cloud Vision AI

- **Description:** Managed image analysis service with pre-built models (label detection, OCR, object detection) and AutoML Vision for custom model training with export capability.
- **API Documentation:** https://cloud.google.com/vision/docs/reference/rest
- **SDKs/Libraries:** Python — `google-cloud-vision`; Node.js, Go, Java, PHP, Ruby, C# available
- **Developer Guide:** https://cloud.google.com/vision/docs/quickstart-client-libraries
- **Standards:** REST/JSON and gRPC; Protocol Buffers for gRPC interface
- **Authentication:** Google Cloud IAM / Service Account key / OAuth 2.0

### Cognex VisionPro (Developer)

- **Description:** PC-based vision software combining rule-based tools (PatMax) and deep learning for industrial inspection; primary developer interface is a .NET SDK and QuickBuild visual programming environment.
- **API Documentation:** https://support.cognex.com/en/downloads/detail/1/1152/10 (requires Cognex login)
- **SDKs/Libraries:** .NET SDK (C#/VB.NET primary); REST API for modern integrations
- **Developer Guide:** https://www.cognex.com/en/products/machine-vision-software/visionpro-software
- **Standards:** OPC UA for MES/SCADA; EtherNet/IP, PROFINET industrial fieldbus
- **Authentication:** Proprietary; network-level security at the factory OT layer

### NVIDIA TAO Toolkit

- **Description:** GPU-accelerated model fine-tuning and optimisation toolkit for vision foundation models; paired with DeepStream for real-time multi-stream inference pipeline deployment.
- **API Documentation:** https://docs.nvidia.com/tao/tao-toolkit/
- **SDKs/Libraries:** Python (primary); CLI; NGC model registry — https://catalog.ngc.nvidia.com/
- **Developer Guide:** https://developer.nvidia.com/blog/build-a-real-time-visual-inspection-pipeline-with-nvidia-tao-6-and-nvidia-deepstream-8/
- **Standards:** ONNX export; NVIDIA TensorRT runtime; DeepStream GStreamer pipeline API
- **Authentication:** NVIDIA NGC API Key for model registry access

### Ultralytics HUB / YOLO

- **Description:** State-of-the-art real-time object detection framework (YOLO series through YOLO26) with cloud HUB for dataset management, training, and deployment, plus a Python-first API.
- **API Documentation:** https://docs.ultralytics.com/ and https://hub.ultralytics.com/
- **SDKs/Libraries:** Python — `ultralytics` (PyPI); CLI; REST API via HUB
- **Developer Guide:** https://docs.ultralytics.com/quickstart/
- **Standards:** ONNX, CoreML, TFLite, TensorRT export formats; COCO JSON dataset format
- **Authentication:** Ultralytics HUB API Key

### OpenVINO (Intel)

- **Description:** Intel's open-source toolkit for optimising and deploying vision models on Intel CPUs, integrated GPUs, VPUs, and FPGAs — the primary ONNX-to-edge deployment path for non-NVIDIA hardware.
- **API Documentation:** https://docs.openvino.ai/
- **SDKs/Libraries:** Python — `openvino` (PyPI); C++; Node.js; Java
- **Developer Guide:** https://docs.openvino.ai/2024/get-started.html
- **Standards:** ONNX ingestion; OpenVINO IR format; REST and gRPC via OpenVINO Model Server
- **Authentication:** API Key via OpenVINO Model Server (self-hosted)

---

## Notes

**Evolving areas:**

- **OPC UA Machine Vision Companion Specification** (Parts 1–3) is still relatively new and not yet universally implemented. Most current vision systems expose OPC UA at the data transport level but do not implement the full companion spec object model. As adoption grows, platforms implementing the full spec will have a significant interoperability advantage.

- **MCP for industrial AI**: The Model Context Protocol is not yet used in any production industrial inspection platform, but represents a natural interface for connecting LLM-based quality agents to inspection result stores and model registries. Early implementation would be a meaningful differentiator.

- **Synthetic defect generation**: Diffusion-model-based defect synthesis (DefectFill, CVPR 2025 generative inspection workshop) is rapidly maturing but has no standardised data format for synthetic defect specifications. An open schema for describing defect geometry, texture, and placement parameters would accelerate community adoption.

- **ONNX opset maturity**: ONNX opset 20+ (2025–2026) has substantially improved support for transformer-based architectures (attention operators, layer normalisation). Projects targeting foundation model fine-tuning for inspection should validate ONNX export compatibility with the specific opset supported by their target runtime (TensorRT 9.x, OpenVINO 2024.x).
