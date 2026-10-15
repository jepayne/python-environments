# Environment inspection summary

Inspection was limited to the four copied virtual environments. No source
projects or original requirement files were present beside them.

All four environments report Python 3.10.6, were isolated from system site
packages, and were originally based on pyenv's Python 3.10.6 installation.

| Environment | Strong top-level signals | Installed snapshot highlights |
| --- | --- | --- |
| bondyield | `arch`, `linearmodels`, `ruptures`, `stargazer`, `statsmodels`, `tables`, scientific stack | `arch 8.0.0`, `linearmodels 7.0`, `numpy 1.26.4`, `pandas 2.2.2`, `scipy 1.13.0` |
| paynecoin | General NumPy/Pandas/SciPy/Matplotlib/SymPy stack | `numpy 1.23.3`, `pandas 1.5.0`, `scipy 1.9.1`, `matplotlib 3.6.0` |
| pytorch | `torch`, `torchvision`, `torchaudio`, Hydra, scikit-learn, statsmodels | `torch 2.5.1`, `torchvision 0.20.1`, `torchaudio 2.5.1`, `numpy 1.23.3` |
| tensorflow | Apple packages `tensorflow-macos` and `tensorflow-metal`, scientific stack | `tensorflow-macos 2.11.0`, `tensorflow-metal 0.7.1`, `numpy 1.24.2`, `pandas 1.5.3` |

## Classification method

The proposed direct requirements combine:

1. packages not required by any other installed distribution;
2. domain-defining packages even when another package also depends on them;
3. obvious notebook and development tools, separated into optional groups.

Everything else in the environments appears to be infrastructure or a
transitive dependency: Jupyter server internals, HTTP clients, serialization
helpers, template engines, plotting internals, and framework support libraries.

## Ambiguous packages omitted pending confirmation

- All environments contain `curio`, and several contain `trio`; these may be
  intentional async tools, but they may also be historical experiments.
- `q` is installed in three environments and may be an intentionally used
  debugging helper.
- PyTorch contains `csr`, `python-math`, and several progress/helper packages.
  `alive-progress` was retained because it looks user-facing; `csr` and
  `python-math` were omitted because their intended use is unclear.
- Bondyield contains `pip-review`; it is an environment-maintenance utility,
  not a runtime requirement, so it was omitted.
- Old compatibility packages such as `backcall`, `pickleshare`, `testpath`,
  `py`, and `ipython-genutils` were treated as historical/transitive.

## Version policy

The `pyproject.toml` files intentionally use package names without version pins.
The installed versions above are evidence, not recommendations. This makes each
file a mutable reference and allows a fresh resolver to select a coherent modern
set. Because these snapshots are old—especially TensorFlow—each environment
should be created and smoke-tested before its dependency list is considered
final.

