# Better Code, Better Science — Book Summary

> Book by Russell Poldrack. Available at: https://bettercodebetterscience.github.io/book/

---

## Introduction
- Coding is now ubiquitous in science, but most researchers lack formal software engineering training
- Code errors can have catastrophic consequences (e.g., retracted papers due to sign-flip bugs)
- Reproducibility is a major challenge even when code and data are shared
- AI tools require close human oversight — they cannot independently solve complex scientific problems
- Strategies like pre-registration and data splitting help prevent researcher bias in code

## Essential Tools and Techniques
- Git version control acts as a digital lab notebook — commit messages should explain *why*, not just *what*
- Virtual environments (uv, Conda) isolate dependencies and are essential for reproducibility
- GitHub workflows (branches, pull requests, code reviews) enable collaborative development
- LLMs use transformer architecture and in-context learning — understanding this helps use them effectively

## Principles of Software Engineering
- Build minimum viable products iteratively (Agile/MVP), avoid premature "gold plating"
- Code is read far more often than written — clarity and naming conventions matter enormously
- Modularity and Single Responsibility principle keep components maintainable
- Use assertions and exceptions loudly; never fail silently
- Code reviews and structured logging (not print statements) are essential practices

## Software Testing
- Tests define expected behavior and catch regressions when code changes
- Unit, integration, and smoke tests each serve distinct purposes:
  - **Unit tests**: test a single function or component in isolation, with no external dependencies — fast and precise
  - **Integration tests**: test how multiple components work together (e.g., code + database + file system) — slower but catch interface bugs
  - **Smoke tests**: quick, minimal checks that the system starts and runs at all, before running a full test suite
- Test-driven development and bug-driven testing embed quality into the workflow
- pytest fixtures, mocking, and parametrized tests make testing efficient
- Separate unit from integration tests and run in parallel to keep test suites fast

## Coding with AI
- AI-generated code *must* be verified through unit tests — it can look correct while being wrong
- Context management (constitution files, memory files, scratchpads) improves agentic AI performance
- Human judgment is irreplaceable for architecture, problem decomposition, and recognizing dead ends
- Scientists bear special responsibility to verify AI-generated code before publishing results

## Project Structure and Management
- Consistent folder hierarchies with separated concerns (code vs. data) reduce long-term friction
- Jupyter notebooks are good for exploration, but reusable logic should be extracted into modules
- Docker containers are the most robust way to share reproducible computational environments
- Document at multiple levels: self-explanatory code → docstrings → API references (Sphinx/MkDocs)
- Use `jupytext` and pre-commit hooks to manage notebooks cleanly in git

## Data Organization and Management
- Follow FAIR principles: data should be Findable, Accessible, Interoperable, Reusable
- Storage choices (file systems, object storage, databases) depend on size, access patterns, and cost
- Metadata, codebooks, and provenance tracking enable others to understand and reuse datasets
- DataLad manages large datasets similarly to git, with audit trails for derived datasets
- Plan data management from project inception — early decisions prevent costly problems later

## Workflow Management
- Good workflows are correct, usable, maintainable, and efficient
- Start with GNU Make; scale to Snakemake (DAG-based) for complex parallel analyses
- Checkpoint intermediate results for resumability; design operations to be idempotent
- An "80/20" approach to FAIR (version control, standard formats, clear config) gives most of the benefit
- AI can generate test suites quickly, but human review is needed to catch missing edge cases

## Validating Scientific Software
- Simulations with known parameters allow validation against "ground truth"
- Closed-form, Bayesian, optimization, and simulation-based inference suit different scenarios
- Uncertainty quantification (confidence/credible intervals, bootstrap) is non-negotiable
- Negative and positive control experiments verify method performance
- Sensitivity and multiverse analyses expose whether results depend on specific analytical choices

## Optimizing Performance
- Always profile first — never optimize before identifying actual bottlenecks
- Algorithmic complexity (O(N) vs O(N²)) matters far more than hardware speed
- Vectorized operations (NumPy, pandas) and built-in data structures outperform hand-written loops
- Parallelize only for embarrassingly parallel problems; be aware of overhead and memory constraints
- GPU acceleration excels for mathematically-intensive tasks like neural network training

## High-Performance Computing
- HPC clusters are managed by sysadmins and offer scalability, power management, and security
- Slurm schedules batch jobs — never run intensive work on login nodes
- HPC storage has a hierarchy: home dirs (persistent), scratch (fast/temporary), long-term storage
- Job arrays enable thousands of parametric runs (e.g., multiverse analyses) with load throttling
- Use modules, virtual environments, or Apptainer containers for software access on HPC

## Sharing Research Objects
- Use DOIs, ORCIDs, and persistent identifiers to prevent link rot and ensure citability
- License everything explicitly: MIT for code, CC0/CC-BY for data — unlicensed work creates legal uncertainty
- Deposit code via GitHub–Zenodo integration; use domain-specific repositories for data
- Include `CITATION.cff`, `codemeta.json`, semantic versioning, and lock files for reproducibility
- Share container images to allow others to reproduce the full computational environment
