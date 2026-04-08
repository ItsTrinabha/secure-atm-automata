# ATM Automata

An interactive Theory of Computation project that models a secure ATM transaction system using automata theory, formal language concepts, and modern UI design.

This project starts with a deterministic ATM workflow and extends it with security controls, formal analysis, and multiple computation models including DFA, NFA, epsilon-NFA, NFA-to-DFA conversion, DFA minimization, Regular Expressions, Context-Free Grammar, Pushdown Automata, and a basic Turing Machine simulation.

## Project Overview

Automated Teller Machines work through a strict sequence of actions:

1. Card insertion
2. PIN verification
3. Operation selection
4. Withdrawal processing
5. Exit / return to idle

This project represents that workflow as a formal automaton and then expands it to show how Theory of Computation concepts apply to a real-world system.

The project includes:

- A polished HTML/CSS/JavaScript interactive simulator
- A standalone TOC explanation page
- Security extensions such as lock state, timeout recovery, and logging
- Academic extensions for viva, presentation, and report support

## Main Features

- DFA-based ATM workflow simulation
- Lock state after 3 incorrect PIN attempts
- Trap state for invalid input sequences
- Timeout recovery back to `q0`
- Dead-state detection
- Transition logging with timestamps
- Transition matrix display
- Live automata graph / state flow visualization
- NFA and epsilon-NFA explanation
- NFA-to-DFA conversion
- DFA minimization using partition refinement
- Regular Expression validation
- Context-Free Grammar representation
- PDA stack simulation
- Turing Machine tape simulation
- Hardware architecture explanation for ATM implementation
- Improved UI/UX for project presentation and GitHub showcase

## Theory of Computation Concepts Used

### 1. Deterministic Finite Automaton (DFA)

The core ATM simulator is modeled as a DFA.

Example flow:

```text
q0 --card--> q1
q1 --pin(correct)--> q2
q2 --op--> q3
q3 --withdraw--> q4
# ATM Automata

An interactive Theory of Computation project that models a secure ATM workflow and explains it through DFA/NFA concepts, language theory, stack-based memory, and tape-based computation.

The main build is `final2.html`.

## Current UI Layout (`final2.html`)

Tabs are currently ordered as:

1. Phase 1: DFA
2. Phase 2: Regex & CFG
3. Phase 3: PDA Memory
4. Phase 4: TM & Decidability
5. Process Guide
6. Hardware

## Core Features

- Phase 1 DFA ATM emulator with visual state transitions
- Security model with `q_lock` (3 wrong PIN attempts) and `q_dead` trap behavior
- Session timeout reset to `q0`
- Live transition log with timestamps
- Transition matrix and live state graph (`vis-network`)
- Dead-state reachability check
- NFA and epsilon-NFA explanations in the formal analysis layer
- NFA-to-DFA conversion output
- DFA minimization output (partition refinement)
- Phase 2 regex membership checker and CFG derivation view
- Phase 3 PDA stack push/pop simulator with instantaneous description
- Phase 4 Turing-style tape simulation for balance/request decidability
- Process Guide section for demo/viva flow
- Hardware section for ATM architecture context

## Formal Model Summary

The ATM language is modeled with states:

```text
Q = {q0, q1, q2, q3, q4, q_lock, q_dead}
Sigma = {card, pin, op, withdraw, exit}
```

Typical valid transaction path:

```text
q0 --card--> q1
q1 --pin(correct)--> q2
q2 --op--> q3
q3 --withdraw--> q4
q4 --exit--> q0
```

Sample non-deterministic interpretation:

```text
q1 --pin--> {q2, q1, q_lock, q_dead}
```

Phase 2 grammar form shown in the UI:

```text
S -> card A
A -> pin B
B -> withdraw C | balance C
C -> exit
```

## Security Behavior

- Wrong PIN x3 transitions to `q_lock`
- Invalid protocol sequence transitions to `q_dead`
- Inactivity timeout resets session back to `q0`
- Hardware reset recovers the machine to initial state

## Project Structure

```text
TOCPROJECT/
├── final1.html
├── final2.html
├── index.html
├── toc-explanation.html
└── README.md
```

## File Notes

### `final2.html`

Primary and latest integrated simulator UI.

### `index.html`

Alternate project UI version with similar phase coverage.

### `final1.html`

Earlier iteration of the simulator.

### `toc-explanation.html`

Standalone explanatory companion page for TOC-focused writeups and viva support.

## How To Run

Open directly in a browser:

- `final2.html` (recommended main experience)
- `toc-explanation.html` (theory explanation page)

## Recommended Demo Flow

1. Start in Phase 1 and run a valid transaction (`q0` to `q4` to `q0`)
2. Show one invalid sequence leading to `q_dead`
3. Show 3 wrong PIN attempts leading to `q_lock`
4. Show timeout and hardware reset behavior
5. Move to Phase 2 for regex + CFG membership/derivation
6. Move to Phase 3 for PDA stack operations
7. Move to Phase 4 for TM tape-based decision output
8. End with Process Guide and Hardware tabs for presentation context

## Tech Stack

- HTML
- CSS
- JavaScript
- `vis-network`
This means:
