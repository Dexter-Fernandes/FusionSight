<!-- devcontainer-code=yes -->

<p align="center">
  <!-- Drop your actual architecture PNG in docs/ and reference it here -->
  <img src="docs/arch_diagram.png" width="640" alt="FusionSight System Diagram"/>
</p>

# FusionSight — Real-Time Stereo RGB + LiDAR Depth-Semantic Fusion

> **To perform real-time, per-pixel depth + semantic-class output by fusing stereoscopic RGB and LiDAR.**

<p align="center">
  <a href="https://github.com/&lt;you&gt;/FusionSight/actions/workflows/build-images.yml">
    <img alt="CI" src="https://github.com/&lt;you&gt;/FusionSight/actions/workflows/build-images.yml/badge.svg">
  </a>
  <img alt="DevContainer" src="https://img.shields.io/badge/VS Code-DevContainer-blue?logo=visualstudiocode">
  <img alt="Docker pulls" src="https://img.shields.io/docker/pulls/&lt;you&gt;/fusionsight-infer?logo=docker">
  <img alt="License" src="https://img.shields.io/github/license/&lt;you&gt;/FusionSight">
</p>

---

<!-- ## ✨ Key Features

| 🔹 | What | Why it matters |
|----|------|----------------|
| **Stereo RGB + LiDAR fusion** | Sparse LiDAR projected into CNN cost-volume | Robust depth in textureless zones |
| **Joint semantics** | DeepLab-v3+ MobileNet-v3 head over fused features | 55 % mIoU at edge-friendly latency |
| **Multi-format export** | ONNX → OpenVINO FP32/FP16/INT8 → TensorRT FP16 | Runs on laptop CPU, ANYmal, or Jetson (stretch) |
| **One-command runtime** | `docker run ghcr.io/&lt;you&gt;/fusionsight-infer` | Reviewers see results in < 30 s |
| **Reproducible dev env** | VS Code devcontainer / Codespaces | Zero “works-on-my-machine” drift |

---

## 🚀 Quick-Start (Inference-Only Docker)

```bash
docker run --rm -it \
  ghcr.io/<you>/fusionsight-infer:latest -->
