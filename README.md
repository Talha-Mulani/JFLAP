# JFLAP
A self-learning repository for Theory of Computation (TCS), documenting automata theory concepts, computational models, and practical experiments implemented using JFLAP. 

## Experiments

### DFA accepting strings that start with `a` and end with `b`

**File:** [`DFA-1.jff`](DFA-1.jff)

This deterministic finite automaton accepts strings over the alphabet
`{a, b}` whose first symbol is `a` and whose last symbol is `b`.

The automaton uses:

- An initial state that directs strings beginning with `b` to a rejecting
  path.
- A state that tracks strings beginning with `a`.
- A final state reached when the most recently read symbol is `b`.
- Transitions that continue tracking the first-symbol condition while
  updating whether the current final symbol is `a` or `b`.

Examples accepted include `ab`, `aab`, and `abb`. Examples rejected include
`a`, `ba`, and `bba`.

### DFA accepting strings containing the substring `bab`

**File:** [`DFA-2.jff`](DFA-2.jff)

This deterministic finite automaton accepts strings over `{a, b}` that
contain `bab` as a substring. Its states track the longest suffix of the
input that is also a prefix of `bab`:

- `q0`: no part of `bab` has been matched.
- `q1`: the latest symbol is `a`.
- `q2`: the latest relevant suffix is `b`.
- `q3`: the latest relevant suffix is `ba`.
- `q4`: `bab` has been found; all remaining input is accepted.

Examples accepted include `bab`, `abab`, and `babb`. Examples rejected include
the empty string, `bba`, and `aaaa`.

### NFA accepting strings that start with `0`

**File:** [`NFA-1.jff`](NFA-1.jff)

This nondeterministic finite automaton accepts binary strings whose first
symbol is `0`. The transition from the initial state to the accepting state
reads the required leading `0`; the accepting state then loops on both `0`
and `1`, allowing any remaining binary symbols.

Examples accepted include `0`, `01`, `0011`, and `01010`. Examples rejected
include the empty string, `1`, and `101`.

### NFA to DFA conversion using subset construction

**File:** [`NFA-to-DFA.jff`](NFA-to-DFA.jff)

This experiment demonstrates the NFA used as the starting point for a
conversion to a DFA over `{a, b}`. The NFA begins at `q0`, accepts in `q2`,
and is nondeterministic because `q0` has two transitions on `a`.

Using subset construction, the reachable DFA states are:

- `{q0}` (initial)
- `{q0, q1}`
- `{q2}` (accepting)
- `{q1, q2}` (accepting)
- `{}` (dead state)

Every subset containing `q2` is accepting. The empty subset is added to make
the resulting DFA complete, with self-loops on both input symbols.

### Moore machine changing every occurrence of `100` to `101`

**File:** [`Moore-Machine.jff`](Moore-Machine.jff)

This Moore machine scans a binary input and changes each occurrence of
`100` to `101`. Its states remember the relevant suffix of the input:

- `q0`: no partial `100` pattern is being matched.
- `q1`: the latest relevant symbol is `1`.
- `q2`: the latest relevant suffix is `10`.
- `q3`: `100` has been detected, and the output changes its final `0` to `1`.

The machine uses output labels `0` and `1` to produce the transformed binary
string while preserving all other input symbols.

### Epsilon-NFA for the regular expression `(01)*0*`

**File:** [`epsilon-NFA-to-DFA.jff`](epsilon-NFA-to-DFA.jff)

This epsilon-NFA uses ε-transitions to accept strings described by
`(01)*0*`. It can accept the empty string, repeated `01` pairs, and any
number of trailing zeros. Examples include `ε`, `0`, `01`, `010`, and
`0100`.
