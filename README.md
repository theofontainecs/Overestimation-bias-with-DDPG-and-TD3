# Overestimation bias with DDPG and TD3 on LunarLander

Mini-project 1 of UM5IN872 Reinforcement Learning (M2 MIND, Sorbonne Université).

Study of the impact of Layer Normalization on the overestimation bias of DDPG and TD3 on
`LunarLanderContinuous`, and of the impact of this bias on performance. The bias is estimated by
comparing critic Q-values with Monte Carlo returns from the same (state, action) pairs.

Deadline: Friday, October 9 2026, 23:59. The report is at most 4 pages, in English, and must be named `name1_name2.pdf`.

## Layout

```
report/            LaTeX report (main.tex, refs.bib, figures/)
```

## Building the report

```bash
cd report && latexmk main.tex
```

The PDF is written to `report/build/main.pdf`.
