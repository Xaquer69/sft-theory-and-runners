# SFT — Designed Matter via Tensional Compatibility

Tagline: If stability is compatibility with the medium, then matter can be designed **[DOC_0 The stability of a configuration is not intrinsic to the object, but emerges from its tensional compatibility with the medium](sft-theory-and-runners/0_SFT_Document0_Abstract_and_Orientation_UPDATED_with_10to14.pdf)** Release of SFT: a theory/framework plus a set of **runners** designed for **external audit**.

> **What’s the idea?** In Structural Field Theory (SFT), a configuration exists when it is stably compatible with its medium. Existence comes in two modes: - Natural: stability holds in the ambient medium (no upkeep). - Maintained: stability holds when minimal external conditions (controls, confinement, fields, BCs) provide compatibility **[Doc.11_OnePager_DesignedMatter_SFT_UPDATED.pdf](/11_OnePager_DesignedMatter_SFT_UPDATED.pdf)** 

The key idea is simple:
- The “vacuum” is treated as a **structural medium/field**.
- “Particles” are **stable field configurations** (discrete in manifestation, continuous in availability).
- The project is organized so third parties can **verify pipelines** via **PASS/FAIL gates**, **hash manifests**, and **schema-validated artifacts**.

> Important: many included datasets are **synthetic (C)** because this release is built to be verified on **CPU-only**.  
> Physical end-to-end confirmation requires REAL (P) solver outputs. CI only validates the verification pipeline (CPU-only), not physical validation.
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

### 2) Example pattern (adjust the path to the pack you choose):

```bash
cd <PATH_TO_A_PACK>
sha256sum -c checksums_SHA256.txt
python3 verify_*.py
```

## Recommended verification path:

1) **Atom X**  

*_CLEANED.zip and runner bundles
When a document has an executable verification component, the corresponding zipped runner bundle is included.

Schemas/ (if present)
JSON schemas for standardized artifacts (reports, scans, manifests).

## Artifact contract (what “verification” means here)
Most runners produce a standard set of artifacts:

COMPATIBILITY_SCAN_*.json
A parameter sweep (grid/scan) with per-point metrics.

EXISTENCE_REGION_*.json
The PASS region extracted from the scan (mask/region geometry + thresholds).

EXISTENCE_REPORT_*.json
A single verdict + provenance (version, seed, gates, hashes).

Typical verdict labels:

natural — stable without “maintenance”

maintained — stable only under explicit constraints/controls

All packs include:

SHA-256 manifests (checksums_SHA256.txt, etc.)

PASS/FAIL gates with explicit thresholds

(often) JSON schema validation

## What is (C) vs (P)?
This repo uses a strict separation:

(C) Convenience / CI / Synthetic

Runs on CPU.

Validates pipelines, regression checks, schemas, and audit trails.

Does not claim physical validation by itself.

(P) Physical / REAL

Requires the real solver outputs (often GPU-scale).

Intended to be run by third parties, then checked with the same verification pipelines.

## Minimal requirements
Python 3.10+

CPU-only is sufficient for the (C) packs.

OS: Linux/macOS/Windows should work if Python dependencies install cleanly.

## Notes for reviewers

This repository is intentionally organized around external verifiability:

deterministic seeds,

explicit thresholds,

hashes/manifests,

and schema-validated outputs.

If you want to contribute REAL (P) runs, please follow this minimal contract:

- Export **SCAN / REGION / REPORT** artifacts using the same filename patterns used by the pack.
- Include full **provenance** in SCAN metadata: solver version/hash, grid(s), Δt/CFL, BCs, seed(s), platform.
- Provide **≥2 resolutions** for any physical claim (or an explicit pre-asymptotic analysis).
- Include a **SHA-256 manifest** covering all exported files, and reference the exact **gate_id** used.
- Gates must be **pre-registered** (locked before the solver run); post-hoc loosening is not allowed.

Distributed under the MIT License. See the LICENSE
 file.

DOI:
https://doi.org/10.5281/zenodo.18631789

## Author & Contact

Francisco Queral Rallo
Murcia, España
✉ xaviqueral@gmail.com
