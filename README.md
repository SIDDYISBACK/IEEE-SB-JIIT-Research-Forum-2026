# ⚡ Energy–Accuracy Trade-off Analysis of MobileNet-V2 for Edge AI Inference

<div align="center">

![IEEE](https://img.shields.io/badge/Published-IEEE%20SB%20JIIT-blue?style=for-the-badge)
![Year](https://img.shields.io/badge/Year-2026-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Published-brightgreen?style=for-the-badge)

</div>

---

## 📌 Publication Details

| Field | Info |
|-------|------|
| **Conference** | 1st Student Conference Research Forum |
| **Organized by** | IEEE Student Branch, JIIT |
| **Dates** | January 30 – February 2, 2026 |
| **Venue** | Jaypee Institute of Information Technology, Noida |
| **Paper Number** | #11 |
| **Pages** | 35–36 |
| **Certificate ID** | IEESBJIIT/RESEARCHFORUM_1/078 |

---

## 👥 Authors

| Name | GitHub | Institute |
|------|--------|-----------|
| **Sidhant Singh** | [@SIDDYISBACK](https://github.com/SIDDYISBACK) | ECE, JIIT Noida |
| **Sarthak Tripathi** | [@quarky-1]((https://github.com/quarky-1)) | ECE, JIIT Noida |

---

## 📄 Abstract

Edge AI deployments are constrained by limited energy availability and 
thermal budgets, making accuracy-centric evaluation insufficient for 
real-world systems. This paper presents a comparative meta-analysis of 
**MobileNet-V2** inference under **FP32, FP16, and INT8** numerical 
precision on Jetson-class edge hardware.

Benchmark-reported accuracy, inference latency, and power measurements 
were collected from publicly available vendor documentation and prior 
studies. Energy per inference was computed by synthesizing reported power 
and latency metrics, enabling a cross-metric evaluation that is often 
absent in isolated benchmark reports.

---

## 🔑 Key Findings

- 🟢 **FP16** reduces energy per inference by **~40%** vs FP32 with **zero accuracy loss**
- 🟡 **INT8** reduces energy per inference by **~60%** vs FP32 with **< 1% accuracy degradation**
- 🔵 **GPU-based inference** consistently dominates CPU across all precision modes and latency metrics
- 📊 Pareto frontier analysis reveals improvements in energy efficiency are tightly coupled with reduced numerical precision and hardware acceleration

---

## 📊 Results Summary

### Precision vs Performance (MobileNet-V2 on Jetson-class hardware)

| Precision | Accuracy (%) | Latency (ms) | Power (W) | Energy (mJ) |
|-----------|-------------|--------------|-----------|-------------|
| FP32      | 71.8        | 54.2         | 0.26      | 14.10       |
| FP16      | 71.8        | 30.0         | 0.28      | 8.46        |
| INT8      | 71.2        | 18.0         | 0.31      | 5.64        |

### CPU vs GPU Inference

| Mode     | Precision | Accuracy (%) | Latency (ms) | Energy (mJ) |
|----------|-----------|-------------|--------------|-------------|
| CPU-only | FP32      | 71.8        | 95.0         | 24.7        |
| GPU      | FP32      | 71.8        | 54.2         | 14.1        |
| GPU      | FP16      | 71.8        | 30.0         | 8.46        |
| GPU      | INT8      | 71.2        | 18.0         | 5.64        |

---

## 🏷️ Keywords

`Edge AI` · `MobileNet-V2` · `Model Quantization` · `Energy Efficiency` · 
`Pareto Frontier` · `FP16` · `INT8` · `Jetson` · `Deep Learning` · 
`Inference Optimization` · `NVIDIA` · `IEEE`

---

## 📜 Certificate of Participation

Both authors attended the full conference (Jan 30 – Feb 2, 2026) and 
presented this work as part of the official proceedings of the 
**1st Edition IEEE SB JIIT Student Conference Research Forum**.

Certificates are available in this repository.

---

<div align="center">

*Published in the Proceedings of the 1st Student Conference Research Forum*  
*© 2026 IEESBJIIT. All rights reserved.*

</div>
