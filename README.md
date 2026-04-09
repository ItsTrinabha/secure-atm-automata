# ATM Automata

## 1. Title

**ATM Automata**

A Theory of Computation project that models an ATM transaction system using formal automata, language theory, and interactive visualization.

---

## 2. Team Members

- Trinabha Dixit
- Bhargav Mahanta

---

## 3. Aim

The aim of this project is to demonstrate how a real-world ATM workflow can be represented as a formal computational model. The project uses Theory of Computation concepts to:

- model the ATM session as a finite automaton,
- enforce security behavior like PIN validation and lockout,
- explain invalid transitions through rejection states,
- illustrate equivalent formal representations using regular expressions and context-free grammar,
- extend the same system with PDA and Turing Machine concepts.

---

## 4. Modules

This is a multi-module HTML project with the following components:

- `ATM.html` — Main interactive ATM simulator with DFA-based state transitions, security logic, and visualization.
- `toc-explanation.html` — Theory of Computation explanation page covering DFA, NFA, ε-NFA, regex, CFG, PDA, and TM concepts.
- `.gitignore` — Git ignore settings for the project.
- `README.md` — Project documentation and submission guide.

> Note: There is no `index.html`, `final1.html`, or `rejected.html` in the current folder structure, so the README reflects the actual available files.

### Related TOC Topics Used

This project uses the following Theory of Computation topics:

- Deterministic Finite Automaton (DFA)
- Non-Deterministic Finite Automaton (NFA)
- Epsilon-NFA
- NFA to DFA conversion
- DFA minimization
- Regular Expressions
- Context-Free Grammar (CFG)
- Pushdown Automaton (PDA)
- Turing Machine (TM)
- Language acceptance and rejection
- Trap/lock state modeling
- Timeout and recovery behavior

---

## 5. Highlights of the Project (Features)

- **DFA-based transaction flow** with defined ATM states and valid transitions.
- **PIN verification** with a secure check for the correct PIN value.
- **Lock state after 3 wrong PIN attempts** to simulate real ATM security.
- **Trap state (`q_dead`)** for invalid or out-of-order button presses.
- **Timeout recovery** that returns the system to the idle state after inactivity.
- **Transition logging** to capture each state change with timestamped messages.
- **Live state graph** visualization using `vis-network`.
- **Multi-phase interface** showing DFA, regex/CFG, PDA, and Turing Machine sections.
- **Theoretical summary page** for clear academic explanation.

---

## 6. Screenshots

The current repository does not include image files, but you can capture the following screens in your browser and add them later:

1. `ATM.html` main dashboard with ATM display and controls.
2. DFA state graph view.
3. Process guide / accepted transaction flow.
4. Theory explanation page in `toc-explanation.html`.

If screenshot images are added, include them like this:

```markdown
![ATM Simulator](screenshots/atm-dashboard.png)
![TOC Explanation](screenshots/toc-explanation.png)
```

---

## 7. Advantages and Benefits

- **Educational clarity**: Helps learners connect ATM workflows with formal automata concepts.
- **Practical security modeling**: Demonstrates lockout and rejection in a controlled simulator.
- **Multiple TOC representations**: Shows DFA, NFA, ε-NFA, regex, CFG, PDA, and TM within one project.
- **Interactive experience**: Provides immediate visual feedback for each action.
- **Presentation-ready**: Contains both simulation and explanation content for academic submission.
- **Simple setup**: Runs directly in a browser with no backend required.

---

## 8. Drawbacks and Future Improvements

### Drawbacks

- No dedicated image screenshot assets are currently included.
- The simulator is browser-only and does not have a backend or database.
- The current PIN logic is fixed to a single value and not extensible without code changes.
- The project contains only two HTML files, so there is limited separation between frontend modules.

### Future Improvements

- Add real screenshot files under a `screenshots/` folder.
- Add a `README` image preview and demo GIF for GitHub presentation.
- Add `index.html` as a landing page that links to the simulator and theory guide.
- Support configurable PIN values and multi-user session flow.
- Add a backend or server-based simulation for ATM request handling.
- Improve mobile responsiveness and UX for smaller screens.
- Add more formal analysis tools such as DFA equivalence and reachability reports.

---

## 9. Societal Measures and Usage

This ATM Automata project promotes safer and more understandable banking workflows by:

- modeling security awareness through lockout policy,
- emphasizing correct transaction order,
- demonstrating how invalid actions are rejected formally,
- teaching the importance of controlled user input and session management.

### Usage Scenarios

- Academic submission for Theory of Computation coursework.
- Classroom demonstration of automata concepts.
- Seminar presentation on formal models and secure workflow design.
- Self-study resource for students learning DFA, NFA, CFG, PDA, and TM.

---

## How to Run

1. Open `ATM.html` in a web browser.
2. Use the buttons to simulate ATM actions:
   - `Insert Card`
   - `Enter PIN`
   - `Choose Op`
   - `Withdraw`
   - `Cancel/Exit`
3. Open `toc-explanation.html` to review the Theory of Computation explanation.

---

## Author Info

Project by:

- Trinabha Dixit
- Bhargav Mahanta

This project is prepared for Theory of Computation coursework and a formal automata demonstration.

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
