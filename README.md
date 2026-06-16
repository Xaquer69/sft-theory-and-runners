# SFT — Structural Field Theory (Docs + Runners)

This repository is a **[verification-first](sft-theory-and-runners/SFT_Paper_Verification-First_Protocol_v0.3_FIREDRAKE_REVIEWER_SAFE_EDIT.pdf)** release of SFT: a theory/framework plus a set of **runners** designed for **external audit**.

## Update — Firedrake/UFL exploratory bridge outputs

**Update date:** 2026-06-16

This repository now includes `SFT_FIREDRAKE_CORE_REPRO_v0_1_8`, an exploratory Firedrake/UFL real-solver bridge package.

This package adds external PDE/FEM bridge outputs for selected SFT-facing audit targets, including:

* spin-½ FR bend robustness signatures,
* hydrogenic radial Coulomb H/T 2s/2p gates,
* Venus and Mercury 1PN perihelion geometry gates,
* alpha-localization capacity scans,
* double-slit Firedrake phase/visibility diagnostics,
* and an intentionally incomplete Alpha-Out bridge report.

These Firedrake/UFL outputs are stronger than synthetic CI checks because they are produced in an external real-solver environment and exported as auditable JSON/CSV artifacts with SHA-256 manifests and PASS/FAIL gates.

They are **not** presented as global physical validation of SFT, nor as derivations of the Standard Model or General Relativity. They should be read as an **exploratory P-bridge**: real-solver bridge outputs that exercise the verification-first contract, while still requiring independent third-party REAL runs at multiple resolutions for physical confirmation.

Evidence labels used in this repository:

* **CI (C):** CPU-only validation of tooling, schemas, manifests, regression checks, and PASS/FAIL logic.
* **REAL-ready (P-input):** verifier and artifact contract are ready to ingest third-party real-solver outputs.
* **Exploratory P-bridge:** real-solver bridge outputs produced in an external solver environment, with hashes and machine-checkable reports, but not yet independently replicated.
* **REAL-verified (P):** reserved for independent third-party real-solver runs with artifacts, hashes, locked gates, and at least two resolutions.

-----------------------------------------------------------------------------------------------

> **Start here:** read **[Doc 0 — Abstract & Orientation](sft-theory-and-runners/0_SFT_Document0_Abstract_and_Orientation_UPDATED_with_10to14.pdf)** for the ontological stance, scope, current limitations, and falsifiable predictions.

The key idea is simple:
- The “vacuum” is treated as a **structural medium/field**.
- “Particles” are **stable field configurations** (discrete in manifestation, continuous in availability).
- The project is organized so third parties can **verify pipelines** via **PASS/FAIL gates**, **hash manifests**, and **schema-validated artifacts**.

> Important: many included datasets are **synthetic (C)** because this release is built to be verified on **CPU-only**.  
> Physical end-to-end confirmation requires REAL (P) solver outputs. CI only validates the verification pipeline (CPU-only), not physical validation.
- **REAL-ready**: verifiers + artifact contract are in place; can consume third-party real-solver outputs.
- **REAL-verified**: a real-solver run has been published with artifacts + hashes and passes the declared gates.
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

### 2) Run one demo runner

Pick one of the “packs” below (recommended: Spin (Doc.5) or DoubleSlit (Doc.7_1)) and run its verify script.

Example pattern (adjust the path to the pack you choose):

```bash
cd <PATH_TO_A_PACK>
sha256sum -c checksums_SHA256.txt
python3 verify_*.py
```

If the verifier ends with GLOBAL_PASS = true, you successfully validated that pipeline.

## Recommended verification path (in order)

1) **CI / convergence sanity (C)**  
   Run the EOC/CI (Doc.6) synthetic check to verify your environment and regression gates.

2) **One physics-style demo with PASS/FAIL (C)**  
   Run either: Double-slit (Doc.7_1) or Spin-½ (Doc.5).

3) **External Review Pack (C) (Doc.9)**  
   Validate SCAN → REGION → REPORT artifacts, JSON schema compliance, and manifests/hashes for audit readiness.

4) **(Optional) Doc 10.1 — Alpha-Elasticity CI Suite (C)**
   A CI/synthetic protocol for an alpha-like estimator (anti-leakage discipline, preregistered decision rules + hashing, null/adversarial controls).
   Not physical validation of α; included as a verification methodology appendix.

5) **(Optional) Doc 8 - Limitations and Validation Plan**
   includes External Break Test #01 (field rescaling) as a Doc9/Doc10.1-style anti-post-hoc audit protocol.
   
6) **(Optional) Doc 14 - Capstone (Unified v6c)**
   Includes Firedrake/UFL external bridge [CI/exploratory]: a reference executable mini-pack implementing selected scalar-field equations, benchmarks, and exploratory diagnostics in a non-native PDE/FEM environment. Its purpose is not to reproduce the full SFT corpus externally, but to provide an auditable bridge for inspecting parts of the framework outside the native SFT runner ecosystem.

## Repository structure
Doc_01/ ... Doc_14/
The full documentation set (each doc in its own folder).

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

## Where to start (most user-friendly packs)
If you only run one thing, run one of these:

DoubleSlit_PACKAGE — verifies phase slope linearity and visibility monotonicity (PASS/FAIL). (Doc.7).

Spin / Appendix S pack — verifies FR 2π sign flip and rotor spectrum fit (PASS/FAIL). (Doc.5).

External Review Pack — verifies SCAN→REGION→REPORT with schema checks and manifests. (Doc.9).

(Each pack contains a README/HOW-TO-RUN plus verify_*.py scripts.)


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

## Designed Matter via Tensional Compatibility
Click here:
https://github.com/Xaquer69/sft-theory-and-runners/tree/Designed-Matter-via-Tensional-Compatibility-(SFT)

Distributed under the MIT License. See the LICENSE
 file.

DOI:
https://doi.org/10.5281/zenodo.18648618

Reproducible Physics:
https://zenodo.org/communities/reproducible_physics/records

## Author & Contact

Francisco Queral Rallo
Murcia, España
✉ xaviqueral@gmail.com

ORCID https://orcid.org/0009-0006-5326-0537
