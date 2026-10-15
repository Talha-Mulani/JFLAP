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
