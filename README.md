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
