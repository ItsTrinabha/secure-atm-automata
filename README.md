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
q4 --exit--> q0
```

### 2. Non-Deterministic Finite Automaton (NFA)

NFA is used to explain branching behavior such as:

- correct PIN
- retry
- lock
- rejection

Example:

```text
q1 --pin--> {q2, q1, q_lock, q_dead}
q2 --op--> {q3, q_dead}
```

### 3. Epsilon-NFA

Epsilon transitions are used to explain internal state movement without consuming visible input.

```text
q1 --ε--> q2
```

### 4. NFA to DFA Conversion

Subset construction is demonstrated to convert non-deterministic state sets into deterministic composite states.

Examples:

```text
{q1, q2}
{q1, q_lock}
{q2, q_dead}
```

### 5. DFA Minimization

Partition refinement is used to analyze whether DFA states can be merged while preserving behavior.

This helps explain:

- formal optimization
- reduced state complexity
- implementation efficiency

### 6. Regular Expression

The legal ATM transaction string is represented as:

```text
(card)(pin)(op)(withdraw)(exit)
```

### 7. Context-Free Grammar (CFG)

The same workflow is also represented as production rules:

```text
S -> card A
A -> pin B
B -> op C
C -> withdraw D
D -> exit
```

### 8. Pushdown Automata (PDA)

PDA is used to simulate stack memory for session events such as card and PIN handling.

### 9. Turing Machine

A simple tape-based representation is included to show a more general model of computation.

## How Theory of Computation Is Used In This Project

This project does not use Theory of Computation only as background theory. TOC is used as the actual design logic behind the ATM system.

Instead of treating the ATM as a normal UI with buttons, the project treats it as a formal machine that changes state only when a valid symbol is received. That means the ATM is modeled as a language-recognition system where:

- states represent stages of the ATM session
- inputs represent valid ATM actions
- transitions define what the machine is allowed to do next
- invalid strings are rejected formally

So the project is built around formal computation models, not just around interface behavior.

### DFA as the Core ATM Model

The main workflow is designed as a Deterministic Finite Automaton.

That means:

- every valid input from a valid state leads to one exact next state
- the ATM behaves in a predictable and controlled way
- valid user behavior follows one legal transaction path

Formal interpretation:

- `Q = {q0, q1, q2, q3, q4, q_lock, q_dead}`
- `Σ = {card, pin, op, withdraw, exit}`
- `q0` is the initial state
- `δ` is the transition function
- the machine returns to `q0` after a successful session

Example valid DFA flow:

```text
q0 --card--> q1
q1 --pin(correct)--> q2
q2 --op--> q3
q3 --withdraw--> q4
q4 --exit--> q0
```

This is the formal language the ATM accepts.

### Rejection Through Trap State

TOC is also used to define rejection behavior.

If a wrong symbol is entered at the wrong time, the input string should not be accepted. For that reason, the project includes:

- `q_dead` as a trap state

This means:

- invalid sequences are formally rejected
- once the machine enters `q_dead`, it cannot continue normal computation
- the system requires reset or recovery logic

This is a direct application of finite automata rejection behavior.

### Lock State as Finite-State Security Logic

The project extends the formal DFA with a security-oriented state:

- `q_lock`

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
