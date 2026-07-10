# Awesome Applied AI Researcher (Generative 3D) Interview Q&A 🧊🎨🧠

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A curated, no-fluff collection of **Applied AI Researcher (Generative 3D) interview questions with answers**, organized by topic. Built for candidates prepping for roles building generative models for 3D content — 3D Generative AI Researcher, Neural Rendering Research Engineer, Text-to-3D/4D Researcher, and Applied Scientist (3D Vision/Graphics) roles — and for interviewers building question banks.

> 📎 **Scope note:** This repo sits at the intersection of three fields that a Generative 3D researcher needs fluency in: **3D representations** (meshes, point clouds, SDFs, NeRFs, Gaussian Splatting), **generative modeling** (diffusion, GANs, VAEs, autoregressive/flow models — and how each does or doesn't translate cleanly from 2D images to 3D data), and **differentiable/neural rendering** (the bridge that lets 2D image supervision train 3D generative models). It's distinct from the [Awesome-Perception-Simulation-Engineer-Interview-QA](https://github.com/ishandutta2007/Awesome-Perception-Simulation-Engineer-Interview-QA) repo in this series, which covers *perceiving and simulating* the 3D world for robotics/AV, rather than *generating* novel 3D content from learned models.

Every answer aims to be **concise, correct, and interview-ready** — the kind of answer that would actually land well in a 45-60 minute technical/research round, not a textbook chapter.

> ⭐ Star this repo if it helps your prep. PRs adding new questions, fixing answers, or improving explanations are very welcome — see [CONTRIBUTING.md](CONTRIBUTING.md).

---

## 📚 Table of Contents

| # | Topic | Questions | Difficulty Mix |
|---|-------|-----------|-----------------|
| 01 | [3D Representations Fundamentals](topics/01-3d-representations-fundamentals.md) | 11 | Easy → Hard |
| 02 | [Generative Modeling Fundamentals](topics/02-generative-modeling-fundamentals.md) | 11 | Medium → Hard |
| 03 | [Diffusion Models for 3D Generation](topics/03-diffusion-models-3d-generation.md) | 10 | Medium → Hard |
| 04 | [Neural & Differentiable Rendering](topics/04-neural-differentiable-rendering.md) | 10 | Medium → Hard |
| 05 | [Text-to-3D & Multimodal Conditioning](topics/05-text-to-3d-multimodal-conditioning.md) | 9 | Medium → Hard |
| 06 | [Neural Fields: NeRF & Gaussian Splatting](topics/06-neural-fields-nerf-gaussian-splatting.md) | 10 | Medium → Hard |
| 07 | [Mesh Generation, Topology & Post-Processing](topics/07-mesh-generation-topology.md) | 9 | Medium → Hard |
| 08 | [Texture, Material & Appearance Generation](topics/08-texture-material-appearance.md) | 9 | Medium → Hard |
| 09 | [3D Data Pipelines, Datasets & Preprocessing](topics/09-3d-data-pipelines-datasets.md) | 9 | Medium |
| 10 | [Evaluation Metrics for Generative 3D](topics/10-evaluation-metrics-generative-3d.md) | 9 | Medium → Hard |
| 11 | [Training Infrastructure & Scaling](topics/11-training-infrastructure-scaling.md) | 9 | Medium → Hard |
| 12 | [Research Methodology & Experimentation](topics/12-research-methodology-experimentation.md) | 9 | Medium → Hard |
| 13 | [Scenario-based & Behavioral](topics/13-scenario-behavioral.md) | 10 | Medium → Hard |

**Total: 125 questions** in v1, growing with community contributions.

---

## 🧭 How to Use This Repo

- **Cramming for an interview next week?** Start with the topic weighted heaviest for your target role (see below), and read the "Follow-up" notes — interviewers almost always dig deeper.
- **Deep prep over weeks?** Work through every file top to bottom — for the math-heavy topics (diffusion, differentiable rendering), re-derive the key equations yourself; for representation topics, be ready to sketch the tradeoffs on a whiteboard.
- **Interviewing candidates?** Use these as a base question bank — mix easy/medium/hard per round, and use the scenario/research-methodology questions to gauge genuine research judgment, not just paper recall.

### Suggested focus by role

| Role | Prioritize |
|------|------------|
| 3D Generative AI Researcher (generalist) | 3D Representations, Generative Modeling Fundamentals, Diffusion for 3D, Evaluation Metrics |
| Text-to-3D / Multimodal Researcher | Text-to-3D & Conditioning, Diffusion for 3D, Neural Fields, Research Methodology |
| Neural Rendering Research Engineer | Neural & Differentiable Rendering, Neural Fields (NeRF/Gaussian Splatting), Training Infra |
| 3D Asset / Mesh Generation Researcher | Mesh Generation & Topology, Texture/Material Generation, 3D Data Pipelines |
| Research Engineer (infra-leaning) | Training Infrastructure & Scaling, 3D Data Pipelines, Research Methodology |
| Applied Scientist (product-facing) | Evaluation Metrics, Text-to-3D & Conditioning, Scenario-based & Behavioral |

---

## 🗂️ Repo Structure

```
Awesome-Applied-AI-Researcher-Generative3D-Interview-QA/
├── README.md                 ← you are here
├── CONTRIBUTING.md
├── LICENSE
└── topics/
    ├── 01-3d-representations-fundamentals.md
    ├── 02-generative-modeling-fundamentals.md
    ├── 03-diffusion-models-3d-generation.md
    ├── 04-neural-differentiable-rendering.md
    ├── 05-text-to-3d-multimodal-conditioning.md
    ├── 06-neural-fields-nerf-gaussian-splatting.md
    ├── 07-mesh-generation-topology.md
    ├── 08-texture-material-appearance.md
    ├── 09-3d-data-pipelines-datasets.md
    ├── 10-evaluation-metrics-generative-3d.md
    ├── 11-training-infrastructure-scaling.md
    ├── 12-research-methodology-experimentation.md
    └── 13-scenario-behavioral.md
```

## 🛣️ Roadmap (v2+)

- [ ] Add "Paper tags" (which questions map to specific influential papers — DreamFusion, Zero-1-to-3, 3D Gaussian Splatting, Point-E/Shap-E, Instant-NGP, etc.)
- [ ] Add a `/mock-interviews` folder with full simulated research-presentation and whiteboard-derivation sessions
- [ ] Add difficulty badges per question
- [ ] Add worked derivations for the diffusion ELBO/score-matching objective and volumetric rendering equation
- [ ] Add a companion cheat-sheet repo comparing 3D representation tradeoffs and generative model family tradeoffs
- [ ] Community-submitted "how I answered this in a real interview" notes

## 🤝 Contributing

This is meant to be a living, community-curated resource. See [CONTRIBUTING.md](CONTRIBUTING.md) for the format to follow when submitting a question.

## 📄 License

Content is released under the [MIT License](LICENSE) — free to use, fork, and adapt.

---

*Maintained by [@ishandutta2007](https://github.com/ishandutta2007). Part of a series of "Awesome" curated technical resources.*
