<!-- solve-problem:6623bf7e-d793-4a03-b069-afedbcf9d3c0 -->
# Tight bounds on planar k-sets

A [Tangle Solve problem](https://solve.tangle.tools/problems/6623bf7e-d793-4a03-b069-afedbcf9d3c0).

## What is the problem?

Given a set S of n points in the plane in general position (no three collinear), a **k-set** is a subset of exactly k points that can be separated from the rest by a line. Equivalently, it is the set of points lying strictly below (or above) some line, with |below| = k. The problem: determine, as a function of n and k, the maximum number of k-sets over all such S:

f(n, k) = max over S of #{k-sets of S}.

The central open regime is **k ≈ n/2**, i.e., counting **halving lines**: lines through two points of S leaving exactly (n−2)/2 points on each side. Let h(n) denote the max number of halving lines. Known: n^1/log n-ish lower bound construction (Tóth; refined by Nivasch) versus Dey's upper bound O(n^{4/3}). The gap is enormous — the true exponent is conjectured to be near 1 (possibly n^{1+o(1)}), but even n^{1.01} upper bounds are out of reach. Ambiguity note: "tight bounds" could mean (a) resolving the halving-line exponent Θ(?), or (b) closing the gap for all k between the Lovász/Dey upper bounds and known lower constructions. Most researchers read it as (a), with (b) as the general-k version.

## Why does it matter?

The k-set problem is a canonical measure of the worst-case complexity of a **level** in an arrangement of lines (the k-set count of point set S equals the complexity of the k-th level of the dual arrangement), and levels govern output sizes and running times of geometric algorithms for range searching, halfspace reporting, and kinetic geometric computation. Halving-line bounds also control the worst-case running time of algorithms that maintain combinatorial structure under motion (e.g., kinetic Delaunay triangulations). It is one of the flagship open problems in discrete geometry (TOPP Problem 7), so any progress would reshape extremal combinatorics of point configurations.

## What's already known?

**Upper bounds.** Lovász (1971): O(n√k). Dey (1998), via a crossing-number/junction argument on the ≤k-set graph: **O(nk^{1/3})**, hence O(n^{4/3}) for k = n/2. This is the standing record; Dey's technique caps out because the crossing-lemma inequality it uses is itself tight in the relevant range.

**Lower bounds.** Erdős–Lovász–Simmons–Straus (1973): n·e^{Ω(√log k)}. Tóth (2000): n·e^{Ω(√(log k))} improved, giving halving-line constructions with n e^{Ω(√log n)} — superlinear but barely so. Nivasch (2008) and Sharir–Zahl improved constants/exponents slightly in the lower-bound exponent; the record remains n^{1+Ω(1/√log log n)}-type (verify exact exponent against Nivasch's survey).

So for halving lines: lower ≈ n^{1+o(1)}, upper O(n^{4/3}); exponent between 1 and 4/3 entirely unknown. Techniques tried: crossing numbers of level graphs, allowed/disallowed edges, topological arguments, random point sets (which have only ~n halving lines — the extremal configurations are highly structured, near "stretched grids").

## What would count as solving it?

Any of:
1. **Upper bound improvement:** a proof that h(n) ≤ n^{4/3−ε} for explicit ε > 0 — even beating Dey by any polynomial factor beyond n^{4/3−o(1)} would be major.
2. **Matching lower bound:** a construction with h(n) ≥ n^{c} for c > 1 polynomially separated from linear (e.g., n^{1.01}).
3. **Tight resolution:** prove h(n) = n^{1+o(1)} (matching Tóth/Nivasch-style lower bounds), or Θ(n^{4/3}).
4. **General k:** determine whether f(n,k) = Θ(nk^{1/3}) or close the gap against the e^{Ω(√log k)} lower bounds for all k.

A referee accepts: a rigorous proof or explicit construction in the standard general-position model, with full constants or exponents, resolving one of the above.

## How to start

1. Read Dey (1998) thoroughly — understand exactly where the nk^{1/3} bound loses tightness (the crossing-number bound on the ≤k-set graph). Any improvement must evade this bottleneck.
2. Read Nivasch's survey "Halving lines, k-sets, and related problems" (or TOPP Problem 7) for the current landscape and the known obstructions.
3. Study Tóth's and Nivasch's lower-bound constructions (based on iterated point substitutions near stretched grids) to understand what extremal structure plausibly looks like.
4. Natural attack: dualize to levels in arrangements and try new charging schemes or topological/allowable-sequence arguments; alternatively seek higher-moment or higher-order junction counting beyond Dey's pair counting. Main obstacle: no known technique separates "many k-sets" from crossing-number-type inequalities that are saturated by known constructions that nonetheless have few k-sets.

## Key references

- T. K. Dey, *Improved bounds for planar k-sets and related problems*, Discrete Comput. Geom. 19:373–382, 1998. Proves the O(nk^{1/3}) upper bound on k-sets via crossing numbers of level graphs. https://doi.org/10.1007/PL00009354
- Cs. D. Tóth, *Point sets with many k-sets*, Discrete Comput. Geom. 26:187–194, 2001. Constructs point sets with n·e^{Ω(√(log k / log log k))} k-sets (verify exact form). https://doi.org/10.1007/s004540010021
- G. Nivasch, *An improved lower bound on the number of points needed to decide halving lines*, and his survey on k-sets (verify exact titles/venues). Improves halving-line lower bounds and surveys the problem.
- The Open Problems Project (TOPP), Problem 7 (k-sets). Community-maintained status of the problem: https://topp.openproblem.net/p7 (verify link).
- L. Lovász (1971) and Erdős–Lovász–Simmons–Straus (1973), early upper/lower bounds (see TOPP Problem 7 for citations).

## Warnings

- "Tight bounds" is aspirational; the realistic goal is any exponent improvement. Don't promise Θ(·).
- General position is essential; k-set counts blow up or become ill-defined with collinearities/degeneracies.
- Easy-looking approaches (direct crossing-number tweaks, induction on n, probabilistic constructions) have all been tried and fail for documented reasons — random point sets have very *few* k-sets, so lower bounds need intricate recursive constructions.
- The analogous problem in 3D and higher is even more open; don't conflate planar results with higher-dimensional level-complexity bounds.

---
*`ALGO-000147` · unverified*

## Acceptance guidance

Any of:
1. **Upper bound improvement:** a proof that h(n) ≤ n^{4/3−ε} for explicit ε > 0 — even beating Dey by any polynomial factor beyond n^{4/3−o(1)} would be major.
2. **Matching lower bound:** a construction with h(n) ≥ n^{c} for c > 1 polynomially separated from linear (e.g., n^{1.01}).
3. **Tight resolution:** prove h(n) = n^{1+o(1)} (matching Tóth/Nivasch-style lower bounds), or Θ(n^{4/3}).
4. **General k:** determine whether f(n,k) = Θ(nk^{1/3}) or close the gap against the e^{Ω(√log k)} lower bounds for all k.

A referee accepts: a rigorous proof or explicit construction in the standard general-position model, with full constants or exponents, resolving one of the above.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/6623bf7e-d793-4a03-b069-afedbcf9d3c0?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000147.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000147)
