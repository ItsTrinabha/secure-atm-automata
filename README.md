# ATM Automata

> A complete Theory of Computation project that models a secure ATM transaction system through formal automata, language theory, and interactive visualization.

---

## 📌 Project Summary

This project demonstrates how an ATM session can be designed as a formal computational model. It starts with a deterministic ATM workflow and extends it into academic TOC concepts such as:

- Deterministic Finite Automaton (DFA)
- Non-Deterministic Finite Automaton (NFA)
- Epsilon-NFA
- NFA-to-DFA conversion
- DFA minimization
- Regular Expression modeling
- Context-Free Grammar (CFG)
- Pushdown Automaton (PDA)
- Turing Machine simulation

The purpose is to connect real-world ATM behavior to Theory of Computation concepts, making the system both practical and pedagogical.

---

## 🚀 What the Project Delivers

- Interactive HTML/CSS/JavaScript ATM simulator
- Clean UI with formal state flow visualization
- Security behavior for PIN retries and lock states
- Formal language modeling for accepted and rejected sequences
- Structured explanation pages for academic submission
- Ready-to-present content for viva, seminar, and report evaluation

---

## ⭐ Key Features

- **DFA-based ATM workflow** with defined states and transitions
- **Invalid input rejection** through trap state handling
- **Lock state** after 3 incorrect PIN attempts
- **Timeout and reset flow** that returns the machine to idle
- **Transition logs** and state history tracking
- **Graphical state visualization** for better understanding
- **NFA / ε-NFA conceptual support** for nondeterministic behavior
- **NFA to DFA conversion** to show subset construction
- **DFA minimization** to illustrate state reduction
- **Regular Expression** representation of the valid ATM transaction language
- **CFG representation** to map ATM workflow rules
- **PDA simulation** with stack behavior for session control
- **Turing Machine tape simulation** for advanced computation modeling

---

## 📚 Theory of Computation Concepts Used

### 1. Deterministic Finite Automaton (DFA)

The ATM model is primarily designed as a DFA. Each input symbol triggers one unique next state, making the workflow deterministic and predictable.

Formal description:

- `Q = {q0, q1, q2, q3, q4, q_lock, q_dead}`
- `Σ = {card, pin, op, withdraw, exit}`
- `q0` = initial state
- `F = {q0}` after successful completion
- `δ` = transition function

Example valid flow:

```text
q0 --card--> q1
q1 --pin(correct)--> q2
q2 --op--> q3
q3 --withdraw--> q4
q4 --exit--> q0
```

### 2. Trap State and Rejection

Invalid or out-of-order actions move the machine to a trap state (`q_dead`). Once in `q_dead`, the system requires reset, demonstrating formal rejection behavior.

### 3. Lock State

Security is modeled by a finite-state lock behavior:

- 3 wrong PIN entries → `q_lock`
- accepts only reset or authorized recovery inputs
- simulates real ATM lockout policy using automaton states

### 4. Non-Deterministic Finite Automaton (NFA)

The NFA model shows how one input can lead to many possible next states, which is useful for conceptualizing alternate outcomes, retries, and branching failures.

### 5. Epsilon-NFA

Epsilon transitions represent internal state changes that do not consume user-visible input. This helps explain hidden state movement and internal state preparation.

### 6. NFA to DFA Conversion

The project includes subset construction examples showing how nondeterministic state sets become deterministic DFA states.

### 7. DFA Minimization

Minimization is used to demonstrate how equivalent states can be merged while preserving accepted language behavior.

### 8. Regular Expressions

The valid ATM transaction sequence is represented as a regular expression.

Example:

```text
(card)(pin)(op)(withdraw)(exit)
```

### 9. Context-Free Grammar (CFG)

The ATM workflow is also described using production rules.

Example:

```text
S -> card A
A -> pin B
B -> op C
C -> withdraw D
D -> exit
```

### 10. Pushdown Automaton (PDA)

A PDA is included to simulate stack-based session memory, demonstrating how pushdown automata can model nested or sequential session operations.

### 11. Turing Machine

A simple tape-based Turing Machine simulation illustrates the general computation model beyond finite automata.

---

## 📁 Project Structure

- `ATM.html` — Main ATM simulator and interface
- `index.html` — Home or landing page for the project
- `toc-explanation.html` — Theory of Computation explanation page
- `final1.html` — Final project submission page or report view
- `rejected.html` — Invalid/failed transaction demonstration page

---

## ✅ How to Use

1. Open `ATM.html` in a web browser.
2. Follow the transaction flow by selecting:
   - `Card`
   - `PIN`
   - `Operation`
   - `Withdraw`
   - `Exit`
3. Explore invalid inputs and observe trap-state behavior.
4. Review the explanation page in `toc-explanation.html` for academic details.

---

## 🎯 Learning Outcomes

After using this project, a reader should be able to:

- Explain how a real ATM workflow maps to a DFA
- Distinguish between DFA, NFA, and ε-NFA behaviors
- Convert an NFA into an equivalent DFA
- Minimize a DFA using partition refinement
- Express an ATM sequence using regular expressions and CFG
- Understand how finite state machines can model security features
- Relate PDA and Turing Machine concepts to practical computation modeling

---

## 💡 Submission Notes

This repository is designed for academic submission. It combines:

- formal Theory of Computation modeling,
- interactive simulation,
- clear documentation,
- and submission-ready explanation structure.

Use the HTML pages and visual simulation as evidence of both theoretical understanding and practical implementation quality.

---

## 📞 Contact / Author

Prepared as a semester project in Theory of Computation.

For further explanation, refer to `toc-explanation.html` and the source HTML files.

After three incorrect PIN attempts, the machine moves to `q_lock`.

This shows that TOC can model practical security rules, not only theoretical transitions. Even though this is a real ATM-inspired behavior, it is still expressed using finite-state logic.

So the lock policy is not just described in words. It is formally represented as a state transition.

### Dead State Detection

Another TOC-based analysis used in the project is dead-state detection.

A state is considered dead if it cannot reach a final or acceptable state. In this project, the system checks which states cannot return to `q0`.

This demonstrates:

- reachability analysis
- formal validation of state behavior
- correctness checking of rejection and recovery paths

This is important because it shows the project is not only simulating the machine, but also analyzing it mathematically.

### NFA for Branching Possibilities

The project also explains the ATM using a Non-Deterministic Finite Automaton.

In an NFA, one input can conceptually lead to multiple possible next states.

Example:

```text
q1 --pin--> {q2, q1, q_lock, q_dead}
q2 --op--> {q3, q_dead}
```

This is useful because ATM behavior contains branching outcomes such as:

- correct PIN
- retry after wrong PIN
- account lock
- complete rejection

The NFA view shows how one symbol can represent multiple theoretical possibilities.

### Epsilon-NFA for Internal Movement

The project includes epsilon transitions to explain movement without consuming a visible user input.

Example:

```text
q1 --ε--> q2
```

This is used to explain internal ATM preparation steps where the machine may move logically without the user explicitly entering another symbol.

This connects system behavior with epsilon-NFA theory in a simple and intuitive way.

### NFA to DFA Conversion

The project demonstrates subset construction to convert the NFA into a DFA.

This is a major TOC concept because it proves that non-deterministic behavior can be transformed into deterministic behavior while preserving the same language.

Examples of composite DFA states:

```text
{q1, q2}
{q1, q_lock}
{q2, q_dead}
```

This is academically valuable because it shows equivalence between models rather than only presenting them separately.

### DFA Minimization

The project also includes DFA minimization using partition refinement.

This shows how automata can be optimized after construction.

Minimization is useful for explaining:

- reduced state complexity
- formal optimization
- efficient implementation

It also shows that the project goes beyond modeling into formal analysis and optimization.

### Regular Expression

The accepted ATM transaction language is also expressed as a regular expression:

```text
(card)(pin)(op)(withdraw)(exit)
```

This demonstrates a key TOC idea:

- regular languages can be described by finite automata
- the same regular languages can also be described by regular expressions

So the project connects automata theory with another equivalent formal representation.

### Context-Free Grammar

The same ATM language is represented through production rules:

```text
S -> card A
A -> pin B
B -> op C
C -> withdraw D
D -> exit
```

Even though the ATM workflow is regular, showing it as a CFG helps explain the language from a derivation perspective.

This means the project shows both:

- recognition by automata
- generation by grammar

### PDA for Stack-Based Memory

Pushdown Automata are used to show what happens when memory is added to computation.

In the project, stack operations are used to model session-like memory, such as:

- card inserted
- PIN processed
- exit removing stack context

This extends the project beyond finite-state behavior and helps explain how TOC models become stronger when memory is introduced.

### Turing Machine for General Computation

The project also includes a simple Turing Machine representation.

The ATM symbols are placed on a tape, and a head reads one symbol at a time and moves right.

This is useful because it shows the same workflow under the most general classical model of computation.

It is not necessary for ATM implementation, but it strengthens the academic depth of the project.

### Formal Verification Mindset

Overall, TOC is used in this project in a complete formal way:

- to define the legal ATM language
- to reject invalid strings
- to model security behavior
- to analyze reachability and dead states
- to convert NFA to DFA
- to minimize DFA
- to represent the same language using regex and grammar
- to extend the model with memory and tape-based computation

So the project is not just “inspired by” Theory of Computation.

It is actually built around TOC principles at the modeling, verification, and explanation levels.

## Security Extensions

The project is not limited to theoretical state transitions. It also models realistic ATM-style security behavior.

### Lock State

After 3 incorrect PIN attempts:

```text
q1 -> q_lock
```

### Trap State

Any protocol violation or invalid sequence sends the machine to:

```text
q_dead
```

### Timeout Recovery

If no input is received within a fixed time window, the machine resets safely to:

```text
q0
```

### Logging

The simulator keeps timestamped logs of:

- transitions
- authentication failures
- timeout events
- resets
- security violations

## Project Structure

```text
TOCPROJECT/
├── final1.html
├── final2.html
├── toc-explanation.html
└── README.md
```

## Files Description

### `final1.html`

An earlier HTML version of the ATM automata simulator. It contains the basic DFA-oriented project structure and interactive ATM logic.

### `final2.html`

The main and most complete version of the project.

It includes:

- upgraded UI/UX
- DFA, NFA, epsilon-NFA
- lock state
- timeout
- logging
- minimization
- regex, CFG, PDA, and TM sections

### `toc-explanation.html`

A standalone explanation page for Theory of Computation usage in the project. It is useful for:

- viva
- oral presentation
- GitHub readers
- project explanation outside the simulator

## How to Run

## Option 1: HTML Version

Open these files directly in a browser:

- `final2.html` for the main project
- `toc-explanation.html` for the theory explanation

If you want the full project experience, start with `final2.html`.

## Recommended Demo Flow

If you are presenting this project in class or viva, this order works well:

1. Show the DFA ATM flow from `q0` to `q4`
2. Explain `q_dead` as a trap state
3. Enter wrong PINs and show `q_lock`
4. Show timeout recovery
5. Open the NFA / epsilon-NFA section
6. Show NFA-to-DFA conversion
7. Show DFA minimization
8. Explain regex and CFG
9. Demonstrate PDA stack and Turing Machine tape
10. Open `toc-explanation.html` for final theoretical summary

## Use Cases

This project is useful for:

- Theory of Computation coursework
- automata lab/project submission
- viva explanation
- educational demonstration of formal models
- showing how theoretical CS applies to real systems

## Why This Project Is Strong

This project is strong because it does not stop at only one model.

It connects:

- formal language theory
- state machine design
- security behavior
- system workflow validation
- UI-based educational presentation
- web-based implementation

It is both:

- academically meaningful
- visually presentable

## Technologies Used

### Web Version

- HTML
- CSS
- JavaScript
- `vis-network` for graph visualization

## Suggested GitHub Topics / Tags

- theory-of-computation
- automata
- finite-automata
- dfa
- nfa
- epsilon-nfa
- nfa-to-dfa
- dfa-minimization
- formal-languages
- atm-simulator
- regex
- context-free-grammar
- pushdown-automata
- turing-machine
- html
- css
- javascript
- visualization
- education
- computer-science

## Future Improvements

Possible future extensions:

- Arduino code for embedded ATM-state validation
- network-based ATM request simulation
- cryptographic authentication explanation
- downloadable project report PDF
- deployment to GitHub Pages

## Author Info

Course context:

- Theory of Computation
- ATM workflow modeled using formal automata

Project by:

- Bhargav Mahanta
- Trinabha Dixit

## License

This project can be used for educational and academic demonstration purposes.
