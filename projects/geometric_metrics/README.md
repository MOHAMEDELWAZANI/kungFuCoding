# Geometric Metrics — a ten-problem set

Consolidating the geometric family (cosine, Minkowski, Mahalanobis, and the
distance→similarity conversions) as ten problems on one task, across two
datasets chosen to disagree with each other.

**I implement. The notebook is scaffolding.** Every `raise NotImplementedError`
is mine to fill; the verification cells below each stub are not.

**Task everywhere:** for each sample, retrieve its 10 nearest neighbours
(excluding itself) and score `precision@10` = fraction sharing the query's true
label. Report mean and std across queries. One number, so ten metrics fit on one
scoreboard.

## The set

Each problem follows the `../../MLproblems/` layout: statement with formula,
examples, hints, requirements and constraints → an approach cell that names the
traps without giving the code → the stub → the verification cell → an
"after it passes" cell.

| # | problem | difficulty | stubs |
|---|---|---|---|
| 0 | Retrieval Harness | easy | `top_k_neighbours`, `precision_at_k` |
| 1 | TF-IDF + Cosine — the baseline | medium | `cosine_scratch` |
| 2 | Euclidean on Unnormalised TF-IDF | easy | `euclidean_scratch` |
| 3 | L2-Normalise, then Euclidean | medium | `l2_normalize` |
| 4 | Minkowski Sweep over p | medium | `minkowski_scratch` |
| 5 | Weighted Cosine, `w = idf²` | medium | `weighted_cosine` |
| 6 | Soft Cosine — the toy vocabulary | medium | `soft_cosine` |
| 6b | Soft Cosine on the Real Corpus | hard | `build_S` |
| 7 | Mahalanobis on Wine | hard | `mahalanobis_scratch` |
| 8 | Distance → Similarity, four ways | easy | `sim_reciprocal`, `sim_gaussian`, `sim_exponential`, `sim_bounded` |

14 stubs, plus one open decision that is not a function: the zero-vector fork in
problem 1, which every number below it depends on.

**Solve them in order.** Problems 1–8 all call the harness from problem 0, and
problems 2–6b share the corpus built in problem 1.

## Run it

```bash
jupyter notebook geometric_metrics.ipynb     # or open it in PyCharm
```

Dependencies are already in `../../.venv`: numpy, scipy, scikit-learn,
matplotlib. First run downloads 20newsgroups (~14 MB) to `~/scikit_learn_data/`.

Everything is seeded (`SEED = 0`), so the numbers below are reproducible.
A mismatch is a signal, not rounding.

### ⚠️ gensim, needed for problem 6b — read this before you get there

**gensim will not install on this machine.** The venv is Python **3.14**; gensim
publishes no wheel for it and the source build fails on a missing `Python.h`
(`python3-dev` headers). I confirmed this by trying:

```
gensim/models/word2vec_inner.c:25:10: fatal error: Python.h: No such file or directory
```

Two ways forward, your call — decide before problem 6b, not during it:

1. **Separate venv on Python 3.11/3.12** just for problem 6b, then
   `pip install gensim`. You get the real `SparseTermSimilarityMatrix` and
   `glove-wiki-gigaword-100` (a 128 MB download) exactly as specified.
2. **Stay on 3.14** and build the `S` matrix from term vectors you derive from
   this corpus instead (a `TruncatedSVD` of the term–document matrix gives you
   distributional term embeddings — same idea as GloVe, computed locally). The
   soft-cosine maths you write is identical; only the source of `S` changes.

Either way problem 6 — the toy-vocabulary half — runs anywhere, and that is the
half where you can actually read `S` and check its eigenvalues.

---

## Expected results

Added one problem at a time, as I finish each. Read a section **after** running
the problem — it's here to separate "I learned something" from "I have a bug."

### Problem 0 — Retrieval Harness

No dataset yet. The verification cell is four points on a line, hand-computed:

| check | expected |
|---|---|
| `k=1`, self excluded | mean precision **0.0** |
| `k=2`, self excluded | per-query **[0.5, 0.0, 0.0, 0.5]**, mean **0.25**, std **0.25** |
| `-D` with `higher_is_better=True` | identical to `D` with `False` |

**If `k=1` gives you 1.0**, you are not excluding the query itself — every point
is its own nearest neighbour. That single bug inflates every later problem, and
it inflates them *plausibly*, which is what makes it dangerous.

### Problem 1 — TF-IDF + Cosine

The corpus is **2221 documents × 5000 terms**, 4 categories, density ~1.1%.

**Your number depends on a decision you make, and both answers are correct:**

| zero-vector choice | docs | precision@10 | std |
|---|---|---|---|
| (a) drop the 66 zero-norm rows | 2155 | **0.7491** | 0.2587 |
| (b) keep them, define `cos(0, y) := 0` | 2221 | **0.7343** | 0.2686 |

Random baseline is ~0.25, so either way cosine is doing real work.

**66 documents have `‖x‖ = 0`.** That is not a data error — `remove=('headers',
'footers','quotes')` empties some posts down to nothing. Option (b) scores lower
because those 66 documents match nothing, so they retrieve 10 effectively random
neighbours and contribute ~0.25 each.

Two traps are planted in this problem:

- `scipy.spatial.distance.cosine(a, 2a)` returns **0.000**. It is a *distance*.
  Parallel vectors give 0, not 1. The similarity is `1 - that`.
- A zero vector has no direction, so cosine is `0/0 = nan`. One `nan` poisons
  every `argsort` it touches. sklearn quietly returns `0.0` instead, which is
  arguably worse — the document is never retrieved and nothing warns you.

If `cosine_scratch` disagrees with sklearn by ~`1e-16`, that's float noise and
`atol=1e-10` absorbs it. If it disagrees by anything visible, check whether you
normalised rows (axis=1) rather than columns.

**Carry the choice forward.** Problem 3 behaves very differently under (b): a
zero vector cannot be normalised, so it stays at the origin, distance exactly
`1.0` from every unit vector while two unrelated real documents sit at `√2`. The
66 blanks become universal nearest neighbours and problem 3's ranking check fails
on purpose. That is the cost of (b) arriving two problems late, which is how this
kind of decision usually bills you.
