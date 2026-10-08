# Overestimation bias with DDPG and TD3 on LunarLander

Mini-project 1 of UM5IN872 Reinforcement Learning (M2 MIND, Sorbonne Université),
Théo Fontaine and Théophile Lahaussois.

Does Layer Normalization in the critic reduce the overestimation bias of DDPG and TD3 on
`LunarLanderContinuous-v3`, and how does this bias relate to performance? The bias is estimated by
comparing the critic's Q-values with the discounted Monte Carlo returns of the same
(state, action) pairs, visited by the deterministic policy.

Design: {DDPG, TD3} × {critic without / with LayerNorm}, 5 seeds each, 100k environment steps,
evaluation every 5k steps on 10 episodes. DDPG and TD3 share every implementation detail
except the three TD3 mechanisms.

## Contents

| | |
|---|---|
| `1_implementation.ipynb` | networks (with or without LayerNorm), DDPG/TD3 update, bias measurement, training loop, and launch of the grid (in parallel, with joblib) |
| `2_analysis.ipynb` | learning curves, bias curves, bootstrap CIs, Welch / Mann–Whitney tests; writes `report/figures/` |
| `runs/<config>/seed<k>/metrics.json` | raw results of each run (configuration + every evaluation) |
| `report/` | LaTeX report |

## Reproducing

```bash
uv sync
uv run python -m ipykernel install --user --name overbias   # Jupyter kernel for the notebooks
uv run jupyter nbconvert --to notebook --execute --inplace 1_implementation.ipynb   # ~3 h on 4 CPU cores
uv run jupyter nbconvert --to notebook --execute --inplace 2_analysis.ipynb
cd report && latexmk main.tex
```

Finished runs are skipped, so an interrupted grid can be resumed by re-running the notebook.
