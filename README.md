# Awesome AI/ML for Diffraction [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of AI/ML tools, models, and frameworks for diffraction and scattering — from materials discovery and structure generation, through autonomous experiment steering, to structure and dynamics analysis.

Each entry gives a short description plus, where known, its **availability**, **interface/platform**, and **compute** needs:

- 🟢 Open source / public  🟡 Research prototype or partially open  🔒 Not (yet) publicly available
- 💻 Runs on a laptop  🖥️ GPU or moderate compute  🏭 HPC-scale

Contributions are welcome — see [Contributing](#contributing).

## Contents

- [1. Materials Discovery & Structure Generation](#1-materials-discovery--structure-generation)
  - [Universal Interatomic Potentials & Atomistic Foundation Models](#universal-interatomic-potentials--atomistic-foundation-models)
  - [Training, Fine-tuning & Simulation Frameworks](#training-fine-tuning--simulation-frameworks)
  - [Generative Crystal Structure Design](#generative-crystal-structure-design)
  - [Screening, Featurization & Chemical Heuristics](#screening-featurization--chemical-heuristics)
  - [Closed-loop, Bayesian & LLM-driven Discovery](#closed-loop-bayesian--llm-driven-discovery)
  - [Scattering Simulation from Structure Models](#scattering-simulation-from-structure-models)
- [2. Experiment Planning, Steering & Control](#2-experiment-planning-steering--control)
  - [Orchestration & Self-driving Lab Platforms](#orchestration--self-driving-lab-platforms)
  - [Optimization & Active Learning Libraries](#optimization--active-learning-libraries)
  - [Autonomous Diffraction & Scattering Steering](#autonomous-diffraction--scattering-steering)
  - [LLM & Agentic Instrument Control](#llm--agentic-instrument-control)
  - [Portals & Resources](#portals--resources)
- [3. Structure & Dynamics Analysis](#3-structure--dynamics-analysis)
  - [Symmetry & Lattice Determination from Powder Data](#symmetry--lattice-determination-from-powder-data)
  - [Phase Identification & Phase Mapping](#phase-identification--phase-mapping)
  - [Structure Solution from Diffraction Patterns](#structure-solution-from-diffraction-patterns)
  - [Bragg Peak Finding, Indexing & Differentiable Refinement](#bragg-peak-finding-indexing--differentiable-refinement)
  - [Imaging & Reconstruction](#imaging--reconstruction)
  - [Probabilistic & Multimodal Inference](#probabilistic--multimodal-inference)
  - [End-to-end Agentic Workflows](#end-to-end-agentic-workflows)
- [Related Awesome Lists](#related-awesome-lists)
- [Contributing](#contributing)

---

## 1. Materials Discovery & Structure Generation

### Universal Interatomic Potentials & Atomistic Foundation Models

- [M3GNet](https://github.com/materialyzeai/m3gnet) — Universal interatomic potential for atomistic property prediction; widely adopted and typically embedded in simulation workflows. 🟢 🏭 (training heavy, inference moderate; often run on HPC)
- [MACE](https://github.com/ACEsuit/mace-foundations) — Foundation interatomic potential used inside MD/atomistic workflows via a standard ML interface. 🟢 🏭 (training heavy, inference moderate)
- [MatterSim](https://github.com/microsoft/mattersim) — Industry-scale foundation atomistic model designed as a general-purpose simulation engine. 🟡 🏭
- [GNoME](https://app.readytensor.ai/publications/materials-discovery-gnome-vyH2wPwb1fum) — Industry model for large-scale materials screening, embedded in discovery pipelines. 🟡 🏭
- Orb / UMA / EquiformerV2 / JMP — Open foundation atomistic models designed to be fine-tuned and embedded; supported in MatterTune through ASE wrappers. 🟢 🖥️
  - [Orb](https://github.com/orbital-materials/orb-models)
  - [UMA](https://ai.meta.com/research/publications/uma-a-family-of-universal-models-for-atoms/)
  - [EquiformerV2](https://github.com/atomicarchitects/equiformer_v2)
  - [JMP](https://arxiv.org/abs/2310.16802)

### Training, Fine-tuning & Simulation Frameworks

- [MatterTune](https://github.com/Fung-Lab/MatterTune) — Fine-tuning framework for atomistic foundation models; wraps models into ASE pipelines with multi-GPU support. 🟢 🖥️
- [HydraGNN](https://github.com/ORNL/HydraGNN) — ORNL's distributed equivariant GNN framework for training structure → property models at exascale. 🟢 🏭
- [TorchSim](https://arxiv.org/pdf/2508.06628) — Geometry optimization and molecular dynamics engine with interfaces to many interatomic potentials ([intro blog](https://huggingface.co/blog/Nekkrad/introduction-to-torchsim)). 🟢 🖥️

### Generative Crystal Structure Design

- [CDVAE](https://github.com/txie-93/cdvae) — Crystal diffusion variational autoencoder for generating periodic structures ([paper](https://doi.org/10.48550/arXiv.2110.06197)). 🟢 🖥️
- [DiffCSP](https://github.com/jiaor17/DiffCSP) — Diffusion model for crystal structure prediction. 🟢 🖥️
- [MatterGen](https://github.com/microsoft/mattergen) — Diffusion-based generative model for inorganic materials design. 🟢 🖥️
- [SCIGEN](https://github.com/RyotaroOKabe/SCIGEN) — Constrains generative diffusion models to produce structures with target geometric motifs ([MIT News](https://news.mit.edu/2025/new-tool-makes-generative-ai-models-likely-create-breakthrough-materials-0922)). 🟢 🖥️
- [CrystaLLM](https://github.com/lantunes/CrystaLLM) — LLM that generates candidate crystal structures as CIF files ([paper](https://doi.org/10.1038/s41467-024-54639-7)). 🟢 🖥️
- [CrystalLLM (crystal-text-llm)](https://github.com/facebookresearch/crystal-text-llm) — Fine-tuned LLMs that generate stable materials as text/CIF; distinct from CrystaLLM ([paper](https://arxiv.org/abs/2402.04379)). 🟢 🖥️
- [CDVAE_XRD](https://github.com/gabeguo/cdvae_xrd/tree/main) — Generative structure modeling regularized by powder diffraction patterns. 🟢 🖥️
- [Supramolecular VAE](https://github.com/zhenpengyao/Supramolecular_VAE) — Variational autoencoder for generating metal–organic frameworks ([paper](https://doi.org/10.1038/s42256-020-00271-1)). 🟢 🖥️
- PyXtal — Generates candidate crystal structures from a chosen space group. 🟢 💻

### Screening, Featurization & Chemical Heuristics

- [The High-Throughput Toolkit (httk)](https://github.com/httk/httk) — Screening of large sets of candidate structures ([paper](https://doi.org/10.48550/arXiv.2601.21393)). 🟢 💻
- Matminer — Feature generation for materials datasets (Python/pymatgen). 🟢 💻
- [SMACT](https://pubs.rsc.org/en/content/articlelanding/2018/fd/c8fd00032h) — Oxidation-state and charge-balance screening of compositions. 🟢 💻
- [Robocrystallographer](https://github.com/hackingmaterials/robocrystallographer) — Generates text descriptions of crystal structures (Python/pymatgen); useful for LLM pipelines. 🟢 💻
- Aries_enthalpy (AI Enthalpy Model) — API-accessible model predicting formation enthalpy from composition and/or structure for candidate screening; designed as a callable MCP tool inside a reasoning framework. 🔒 🖥️

### Closed-loop, Bayesian & LLM-driven Discovery

- [LLMatDesign](https://github.com/Fung-Lab/LLMatDesign) — LLM-driven iterative materials optimization coupling an LLM with atomistic simulation back-ends. 🟡 🖥️
- [AMASE](https://www.science.org/doi/10.1126/sciadv.adu7426) — Closed-loop XRD + CALPHAD refinement integrating diffraction with thermodynamic modeling. 🟡 🖥️
- [CAMEO](https://www.nature.com/articles/s41467-020-19597-w) — Bayesian optimization that uses structural (XRD) information to accelerate property optimization. 🟢 💻
- [SAGE](https://arxiv.org/abs/2311.06228) — Bayesian coregionalization that fuses data across a lab to learn synthesis–process–structure–property relationships (Python/NumPyro, MCMC; best for < ~1000 data points). 🟢 💻
- [MULTITASK](https://www.cell.com/matter/fulltext/S2590-2385(23)00124-8) — Framework for creating multiple expert AI agents, managing their collaboration, and optimizing lab operation. 🟢 💻

### Scattering Simulation from Structure Models

- [Diffuse Scattering RMC6f](https://maximeremenko.github.io/Utilities/RMCProfileUtilities/Diffuse_Scattering/Diffuse_Scattering_RMC6f.html) — In-browser computation, visualization, and export of diffuse scattering $I(hkl)$ from RMC6f configurations using Type-3 NUFFT (CPU/WebGPU) with neutron, X-ray, or electron scattering models. 🟢 💻

---

## 2. Experiment Planning, Steering & Control

### Orchestration & Self-driving Lab Platforms

- [INTERSECT](https://github.com/ORNL/intersect-architecture) — ORNL facility-wide orchestration framework with defined services (REST, SDK); designed as a workflow backbone. 🟢 💻
- [MADSci](https://github.com/AD-SDL) — Self-driving lab platform and workflow framework. 🟢 💻
- [Bluesky](https://github.com/bluesky) + [BLOP](https://github.com/bluesky/blop/) — Beamline instrument control with integrated Bayesian optimization in the Bluesky ecosystem. 🟢 💻

### Optimization & Active Learning Libraries

- [DIAL](https://github.com/INTERSECT-DIAL/dial) — Active learning service with a defined interface, integrated into INTERSECT. 🟢 🖥️
- [GPax](https://github.com/ziatdinovmax/gpax) — Gaussian-process Bayesian optimization library; modular backend for DIAL. 🟢 🖥️
- [Xopt](https://github.com/xopt-org/xopt) — Optimization library for beamline and accelerator tuning and Bayesian experimental design; integrated at SLAC. 🟢 🖥️
- [Badger](https://github.com/xopt-org/badger) — GUI optimization framework used alongside Xopt. 🟢 🖥️
- [BAX (Bayesian Algorithm Execution)](https://willieneis.github.io/research/bax/index.html) — Method for targeted Bayesian experimental design; implementations in [multibax-sklearn](https://github.com/sathya-chitturi/multibax-sklearn) and Xopt. 🟢 🖥️

### Autonomous Diffraction & Scattering Steering

- [CrystalPilot](https://github.com/neutrons/CrystalPilot) — Steering of single-crystal neutron experiments; integrates NDIP and an HPC module (memory cost grows quickly with resolution). 🟢 🖥️
- [ANDiE](https://arxiv.org/abs/2108.08918) — Bayesian autonomous neutron diffraction steering integrated with instrument control; demonstrated at NIST/ORNL. 🟡 🖥️
- [AutoREFL](https://doi.org/10.1107/S1600576724006447) — Active learning for neutron reflectometry measurements. 🟡 🖥️

### LLM & Agentic Instrument Control

- [VISION](https://github.com/CFN-softbio/VISION) — Agentic AI for voice-controlled beamline operation and analysis. 🟢 🖥️
- NICE LLM — LLM interface for neutron instrument control (demonstrated). 🔒

### Portals & Resources

- [ADDIE](https://addie.ornl.gov/) — Web portal providing access to diffraction tools and information. 🟢 💻

---

## 3. Structure & Dynamics Analysis

### Symmetry & Lattice Determination from Powder Data

- AlphaDiffract — Predicts crystal system, space group, and lattice parameters from PXRD as candidates for Rietveld refinement. 🔒 (yet to be published) 🖥️
- XSymNet — Symmetry, lattice parameter, and atomic position classification from X-ray or neutron powder diffraction. Workflow: start from the parent-symmetry CIF → enumerate the subgroup tree with ISODISTORT → simulate training data with TOPAS (GSAS-II planned) → train an attention network → predict the subgroup from measured data → Rietveld-refine the top predictions → return refined CIFs and patterns. 🟡 🖥️

### Phase Identification & Phase Mapping

- [XRD-AutoAnalyzer (Branching-CNN)](https://github.com/njszym/XRD-AutoAnalyzer) — Probabilistic multiphase identification from powder XRD ([paper](https://doi.org/10.1021/acs.chemmater.1c01071)). 🟢 🖥️
- [XCA](https://github.com/maffettone/xca) — Crystallographic companion agent for probabilistic phase labeling of powder XRD ([paper](https://www.nature.com/articles/s43588-021-00059-2)). 🟢 🖥️
- [CrystalShift](https://github.com/MingChiangChang/CrystalShift.jl) — Probabilistic multiphase labeling for powder XRD in Julia ([paper](https://www.nature.com/articles/s41524-025-01627-0)). 🟢 🖥️
- [Dara](https://arxiv.org/abs/2510.19667) — Phase identification from diffraction data. 🟡
- [DRNets](https://github.com/gomes-lab/DRNets-Nature-Machine-Intelligence) — Deep reasoning networks for unsupervised phase mapping and multiphase identification from X-ray data ([paper](https://www.nature.com/articles/s42256-021-00384-1)). 🟢 🖥️
- [GRENDEL](https://iopscience.iop.org/article/10.1088/0957-4484/26/44/444002) — Phase mapping for high-throughput combinatorial libraries. 🟡 🖥️
- [Impurity Phase Detection for NPD](https://huggingface.co/spaces/Lalityadav07/phase_detection) — Automatic impurity phase detection from neutron powder diffraction; deployed as a web app. 🟢 💻
- [rhana (RHEED analysis)](https://github.com/AuroraLHT/rhana) — Extracts phases and abundances from RHEED for closed-loop optimization of in situ epitaxial growth ([paper](https://journals.aps.org/prmaterials/abstract/10.1103/PhysRevMaterials.6.063805)). 🟢 🖥️

### Structure Solution from Diffraction Patterns

- [Crystalyze](https://github.com/ML-PXRD/Crystalyze) — Diffusion model that solves crystal structures from powder XRD patterns ([paper](https://doi.org/10.1021/jacs.4c10244)). 🟢 🖥️
- [deCIFer](https://github.com/FrederikLizakJohansen/deCIFer) — LLM that generates CIFs conditioned on powder XRD ([paper](https://arxiv.org/pdf/2502.02189)); note that reported $R_{wp}$ is relatively high for low-symmetry phases. 🟢 🖥️

### Bragg Peak Finding, Indexing & Differentiable Refinement

- [PeakNet](https://github.com/carbonscott/peaknet) — Computer-vision Bragg peak detection, integrated at LCLS with Psocake/Cheetah/CrystFEL. 🟢 🖥️
- [BraggNN](https://github.com/lzhengchun/BraggNN) — Fast Bragg peak localization for HEDM workflows at APS. 🟢 🖥️
- [Resonet](https://github.com/dermen/resonet) — Resolution and lattice prediction trained on simulated data, for use in indexing workflows. 🟢 🖥️
- diffBragg / nanoBragg — Diffraction simulation and differentiable refinement, interfaced via Python/ML stacks ([cxid9114](https://github.com/dermen/cxid9114), [nanoBragg](https://bl831.als.lbl.gov/~jamesh/nanoBragg/)). 🟢 🏭

### Imaging & Reconstruction

- [PtychoNN](https://github.com/mcherukara/PtychoNN) — Real-time neural-network ptychography reconstruction; in production use at multiple APS instruments. 🟢 🏭 (GPU required)

### Probabilistic & Multimodal Inference

- [sbi](https://sbi.readthedocs.io/en/latest/) — Simulation-based inference package for probabilistic analysis of scattering data. 🟢 🖥️
- [SAGE](https://arxiv.org/abs/2311.06228) — Multimodal joint inference across instruments (see also [Closed-loop Discovery](#closed-loop-bayesian--llm-driven-discovery)). 🟢 💻
- [AutoSAS](https://arxiv.org/abs/2506.13918) — Autonomous small-angle scattering model selection, integrated in the Autonomous Formulation Lab (AFL). 🟡 🖥️

### End-to-end Agentic Workflows

- [NeuDiff Agent](https://code.ornl.gov/5xw/NeuDiff-Agent) — Single-crystal neutron diffraction workflow from event data to a checkCIF-validated structure for TOPAZ at SNS; browser front end coupled to governed tool execution. 🟢 🖥️

---

## Related Awesome Lists

- [awesome-matchem-datasets](https://github.com/blaiszik/awesome-matchem-datasets) — Datasets for materials informatics, organized by task.
- [awesome-materials-informatics](https://github.com/tilde-lab/awesome-materials-informatics) — Materials informatics software and resources.
- [MaRDA awesome list](https://github.com/marda-alliance/awesome_list) — Materials research data resources from the MaRDA alliance.

## Contributing

Contributions are welcome! Please open a pull request adding a tool to the most relevant section using the format:

```markdown
- [Tool Name](link) — One-line description of what it does. <availability> <compute>
```

Include a link to code (preferred) or the paper, and note whether the tool is publicly available.
