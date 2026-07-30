# Prep notes: Essence of Linear Algebra, videos 1-4

Read this before tonight's videos. It won't give away the "aha" moments 3B1B builds toward,
but it primes the vocabulary so you're not decoding terms and intuition at the same time.

Free supplement (interactive, not video): **Immersive Linear Algebra** — https://immersivemath.com/ila/
Matches chapters 1-2 of this list almost exactly (vectors, dot product, Gaussian elimination, matrices).

---

## Video 1: Vectors

**Core idea:** a vector is not "a list of numbers." That's a *representation*. The vector itself
is an arrow from the origin — its identity is direction + length, full stop. The list of numbers
(coordinates) is just a translation of that arrow into a specific coordinate system.

Three ways people define "vector," all correct, all limited on their own:
- Physics student: an arrow in space (direction + magnitude), can start anywhere.
- CS student: an ordered list of numbers (an array). Convenient, but not the *meaning*.
- Math student: anything that can be added to another vector and scaled — the abstract definition.

**What to watch for:** how 3B1B roots every vector at the origin, and why that choice makes
addition and scaling geometric operations instead of arithmetic ones.

- **Vector addition** = tip-to-tail. Walk along vector A, then walk along vector B from where A
  ended. The sum is the arrow from the very start to the very end.
- **Scalar multiplication** = stretching/squishing/reversing a vector along its own line. Multiply
  by 2, arrow gets twice as long. Multiply by -1, arrow flips direction.

**Why it matters later:** every operation in linear algebra is built from these two moves
(add vectors, scale vectors) combined together. That combination has a name — coming in video 2.

---

## Video 2: Linear combinations, span, and basis vectors

**Core idea:** in 2D, we usually describe a vector using two special reference vectors:
**i-hat** (length 1, pointing along x) and **j-hat** (length 1, pointing along y). When you write
a vector as (3, -2), you actually mean: "3 copies of i-hat, plus -2 copies of j-hat, added
tip-to-tail." i-hat and j-hat are called **basis vectors**.

- **Linear combination** = any sum of scaled vectors: `a·v + b·w`. That's it — scale some vectors,
  add them up.
- **Span** = the set of *every possible* linear combination of a set of vectors. For two vectors
  that don't point along the same line, the span is the entire 2D plane. If they *do* point along
  the same line, the span is just that one line (they're "stuck" in 1D even though written with
  2 numbers).
- **Linearly dependent** = one vector in your set is already a combination of the others (adds no
  new reach — redundant). **Linearly independent** = each vector adds a genuinely new direction.
- **Basis** (formal definition) = a set of linearly independent vectors that span the full space
  you care about.

**What to watch for:** the moment 3B1B shows why 3 vectors in 2D are always linearly dependent —
that's the intuition that generalizes to n dimensions later.

---

## Video 3: Linear transformations and matrices

**Core idea:** a matrix is not "a grid of numbers to memorize rules for." A matrix is a
**recipe for moving space around** — a function that takes every vector in the plane and moves
it somewhere else, while keeping grid lines parallel and evenly spaced, and keeping the origin
fixed. That restriction (parallel + evenly-spaced grid lines, origin unmoved) is the actual
definition of **"linear."**

**The key trick:** because a linear transformation preserves linear combinations, you only need
to know where it sends i-hat and where it sends j-hat. Every other vector's new position is
just that same linear combination, recomputed with the *new* i-hat and j-hat.

- The **columns of a matrix** = where the basis vectors land after the transformation.
  Column 1 = where i-hat lands. Column 2 = where j-hat lands.
- "Applying a matrix to a vector" = look up where the original basis vectors landed, then take
  the same linear combination of those new landing spots.

**What to watch for:** how a 2x2 matrix full of 4 numbers suddenly becomes readable as
"two arrows telling you where the grid's corners went." This reframe is the single most
useful thing in the whole series — everything after this builds on reading matrices this way.

---

## Video 4: Matrix multiplication as composition

**Core idea:** if matrix A represents one transformation (e.g., a rotation) and matrix B
represents another (e.g., a shear), then the matrix product `A·B` represents "do B first,
then do A" — applied as one single combined transformation. Multiplying matrices = composing
functions, read **right to left**.

- **Order matters.** `A·B ≠ B·A` in general — rotate-then-shear looks different from
  shear-then-rotate. This is the geometric reason matrix multiplication is non-commutative
  (not an arbitrary rule to memorize).
- **How to actually compute it:** track where i-hat and j-hat end up after applying B, then
  apply A to *those* landing spots. The result is a new matrix — the composed transformation.
- **Associativity** (`(AB)C = A(BC)`) makes sense geometrically: whether you first combine B-then-C
  into one transformation and apply A, or apply C, then combine A-with-B first — you get to the
  same final rearrangement of space either way.

**What to watch for:** the moment the abstract "row times column" computation rule gets
derived *from* the geometric composition idea, rather than handed to you as an algorithm.

---

## Journal prompts for tonight (use `journal/_template.md`)

After each video, write down:
1. The one sentence that made something click.
2. One thing you'd have gotten wrong if you'd only memorized the algebra rules.
