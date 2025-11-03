# sft-theory-and-runners

**Structural Field Theory (SFT)** proposes that *all physical observables emerge from a single phenomenon: the microscopic tensile distortion of S*.  
We use a structural scalar field as a minimal descriptor (a map, not the territory) to simulate, calibrate, and validate the program with reproducible runners (JSON + SHA-256 manifests).

> **Start here:** read **[Doc 0 — Abstract & Orientation](./0_SFT_Document0_Abstract_and_Orientation_UPDATED_with_10to14.pdf)** for the ontological stance, scope, current limitations, and falsifiable predictions.

---

## Repository layout

- `Doc_01` … `Doc_14/` — themed subfolders; each contains its document and, when applicable, a matching runner.
- Root contains:
  - `0_SFT_Document0_Abstract_and_Orientation_UPDATED_with_10to14.pdf`
  - `README.md`
  - `LICENSE` (MIT)

Runner outputs are designed to be **reproducible** and include:
- Compact JSON with `schema_version`, criteria/thresholds, random seeds, and verdicts.
- `checksums_SHA256.txt` with a self-hash of the manifest.

---

## Quick run (example)

```bash
# Example (adjust paths/names)
python runners/leptons/particles_sft_full_scan_runner.py leptons \
  --input data/leptons_real.csv \
  --out out/LEPTON_REPORT.json \
  --perm 2000 \
  --jitter 300 \
  --manifest
## Calibration vs prediction

We follow an **α-in** discipline (α provided as an input for calibration).  
Figures/tables across the corpus are explicitly labeled:

- **(C) calibrated** — quantities fitted or normalized using α-in (or analogous anchors).
- **(P) prediction** — out-of-sample and falsifiable.

See **Doc 0** for motivation and cross-reading guidance.

## License

Distributed under the **MIT License**. See the [LICENSE](./LICENSE) file.
## Author & Contact

**Francisco Queral Rallo**  
Murcia, España  
✉ **xaviqueral@gmail.com**
