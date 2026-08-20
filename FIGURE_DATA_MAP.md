# New Main-Text Figures — Data & What They Replace

Three big figures, each a single figure with 2–3 subplots. Each subplot's data
source and the original (main-text/appendix) content it lets you shrink or drop.

---

## Figure 1 — `fig1_motivation.pdf` (Motivation)

| Subplot | What it shows | Data source | Replaces |
|---|---|---|---|
| **(a)** Compute is flat across consequence | Thinking-token allocation by consequence class (0/1/2), normalized within-model, for 5 models (Qwen3-8B, Qwen3-VL, DeepSeek-R1, o4-mini, Claude 4.5). ρ / "capped" printed under each. | 5-model native-thinking audit: `qwen3_think.jsonl`, `qwen3vl_think_v2.jsonl`, `exp_audit_r1.jsonl`, `exp_audit_oseries.jsonl`, `phase4_claude.jsonl` + consequence labels | **the old card-style Figure 1 (`1.pdf`)** and the core of Appendix *Full Audit of Native Thinking Allocation* (the per-model ρ / saturation facts now live in the axis labels) |
| **(b)** High-consequence tasks: big headroom | Solve rate at low vs high compute, by consequence class (class-2: 7% → 59%). | 16-model tier data `exp5_table.csv` (`p_cheap`, `p_premium` by class) | **new** — establishes *why* headroom exists; sets up the main result. Nothing removed, but it motivates the whole paper in one panel. |

**Motivation message (both panels):** current models neither spend more compute on
high-consequence tasks (a) nor is that because the tasks are hopeless — they have
the largest untapped headroom (b).

---

## Figure 2 — `fig2_main.pdf` (Main result)

| Subplot | What it shows | Data source | Replaces |
|---|---|---|---|
| **(a)** Success on the tasks that matter | High-consequence (class-2) solve rate by routing strategy: difficulty 7% / predicted-difficulty 29% / random 20% / **consequence 51%** / oracle 59%. | Main results `exp5_table.csv` + predictor `predictor_labels.jsonl` (= Table 1's class-2 column) | **makes Table 1's class-2 column visual** — the headline reframe |
| **(b)** Compute is reallocated, not created | Solve rate by consequence class under random vs consequence routing (takes from low-cons., boosts high-cons.). | same allocation data, split by class | **new** — explains why overall accuracy is flat while class-2 jumps (the redistribution mechanism) |
| **(c)** Lower cost-weighted loss | Loss reduction vs difficulty by strategy: random +13.8 / pred-diff +16.5 / **consequence +21.8** / priority +30.7 / oracle +23.3 %. | Table 1's Δ column | **Table 1 Δ column + the headline of `fig_pareto`** (the operating-point summary of the Pareto curve) |

---

## Figure 3 — `fig3_generalization.pdf` (Generalization + external validity)

**This one figure lets you collapse 2–3 appendices into the main text.**

| Subplot | What it shows | Data source | Replaces |
|---|---|---|---|
| **(a)** Boundary conditions hold out of domain | Routing gain over random for difficulty vs consequence across SWE-Lite / BIRD / FinQA / MATH (cons. wins on SWE, diff. wins on MATH, neither on BIRD/FinQA). | OOD probes (BIRD/FinQA/MATH allocation) + main SWE | **the core result of Appendix *Out-of-Domain Probes*** (the boundary-condition quadrant/table) |
| **(b)** Labels track maintainer triage | Django Trac maintainer-assigned "Bug" rate by our consequence class: 27 / 70 / 79 %, trend p = 0.002. | `exp_trac.jsonl` + `exp_trac_analysis.py` | **the core result of Appendix *External Validity: Maintainer-Revealed Severity*** |
| **(c)** Stakes flip the winner (MATH) | Consequence − difficulty margin vs dollar-stakes spread on MATH; consequence overtakes difficulty around 30×. | dollar-stakes sweep `finmath_stakes.py` (Design A, MATH) | **the dollar-stakes crossover** from the OOD/stakes appendix |

---

## Net effect on the appendix

- **Fig 1(a)** → shrink Appendix *Full Audit of Native Thinking Allocation* to a pointer.
- **Fig 2(c)** → the Pareto appendix (`fig_pareto`) becomes optional / a pointer.
- **Fig 3(a,b,c)** → shrink Appendices *Out-of-Domain Probes*, *External Validity*, and the *dollar-stakes* sweep to short pointers + text analysis.

Keep the numbers in the appendix tables if you like, but the figures carry the
message in the main text; the prose can then be a paragraph of analysis rather than
a full appendix section.
