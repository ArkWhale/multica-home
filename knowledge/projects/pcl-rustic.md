# pcl-rustic Project Summary

## Definition

`pcl-rustic` is a high-performance Python point-cloud library, implemented in
Rust (PyO3 + `burn` tensor backend), intended to replace Open3D for LAS/LAZ
workflows in the Leo workspace.

## Planned capabilities

- Typed-attribute storage (`f32/f64/u8/u16/u32/i32/bool`) with full LAS fidelity
- NumPy zero-copy ingest and export
- Coordinate ops — transform, rotate, translate, scale, concatenate
- Selection — spatial (AABB / OBB / index) **and** feature-based (classification,
  intensity range, arbitrary attribute predicate)
- Downsampling — voxel (NEAREST_TO_CENTROID / AVERAGE / RANDOM_SEEDED) and
  true random subsampling
- LAS / LAZ / CSV / Parquet I/O
- Outlier removal — Statistical (SOR) and Radius (ROR)
- Registration — ICP (point-to-point, point-to-plane) and Generalized ICP
- GPU acceleration on hot paths via `burn` `Router<(Wgpu, NdArray)>`
- End-to-end examples: spatial-grid split + classification-aware split, each
  downsampled per-slice and concatenated back

## Environment & packaging

Non-negotiable per LEO-36:

- **Rust** — implementation language
- **Cargo** — Rust dependencies, build, publish of the native crate
- **uv** — Python environment, dev tooling, wheel install
- **maturin** — Rust ↔ Python bridge (`[tool.maturin]` in `pyproject.toml`)

## Workspace issue map

- `LEO-36`: Plan pc-rustic (this repo) — parent roadmap issue
- `LEO-37..LEO-43`: one per RFC (M1–M6 plus the umbrella roadmap tracker);
  assigned to Dev

## RFC map

All RFCs live in-repo at `pcl-rustic/docs/plans/`. Naming:
`rfc-{id}-{date}-{title}.md`.

| RFC | Milestone | Focus |
|---|---|---|
| RFC-0001 | — (umbrella) | Roadmap, cross-cutting architecture, out-of-scope |
| RFC-0002 | M1 | API reset, typed attributes, zero-copy NumPy getters |
| RFC-0003 | M2 | Coordinate ops, `select(mask)` primitive, feature selectors |
| RFC-0004 | M3 | GPU hot-path rewrite (voxel binning, gather, benchmarks) |
| RFC-0005 | M4 | KD-tree, kNN / radius search, normal estimation |
| RFC-0006 | M5 | SOR / ROR outlier removal |
| RFC-0007 | M6 | ICP + Point-to-Plane + GICP registration |

## Repo mapping

- Product repo: `ArkWhale/pcl-rustic` (workspace-registered 2026-04-30)
- Shared context repo: `ArkWhale/multica-home`
- Upstream fork: `HernandoR/pcl-rustic` — agent work pushes to ArkWhale only

## Notes for agents

- The issue and planning discussion use "pc-rustic" interchangeably with
  "pcl-rustic". The repo, crate, PyPI package, and Python module are all
  `pcl-rustic` / `pcl_rustic`.
- Use the product repo for implementation details.
- Use this summary when you need high-level scope without loading every RFC.
- When authoring a new RFC, follow `templates/prompts/rfc-authoring.md`.
