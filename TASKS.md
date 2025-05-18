# FusionSight — Master To-Do List (Progress Tracker)

Legend	Meaning
[x]	Completed
[🟡]	In progress
[ ]	Not started
0 · Project Scaffolding

Create Git repo FusionSight/

    Commit baseline folder layout (ros2_ws/, docker/, models/, docs/…)

1 · Development Environment

VS Code devcontainer

.devcontainer/docker/dev.Dockerfile (ROS Jazzy + PyTorch)

    devcontainer.json with postCreateCommand → colcon build

GitHub Actions workflow builds fusionsight-dev:latest image

    Configure optional Codespaces defaults (machine size, ports)

2 · Data Acquisition

data_depth_annotated (dense GT)

[🟡] data_depth_velodyne (sparse depth) — downloading

[🟡] KITTI Raw RGB sequences matching train/val IDs — downloading

kitti_semantics.zip (per-pixel masks for mIoU)

(Optional) SemanticKITTI scans

    Add YAMLs in data_cfg/ pointing to extracted paths

3 · Data Pre-Processing

visualise_triplet.py (RGB / sparse / dense overlay)

Manual alignment sanity-check on 3 sequences

    Generate train_files.txt & val_files.txt manifests

4 · Model Training

Training script (Lightning or custom):

MiDaS-DPT-Hybrid depth branch

Sparse-depth fusion layer

    DeepLab-v3+ MobileNet-v3 semantic head

AMP / mixed precision

TensorBoard or W&B logging

    Save best checkpoint to models/checkpoints/

5 · Evaluation

Depth — evo_ape (RMSE & δ < 1.25)

Semantics — torchmetrics.MeanIoU

Unit tests for dataloader & metrics in CI

    Hit KPI: RMSE < 0.7 m · δ > 0.90 · mIoU > 0.55

6 · Export Pipeline

export_all.sh

PyTorch → ONNX

ONNX → OpenVINO FP32 / FP16 / INT8 (POT)

    ONNX → TensorRT FP16 (x86) (Jetson later)

manifest.json with hashes & precisions

    CI step fails if checkpoint ≠ exported hash

7 · Runtime Docker Image

docker/infer.Dockerfile

Base openvino/ubuntu22_runtime

Copy models/exported/

    CLI infer_openvino.py

GitHub Actions multi-arch build (amd64 & arm64)

Verify README quick-start:

    docker run ghcr.io/<you>/fusionsight-infer:latest

8 · ROS 2 Integration

Package perception/

Node wrapping OpenVINO runtime

    Topics /image/depth, /image/semantic, /pointcloud/semantic

Launch file + RViz config

    Record 30-s demo rosbag

9 · Benchmarks & Reporting

benchmark.py → latency_vs_accuracy.csv

Plot saved to docs/latency_mAP.png

CPU power test with intel_rapl

    Insert Section 7 “Evaluation & Reporting” table into README

10 · Documentation & Polish

Add hero diagram docs/arch_diagram.png

Flesh out README (Quick-start, Dev, Benchmarks)

docs/export_guide.md

docs/hardware_matrix.md

    Shields.io badges (CI, Docker pulls, DevContainer)

11 · Demo Assets

GIF/MP4 overlay demo (docs/demo_gif.gif)

Optional YouTube screencast

    Draft Medium blog post

12 · Stretch Goals

Jetson-Orin INT8 TensorRT build

WebRTC live viewer

Evidential uncertainty head