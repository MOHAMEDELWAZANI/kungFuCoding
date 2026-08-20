<p align="center">
  <img src="assets/kungfu-banner.png" alt="Kung Fu Panda ASCII art" width="880">
</p>

# LeetCode Practice

My problem-solving journey in Python. Started **2026-07-20**.

## Folder layout

```
JsonVsTree/
├─ README.md              this index
├─ tracker.json           the source of truth (status, difficulty, dates, complexity, notes)
├─ problems/              one notebook per LeetCode problem
├─ database_problems/     SQL problems - each notebook runs your query against a real SQLite db
├─ MLproblems/            machine learning - TensorTonic problems + the MNIST classic
├─ tp/                    practical exercises (TP) - bigger, multi-part, not from LeetCode
├─ learn_json/            learning track: the json module, from zero
├─ projects/              real projects built out of what I learned
└─ data/                  input files the notebooks read (.json, .csv, .txt, images)
```

> The folder is `learn_json/`, **not** `json/`. A folder named `json` sitting next
> to your notebook would shadow Python's own `json` module and `import json`
> would import the folder instead. Never name a file or folder after a module
> you import.

Each notebook holds the problem statement in a markdown cell, then `class
Solution` in the code cell below it, then a test cell.

**Reading a data file from a notebook:** notebooks in `tp/` reach the data with
a relative path that goes up one level first, e.g.
`open("../data/company.json")`.

### `status` values in the tracker

- `todo` — file created, not started
- `in_progress` — attempted, not passing yet
- `solved` — accepted
- `review` — passes, but I want to redo it (wrong complexity, ugly, lucky)

## Progress

**20 solved / 25 attempted / 58 total** — last audited **2026-08-15**.

| Difficulty | Solved | Attempted |
|---|---|---|
| Easy | 9 | 11 |
| Medium | 11 | 13 |
| Hard | 0 | 1 |

Every status below was checked by actually running the notebook's own test
cells, not by trusting the old tracker. Four entries moved `todo → solved`, two
moved `solved → in progress`. See [Needs a fix](#needs-a-fix) for what broke.

### Problems

| # | Problem | Difficulty | Status |
|---|---|---|---|
| 1 | [Two Sum](problems/TwoSum.ipynb) | Easy | ✅ solved |
| 9 | [Palindrome Number](problems/PalindromeNumber.ipynb) | Easy | 🔧 in progress |
| 102 | [Binary Tree Level Order Traversal](problems/LevelOrderTraversal.ipynb) | Medium | ✅ solved |
| 103 | [Binary Tree Zigzag Level Order Traversal](problems/ZigzagLevelOrder.ipynb) | Medium | ✅ solved |
| 104 | [Maximum Depth of Binary Tree](problems/MaxDepthBinaryTree.ipynb) | Easy | ✅ solved |
| 105 | [Construct Binary Tree from Preorder and Inorder](problems/ConstructTreePreorderInorder.ipynb) | Medium | ✅ solved |
| 114 | [Flatten Binary Tree to Linked List](problems/FlattenBinaryTree.ipynb) | Medium | ✅ solved |
| 125 | [Valid Palindrome](problems/PalindromeString.ipynb) | Easy | ✅ solved |
| 146 | [LRU Cache](problems/LRUCache.ipynb) | Medium | ✅ solved |
| 148 | [Sort List](problems/SortList.ipynb) | Medium | ⚠️ review |
| 155 | [Min Stack](problems/MinStack.ipynb) | Medium | ✅ solved |
| 206 | [Reverse Linked List](problems/ReverseLinkedList.ipynb) | Easy | ✅ solved |
| 226 | [Invert Binary Tree](problems/InvertBinaryTree.ipynb) | Easy | todo |
| 242 | [Valid Anagram](problems/ValidAnagram.ipynb) | Easy | ✅ solved |
| 295 | [Find Median from Data Stream](problems/FindMedianFromDataStream.ipynb) | Hard | todo |
| 355 | [Design Twitter](problems/DesignTwitter.ipynb) | Medium | 🔧 in progress |
| 359 | [Logger Rate Limiter](problems/LoggerRateLimiter.ipynb) | Easy | todo |
| 362 | [Design Hit Counter](problems/DesignHitCounter.ipynb) | Medium | todo |
| 379 | [Design Phone Directory](problems/DesignPhoneDirectory.ipynb) | Medium | ✅ solved |
| 382 | [Linked List Random Node](problems/LinkedListRandomNode.ipynb) | Medium | todo |
| 535 | [Encode and Decode TinyURL](problems/EncodeDecodeTinyURL.ipynb) | Medium | todo |
| 622 | [Design Circular Queue](problems/DesignCircularQueue.ipynb) | Medium | ✅ solved |
| 707 | [Design Linked List](problems/DesignLinkedList.ipynb) | Medium | ✅ solved |
| 933 | [Number of Recent Calls](problems/NumberOfRecentCalls.ipynb) | Easy | todo |
| 1244 | [Design A Leaderboard](problems/DesignALeaderboard.ipynb) | Medium | ✅ solved |
| 1396 | [Design Underground System](problems/DesignUndergroundSystem.ipynb) | Medium | todo |
| 1472 | [Design Browser History](problems/DesignBrowserHistory.ipynb) | Medium | todo |
| 1603 | [Design Parking System](problems/DesignParkingSystem.ipynb) | Easy | todo |
| — | [Red-Black Tree](problems/RedBlackTree.ipynb) | Hard | 🔧 in progress |

The fifteen **design** problems (146, 155, 295, 355, 359, 362, 379, 382, 535,
622, 707, 1244, 1396, 1472, 1603) are one block on purpose: they are all "pick
the right container", not "find the trick". Each one is a dict, a list, a heap,
or a linked list wearing a different name.

### Database (SQL)

Each notebook builds a real **SQLite** database in memory, runs whatever query you put
in `SOLUTION`, and compares the rows *and* the column names. Nothing is pattern-matched.
LeetCode grades MySQL; where the two engines differ, the notebook says so.

**Nothing started yet** — 175 has `SOLUTION = "select"` and stops there.

| # | Problem | Difficulty | What it teaches | Status |
|---|---|---|---|---|
| 175 | [Combine Two Tables](database_problems/175_CombineTwoTables.ipynb) | Easy | `LEFT JOIN` vs `JOIN` | todo |
| 181 | [Employees Earning More Than Their Managers](database_problems/181_EmployeesEarningMoreThanManagers.ipynb) | Easy | self join, `NULL` comparison | todo |
| 182 | [Duplicate Emails](database_problems/182_DuplicateEmails.ipynb) | Easy | `GROUP BY` / `HAVING` | todo |
| 183 | [Customers Who Never Order](database_problems/183_CustomersWhoNeverOrder.ipynb) | Easy | **the `NOT IN` + `NULL` trap** | todo |
| 196 | [Delete Duplicate Emails](database_problems/196_DeleteDuplicateEmails.ipynb) | Easy | `DELETE`, MySQL error 1093 | todo |
| 176 | [Second Highest Salary](database_problems/176_SecondHighestSalary.ipynb) | Medium | "no rows" is not `null` | todo |
| 180 | [Consecutive Numbers](database_problems/180_ConsecutiveNumbers.ipynb) | Medium | self join vs `LAG` | todo |
| 184 | [Department Highest Salary](database_problems/184_DepartmentHighestSalary.ipynb) | Medium | `GROUP BY` vs `PARTITION BY` | todo |
| 185 | [Department Top Three Salaries](database_problems/185_DepartmentTopThreeSalaries.ipynb) | Hard | `DENSE_RANK` vs `RANK` vs `ROW_NUMBER` | todo |
| 262 | [Trips and Users](database_problems/262_TripsAndUsers.ipynb) | Hard | four requirements at once | todo |

### Machine Learning

From [TensorTonic](https://tensortonic.com), plus MNIST. **NumPy only** — no
sklearn, no PyTorch, no scipy.

Same layout as the LeetCode notebooks: statement, an approach cell that points at
the traps without giving the code, an empty `class Solution`, then a test cell
you can run immediately — every case prints `not implemented` until you fill the
method in, then `OK` or the value it wanted.

| Problem | Difficulty | Topic | The trap | Status |
|---|---|---|---|---|
| [Implement Dot Product](MLproblems/DotProduct.ipynb) | Easy | Linear Algebra | `np.float64` is not `float`; the `ValueError` guard is yours | ✅ solved |
| [Implement Euclidean Distance](MLproblems/EuclideanDistance.ipynb) | Easy | Linear Algebra | predict what `1e200` returns before you run it | todo |
| [Implement Manhattan Distance](MLproblems/ManhattanDistance.ipynb) | Easy | Linear Algebra | when are L1 and L2 equal? answer before the table prints | todo |
| [Implement Cosine Similarity](MLproblems/CosineSimilarity.ipynb) | Easy | Linear Algebra | zero vector → `0.0`; guard *before* dividing, not after | ✅ solved |
| [Weighted Cosine Similarity](MLproblems/WeightedCosineSimilarity.ipynb) | Easy | Linear Algebra | weighting *after* you normalise is a different formula — and it can return > 1 | todo |
| [Jaccard Similarity](MLproblems/JaccardSimilarity.ipynb) | Easy | Recommender Systems | empty/empty raises — same bug shape as the zero vector | todo |
| [Adjusted Cosine Similarity](MLproblems/AdjustedCosineSimilarity.ipynb) | Medium | Recommender Systems | `R.mean(axis=1)` is wrong; `0` means *unrated* | ✅ solved |
| [Soft Cosine Similarity](MLproblems/SoftCosineSimilarity.ipynb) | Medium | NLP | `S` symmetric with a unit diagonal is **not** enough — if it isn't PSD, `sqrt` returns `nan` | todo |
| [MNIST Handwritten Digits](MLproblems/MnistDigits.ipynb) | Medium | Classification | four models, backprop by hand | todo |

**Weighted cosine** is the diagonal case of soft cosine — `S = diag(w)` — so do
it first if soft cosine bites. Every sum picks up a `w_i`, including the two
inside the square roots; move the weights outside them and you get a
"similarity" that can exceed 1. It also asks you to predict, on paper, whether
scaling every weight changes the answer.

**Soft cosine** is the first one that isn't a one-liner. `a · b` becomes
`aᵀ S b`, so write `bilinear(x, S, y)` once and call it three times. Two optional
follow-ups are scaffolded in the same notebook: the Cholesky version
(`S = L Lᵀ` → soft cosine *is* plain cosine on `Lᵀa` and `Lᵀb`, factored once,
which is how a vector DB serves it at ordinary-cosine speed) and
`soft_cosine_matrix`, one query against every row.

**MNIST** — the IDX loader and the ASCII viewer are given (plumbing, marked
don't-edit); the four models are the exercise. Build them in order, each one
fixing what the last got wrong:

| | Model | Target accuracy |
|---|---|---|
| V1 | Nearest centroid | ~0.82 |
| V2 | k-NN (`k=3`) | ~0.94 |
| V3 | Softmax regression | ~0.92 |
| V4 | Neural net, 784→256→10 ReLU | **>0.97** |

Targets are "am I in the right neighbourhood", not answers. V3 scoring *below* V2
is expected — arguing why you would still ship V3 is part of the problem. The
loader downloads ~11 MB on first run and caches to `data/mnist.npz` (gitignored).

The three solved ones feed straight into the
[geometric metrics lab](projects/geometric_metrics/) below — same formulas, but
there they run on 2221 real documents instead of a hand-built 3×3.

### TP

| TP | Topic | Data | Status |
|---|---|---|---|
| [Company Org Chart](tp/TP_OrgChart.ipynb) | tree + json + dict | [company.json](data/company.json) | 🔧 in progress |
| [Store Catalog](tp/TP_JsonCatalog.ipynb) | recursion over nested JSON | [catalog.json](data/catalog.json) | todo |

TP1: the linked-list/tree classes and the recursive `printPersons` are written;
exercises 3–9 (count, depth, payroll, index, team cost, boss map, `Employee`
objects) are still `pass`. Its cells also don't run in order — see below.

### Learning track — JSON

Do these **in order**, they build on each other. Paused the Org Chart TP until
this is done.

| # | Notebook | What it teaches | Data | Status |
|---|---|---|---|---|
| 01 | [The 4 functions](learn_json/01_JsonBasics.ipynb) | `load` / `loads` / `dump` / `dumps`, the JSON↔Python type table | [student.json](data/student.json) | ✅ done |
| 02 | [List of objects](learn_json/02_JsonLists.ipynb) | the shape 90% of real JSON has: filter, `max(key=)`, sort, group, index | [products.json](data/products.json) | ✅ done |
| 03 | [Nested & missing keys](learn_json/03_JsonNested.ipynb) | walking chains, `KeyError`, `.get(k, default)`, chained `.get` | [orders.json](data/orders.json) | todo |
| 04 | [Writing JSON](learn_json/04_JsonWrite.ipynb) | `indent`, `ensure_ascii=False`, what JSON can't store, string keys | [scores.json](data/scores.json) | todo |
| 05 | [Errors & a messy file](learn_json/05_JsonErrors.ipynb) | `JSONDecodeError`, holes in real data, flattening to clean records | [library.json](data/library.json) | todo |

01 and 02 are done — 02 went past what was asked and built a
`dataclass` + Encoder / Decoder / Repository layer. **03, 04 and 05 are still
empty**: every code cell is a bare `# TODO`. That is the next thing to pick up,
and TP1 stays paused until they're finished.

### Projects

| # | Project | Stack | Guide | Status |
|---|---|---|---|---|
| 1 | Org Chart Manager | Flask + SQLite | [PROJECT_1_GUIDE.md](projects/PROJECT_1_GUIDE.md) | todo — guide written, no code |
| 2 | [Plant Disease Cascade](../ClassificationDesPlantes/plantdisease/) | PyTorch, CNN | [PROJECT_2_GUIDE.md](../ClassificationDesPlantes/PROJECT_2_GUIDE.md) | todo — 2025 baseline only |
| 3 | [Geometric Metrics Lab](projects/geometric_metrics/) | NumPy, scipy, sklearn | [README](projects/geometric_metrics/README.md) | todo — 10 problems scaffolded |

**Project 1** starts after TP1 and #102 / #103, and reuses
[company.json](data/company.json) as seed data. The guide already has the
adjacency-list schema, the 5 build steps, and the Repository / Service split.

**Project 2** is a from-scratch rebuild of the June 2025 Keras project: a leaf
photo in, plant + disease out, over 25 classes and 31 397 images. It lives in the
sibling folder `../ClassificationDesPlantes/`, **not** in `projects/`. So far it
holds the guide and `plantdisease/baseline_2025/` — the 2025 confusion matrices
and training curves, kept as the number to beat (**89.42%** end to end). No code
written yet.

**Project 3** ([geometric_metrics/](projects/geometric_metrics/)) is the newest,
added 2026-08-13. Ten problems (0–8, with a 6b) on one retrieval task —
`precision@10` over 20newsgroups and wine — going cosine → Euclidean → the
normalise-then-Euclidean identity → Minkowski sweep → weighted cosine → soft
cosine → Mahalanobis → the four distance→similarity conversions. Each one is
laid out like the `MLproblems/` notebooks: statement with formula, examples,
hints, requirements and constraints, then an approach cell naming the traps,
then the stub, then the verification cell. **14 `NotImplementedError` stubs, none
filled, no cell executed yet.** Its README lists the expected numbers per
problem, so a mismatch is a signal rather than a guess. Read the gensim warning
in there before you reach problem 6b: gensim will not build on this Python 3.14
venv.

## Needs a fix

Found by running every notebook top to bottom on 2026-08-15. These are not
"unsolved" — they are files that misreport themselves.

| File | Problem |
|---|---|
| [RedBlackTree.ipynb](problems/RedBlackTree.ipynb) | Was marked **solved**, doesn't run. The cell holds two half-merged versions: `class Node` takes `key`, but `RedBlackTree` builds `Node(data=...)`. First insert test → `TypeError`. |
| [DesignTwitter.ipynb](problems/DesignTwitter.ipynb) | Was marked **solved**. The 8-case suite is green, but the EXTRA cell (the gap LeetCode found) raises `KeyError: 2` — `follow()` guards the followee, not the follower. |
| [LinkedListRandomNode.ipynb](problems/LinkedListRandomNode.ipynb) | The file doesn't parse. `def __init__(self, head):` and `def getRandom(self):` have empty bodies → `IndentationError` before any test runs. Put `pass` back. |
| [ZigzagLevelOrder.ipynb](problems/ZigzagLevelOrder.ipynb) | Solution is correct, but cell 1 begins with a stray `from zope.interface.common import optional` (IDE auto-import). zope isn't installed, so it dies on any clean machine. Delete the line. |
| [ConstructTreePreorderInorder.ipynb](problems/ConstructTreePreorderInorder.ipynb) | `import pandas as pa`, and pandas isn't in `.venv`. Install it or drop the import. |
| [DesignCircularQueue.ipynb](problems/DesignCircularQueue.ipynb) | V2 (array + modulo) passes everything, but V1 (linked list) sits **above** the tests, so a top-to-bottom run tests V1, prints two FAILs and crashes. Move V2 up or delete V1. |
| [SortList.ipynb](problems/SortList.ipynb) | Correct, and it re-splices the original nodes — but it's an insertion sort. 50 000 random values take ~27 s (44 s on the adversarial case) against 7 ms when already sorted. That's O(n²) and would TLE. Redo with merge sort. |
| [TP_OrgChart.ipynb](tp/TP_OrgChart.ipynb) | Cells out of order: the class cell ends by printing `tree.linkedList` before `tree` exists, and the cell that creates it calls `TreeFixed()`, which is defined nowhere. |

## Environment

`.venv/` is Python **3.14** with numpy, scipy, scikit-learn, matplotlib, joblib.
Not installed: **pandas** (#105 wants it) and **gensim** (no 3.14 wheel, and the
source build needs `python3-dev`; problem 6b of the metrics lab works around it).

```bash
source .venv/bin/activate
jupyter notebook          # or just open the folder in PyCharm
```
