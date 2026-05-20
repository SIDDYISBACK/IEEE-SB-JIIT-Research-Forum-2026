# Energy–Accuracy Trade-off Analysis of MobileNet-V2 for Edge AI Inference

<div align="center">

![Published](https://img.shields.io/badge/Published-IEEE%20SB%20JIIT%20Proceedings-003087?style=flat-square&logo=ieee)
![Year](https://img.shields.io/badge/Year-2026-0a7cc1?style=flat-square)
![Domain](https://img.shields.io/badge/Domain-Edge%20AI%20%7C%20Deep%20Learning-orange?style=flat-square)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat-square)
![License](https://img.shields.io/badge/License-All%20Rights%20Reserved-red?style=flat-square)

</div>

<div align="center">

**Sarthak Tripathi · Sidhant Singh**  
*Department of Electronics and Communication Engineering*  
*Jaypee Institute of Information Technology, Noida, India*

</div>

---

> **Cite as:** S. Tripathi and S. Singh, "Energy–Accuracy Trade-off Analysis of MobileNet-V2 for Edge AI Inference," in *Proceedings of the 1st Student Conference Research Forum*, IEEE Student Branch JIIT, Noida, India, Jan.–Feb. 2026, pp. 35–36.

---

## Table of Contents

- [Publication Details](#-publication-details)
- [Abstract](#-abstract)
- [Background & Motivation](#-background--motivation)
- [Methodology](#-methodology)
- [Results](#-results)
- [Key Findings](#-key-findings)
- [Conclusion](#-conclusion)
- [Repository Contents](#-repository-contents)
- [Authors](#-authors)
- [Legal Notice](#-legal-notice)

---

## 📌 Publication Details

| Field | Details |
|-------|---------|
| **Proceedings** | 1st Student Conference Research Forum |
| **Organizer** | IEEE Student Branch, Jaypee Institute of Information Technology (JIIT) |
| **Conference Dates** | January 30 – February 2, 2026 |
| **Venue** | JIIT, Sector-62, Noida, Uttar Pradesh, India |
| **Official Index Number** | #11 |
| **Pages** | 35–36 |
| **Certificate ID** | IEESBJIIT/RESEARCHFORUM\_1/078 |
| **Faculty Coordinator** | Dr. Abhay Kumar, Dept. of ECE, JIIT |

---

## 📝 Abstract

Edge AI deployments operate under strict constraints on energy consumption, thermal dissipation, and real-time latency — making accuracy-centric evaluation alone insufficient for real-world systems. This paper presents a **comparative meta-analysis** of MobileNet-V2 inference under three numerical precision modes — **FP32, FP16, and INT8** — on Jetson-class edge hardware.

Benchmark-reported accuracy, inference latency, and power measurements were sourced from publicly available vendor documentation and prior peer-reviewed studies. **Energy per inference** was computed by synthesizing reported power and latency metrics, enabling a unified cross-metric evaluation that is frequently absent in isolated benchmark reports. Pareto frontier analysis was employed to visualize the accuracy–energy trade-off across precision modes and execution hardware.

---

## 🧭 Background & Motivation

Deep neural networks deployed at the edge must satisfy constraints beyond raw accuracy. Two fundamental bottlenecks define edge AI feasibility:

**1. Energy Budget**  
Embedded platforms such as NVIDIA Jetson operate under strict power envelopes. Every inference consumes energy proportional to both the model's computational complexity and the hardware's power draw. Energy per inference (mJ) is the deployment-relevant metric — not accuracy in isolation.

**2. Numerical Precision**  
Modern inference engines support multiple floating-point and integer formats:
- **FP32** — Full 32-bit precision. Highest accuracy, highest energy cost.
- **FP16** — Half precision. Leverages Tensor Core acceleration on modern GPUs.
- **INT8** — 8-bit integer quantization. Lowest memory footprint and energy cost, with small accuracy trade-off when calibrated correctly.

Most prior works report accuracy or latency in isolation. This paper directly addresses that gap by computing a **unified energy-per-inference metric** across all three precision modes and comparing CPU vs GPU execution paths.

---

## ⚙️ Methodology

### Evaluation Framework

This study follows a **comparative meta-analysis** approach. No direct hardware measurements were performed. Instead, benchmark results for MobileNet-V2 inference were systematically collected from:

- NVIDIA Jetson benchmarking documentation
- MLPerf Inference benchmark reports
- Peer-reviewed studies on edge AI optimization

All measurements were normalized to ensure consistency across sources.

### Energy Computation

Energy per inference was derived using the following formula:

$$E_{inf} = P_{avg} \times T_{inf}$$

Where:
- $E_{inf}$ = Energy per inference (millijoules, mJ)
- $P_{avg}$ = Average power consumption (Watts, W)
- $T_{inf}$ = Inference latency (seconds, s)

This formulation allows direct comparison of efficiency across hardware configurations and precision modes on a per-inference basis.

### Model

**MobileNet-V2** was selected as the target model due to its widespread deployment in mobile and edge vision systems. It serves as a standard benchmark for lightweight inference evaluation. All accuracy figures refer to **Top-1 accuracy on ImageNet**.

### Evaluation Dimensions

| Dimension | Description |
|-----------|-------------|
| **Accuracy** | Top-1 classification accuracy (%) on ImageNet |
| **Latency** | Inference time per sample (ms) |
| **Power** | Average board-level power draw (W) |
| **Energy per Inference** | Derived metric: Power × Latency (mJ) |
| **Pareto Frontier** | Visual trade-off curve between accuracy and energy |

---

## 📊 Results

### Precision-Level Comparison (GPU Execution)

| Precision | Accuracy (%) | Latency (ms) | Power (W) | Energy (mJ) |
|-----------|:-----------:|:------------:|:---------:|:-----------:|
| FP32 | 71.8 | 54.2 | 0.26 | 14.10 |
| FP16 | 71.8 | 30.0 | 0.28 | **8.46** |
| INT8 | 71.2 | 18.0 | 0.31 | **5.64** |

> FP16 delivers identical accuracy to FP32 while reducing energy by ~40%. INT8 achieves the lowest energy per inference (~60% reduction) with less than 1% accuracy degradation.

---

### CPU vs GPU Execution Comparison

| Execution Mode | Precision | Accuracy (%) | Latency (ms) | Energy (mJ) |
|---------------|-----------|:-----------:|:------------:|:-----------:|
| CPU-only | FP32 | 71.8 | 95.0 | 24.70 |
| GPU | FP32 | 71.8 | 54.2 | 14.10 |
| GPU | FP16 | 71.8 | 30.0 | 8.46 |
| GPU | INT8 | 71.2 | 18.0 | 5.64 |

> CPU-based inference is strictly dominated by GPU execution across both latency and energy metrics at every precision level.

---

### Observed Trends

- Inference latency **decreases monotonically** with reduced numerical precision, indicating improved utilization of GPU Tensor Core accelerators.
- Energy per inference improvements scale **super-linearly** with precision reduction — the latency gain outweighs the slight increase in power draw.
- CPU execution remains impractical for energy-constrained deployments regardless of precision mode.
- The **Pareto frontier** confirms FP16 as the optimal operating point when accuracy must be fully preserved; INT8 dominates when a sub-1% accuracy trade-off is acceptable.

---

## 💡 Key Findings

```
✅ FP16  →  ~40% energy reduction vs FP32  |  0.0% accuracy loss
✅ INT8  →  ~60% energy reduction vs FP32  |  < 1% accuracy loss
✅ GPU   →  strictly dominates CPU on both latency and energy
✅ Pareto analysis confirms precision reduction as primary lever for efficiency
```

---

## ✅ Conclusion

This paper demonstrated that **energy per inference** — rather than accuracy alone — must serve as the primary evaluation metric for edge AI deployments. Through meta-analysis of MobileNet-V2 benchmarks on Jetson-class hardware:

- **FP16 inference** provides a practical balanced operating point: identical accuracy at significantly lower energy cost.
- **INT8 quantization** achieves maximum efficiency with negligible accuracy impact when appropriate calibration techniques are applied.
- **GPU acceleration** is a prerequisite for energy-efficient edge inference; CPU execution is not viable at scale.

These findings reinforce the importance of precision-aware, energy-centric model evaluation in the selection of deployment configurations for real-world edge AI systems.

---

## 📁 Repository Contents

| File | Description |
|------|-------------|
| `Tripathi_Singh_MobileNetV2_EdgeAI_Inference_IEEE_SBJIIT_2026.pdf` | Conference booklet excerpt — Cover, Proceedings, Table of Contents & Paper (pp. 35–36) |
|  `Certificate_Sidhant_Singh.pdf` | Official Certificate of Participation — IEEE SB JIIT Research Forum 2026 |
|  `Certificate_Sarthak_Tripathi.pdf` | Official Certificate of Participation — IEEE SB JIIT Research Forum 2026 |
|  `README.md` | Repository documentation |

---

## 👥 Authors

<table>
  <tr>
    <td align="center">
      <b>Sidhant Singh</b><br>
      B.Tech, Electronics & Communication Engineering<br>
      Jaypee Institute of Information Technology, Noida<br>
      <a href="https://github.com/SIDDYISBACK">@SIDDYISBACK</a>
    </td>
    <td align="center">
      <b>Sarthak Tripathi</b><br>
      B.Tech, Electronics & Communication Engineering<br>
      Jaypee Institute of Information Technology, Noida<br>
      <a href="https://github.com/quarky-1">@quarky-1</a>
    </td>
  </tr>
</table>

---

## ⚖️ License & Copyright
  
This repository is licensed under the **MIT License** — see the
[LICENSE](./LICENSE) file for details.

The MIT License applies to the **repository structure and README
documentation** authored by the contributors of this repository.

**The published research paper PDF** (`Tripathi_Singh_MobileNetV2_
EdgeAI_Inference_IEEE_SBJIIT_2026.pdf`) is reproduced here solely
for author portfolio and academic reference purposes. All rights to
the published proceedings remain with the authors and
**© 2026 IEESBJIIT**. Redistribution or commercial use of the paper
without permission is not permitted regardless of the repository
license.

---

<div align="center">

*Published in the Proceedings of the 1st Student Conference Research Forum*  
*IEEE Student Branch · Jaypee Institute of Information Technology · Noida, India · 2026*

</div>
