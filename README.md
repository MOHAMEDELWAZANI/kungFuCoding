<p align="center">
  <img src="assets/kungfu-banner.png" alt="Kung Fu Panda ASCII art" width="880">
</p>

# LeetCode Practice

My problem-solving journey in Python. Started **2026-07-20**.

## Folder layout

```
Problems/
├─ README.md        this index
├─ tracker.json     the source of truth (status, difficulty, dates, complexity)
├─ problems/        one notebook per LeetCode problem
├─ database_problems/  SQL problems - each notebook runs your query against a real SQLite db
├─ MLproblems/      machine learning - TensorTonic problems + the MNIST classic
├─ tp/              practical exercises (TP) - bigger, multi-part, not from LeetCode
├─ learn_json/      learning track: the json module, from zero
├─ projects/        real projects built out of what I learned
└─ data/            input files the notebooks read (.json, .csv, .txt, images)
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
- `review` — solved but I want to redo it later

## Progress

**13 solved / 16 attempted**

### Problems

| # | Problem | Difficulty | Status      |
|---|---|---|-------------|
| 9 | [Palindrome Number](problems/PalindromeNumber.ipynb) | Easy | in_progress |
| 125 | [Valid Palindrome](problems/PalindromeString.ipynb) | Easy | ✅ solved   |
| 1 | [Two Sum](problems/TwoSum.ipynb) | Easy | ✅ solved   |
| 104 | [Maximum Depth of Binary Tree](problems/MaxDepthBinaryTree.ipynb) | Easy | ✅ solved   |
| 102 | [Level Order Traversal](problems/LevelOrderTraversal.ipynb) | Medium | ✅ solved   |
| 103 | [Zigzag Level Order Traversal](problems/ZigzagLevelOrder.ipynb) | Medium | ✅ solved   |
| 242 | [Valid Anagram](problems/ValidAnagram.ipynb) | Easy | ✅ solved   |
| 226 | [Invert Binary Tree](problems/InvertBinaryTree.ipynb) | Easy | todo        |
| 206 | [Reverse Linked List](problems/ReverseLinkedList.ipynb) | Easy | ✅ solved   |
| 114 | [Flatten Binary Tree to Linked List](problems/FlattenBinaryTree.ipynb) | Medium | ✅ solved   |
| 105 | [Construct Binary Tree from Preorder and Inorder Traversal](problems/ConstructTreePreorderInorder.ipynb) | Medium | ✅ solved   |
| 155 | [Min Stack](problems/MinStack.ipynb) | Medium | ✅ solved   |
| 355 | [Design Twitter](problems/DesignTwitter.ipynb) | Medium | ✅ solved   |
| 382 | [Linked List Random Node](problems/LinkedListRandomNode.ipynb) | Medium | todo        |
| 379 | [Design Phone Directory](problems/DesignPhoneDirectory.ipynb) | Medium | ✅ solved   |
| 622 | [Design Circular Queue](problems/DesignCircularQueue.ipynb) | Medium | todo        |
| 707 | [Design Linked List](problems/DesignLinkedList.ipynb) | Medium | todo        |
| 148 | [Sort List](problems/SortList.ipynb) | Medium | todo        |
| 1603 | [Design Parking System](problems/DesignParkingSystem.ipynb) | Easy | todo        |
| 933 | [Number of Recent Calls](problems/NumberOfRecentCalls.ipynb) | Easy | todo        |
| 359 | [Logger Rate Limiter](problems/LoggerRateLimiter.ipynb) | Easy | todo        |
| 535 | [Encode and Decode TinyURL](problems/EncodeDecodeTinyURL.ipynb) | Medium | todo        |
| 1396 | [Design Underground System](problems/DesignUndergroundSystem.ipynb) | Medium | todo        |
| 362 | [Design Hit Counter](problems/DesignHitCounter.ipynb) | Medium | todo        |
| 1472 | [Design Browser History](problems/DesignBrowserHistory.ipynb) | Medium | todo        |
| 1244 | [Design A Leaderboard](problems/DesignALeaderboard.ipynb) | Medium | ✅ solved   |
| 146 | [LRU Cache](problems/LRUCache.ipynb) | Medium | todo        |
| 295 | [Find Median from Data Stream](problems/FindMedianFromDataStream.ipynb) | Hard | todo        |
| — | [Red-Black Tree](problems/RedBlackTree.ipynb) | Hard | ✅ solved   |

### Database (SQL)

Each notebook builds a real **SQLite** database in memory, runs whatever query you put
in `SOLUTION`, and compares the rows *and* the column names. Nothing is pattern-matched.
LeetCode grades MySQL; where the two engines differ, the notebook says so.

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

### TP

| TP | Topic | Data | Status |
|---|---|---|---|
| [Company Org Chart](tp/TP_OrgChart.ipynb) | tree + json + dict | [company.json](data/company.json) | in_progress |
| [Store Catalog](tp/TP_JsonCatalog.ipynb) | recursion over nested JSON | [catalog.json](data/catalog.json) | todo |

### Learning track - JSON

Do these **in order**, they build on each other. Paused the Org Chart TP until
this is done.

| # | Notebook | What it teaches | Data |
|---|---|---|---|
| 01 | [The 4 functions](learn_json/01_JsonBasics.ipynb) | `load` / `loads` / `dump` / `dumps`, the JSON↔Python type table | [student.json](data/student.json) |
| 02 | [List of objects](learn_json/02_JsonLists.ipynb) | the shape 90% of real JSON has: filter, `max(key=)`, sort, group, index | [products.json](data/products.json) |
| 03 | [Nested & missing keys](learn_json/03_JsonNested.ipynb) | walking chains, `KeyError`, `.get(k, default)`, chained `.get` | [orders.json](data/orders.json) |
| 04 | [Writing JSON](learn_json/04_JsonWrite.ipynb) | `indent`, `ensure_ascii=False`, what JSON can't store, string keys | [scores.json](data/scores.json) |
| 05 | [Errors & a messy file](learn_json/05_JsonErrors.ipynb) | `JSONDecodeError`, holes in real data, flattening to clean records | [library.json](data/library.json) |

### Projects

| # | Project | Stack | Guide | Status |
|---|---|---|---|---|
| 1 | Org Chart Manager | Flask + SQLite | [PROJECT_1_GUIDE.md](projects/PROJECT_1_GUIDE.md) | not started |
| 2 | [Plant Disease Cascade](../ClassificationDesPlantes/plantdisease/) | PyTorch, CNN | [PROJECT_2_GUIDE.md](../ClassificationDesPlantes/PROJECT_2_GUIDE.md) | not started |

Project 2 is a from-scratch rebuild of the June 2025 Keras project: a leaf photo
in, plant + disease out, over 25 classes and 31 397 images. The 2025 results are
kept in `../ClassificationDesPlantes/plantdisease/baseline_2025/` as the target (**89.42%** end to
end), and the images are in `../ClassificationDesPlantes/plantes/` — a 9 MB sample committed, the 542 MB
full split gitignored.
