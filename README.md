# SFT — Structural Field Theory (Docs + Runners)

This repository is a **verification-first** release of SFT: a theory/framework plus a set of **runners** designed for **external audit**.

> **Start here:** read **[Doc 0 — Abstract & Orientation](0_SFT_Document0_Abstract_and_Orientation_UPDATED_with_10to14.pdf)** for the ontological stance, scope, current limitations, and falsifiable predictions.

The key idea is simple:
- The “vacuum” is treated as a **structural medium/field**.
- “Particles” are **stable field configurations** (discrete in manifestation, continuous in availability).
- The project is organized so third parties can **verify pipelines** via **PASS/FAIL gates**, **hash manifests**, and **schema-validated artifacts**.

> Important: many included datasets are **synthetic (C)** because this release is built to be verified on **CPU-only**.  
> Physical end-to-end confirmation requires **REAL solver runs (P)**, which this repo is designed to accept as external inputs.

---

## Quickstart (3 minutes)

### 1) Setup

```bash
git clone https://github.com/Xaquer69/sft-theory-and-runners
cd sft-theory-and-runners

python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate

pip install -r requirements.txt
```

2) Run one demo runner

Pick one of the “packs” below (recommended: Spin (Doc.5) or DoubleSlit (Doc.7)) and run its verify script.

Example pattern (adjust the path to the pack you choose):

```bash
cd <PATH_TO_A_PACK>
sha256sum -c checksums_SHA256.txt
python3 verify_*.py
```

If the verifier ends with GLOBAL_PASS = true, you successfully validated that pipeline.

Recommended verification path (in order)
CI / convergence sanity (C)
Run the EOC/CI synthetic check to verify your environment and regression gates.
One physics-style demo with PASS/FAIL (C)
Run either:
Double-slit demo (phase slope + visibility gates), or
Spin-½ demo (FR sign flip + rotor spectrum fit gates).
External Review Pack (C)
Run the “external review pack” to validate:
SCAN → REGION → REPORT artifacts,
JSON schema compliance,
and manifests/hashes for audit readiness.
