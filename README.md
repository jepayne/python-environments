# Python environments

Mutable reference environments reconstructed from four existing Python 3.10.6
virtual environments. Each directory contains a small `pyproject.toml` listing
the likely intentional, top-level packages rather than every transitive package
found in the original environment.

## Layout

- `bondyield/` — econometrics, fixed-income analysis, and notebooks
- `paynecoin/` — general scientific-computing and notebook environment
- `pytorch/` — PyTorch machine-learning environment
- `tensorflow/` — Apple Silicon TensorFlow environment

These files deliberately do not lock transitive versions. `uv.lock` is ignored
so this repository remains a set of mutable references. Re-resolve and test each
environment before relying on it for reproducible historical results.

See `inspection-summary.md` for the reconstruction evidence and uncertain
packages that were intentionally omitted.

