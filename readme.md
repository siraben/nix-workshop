# Nix Workshop Outline
Nix workshop outline, intended for a CS and discrete math-literate
audience without prior experience with Nix.  Knowledge of other build
systems is useful but not required.  Each session should take around 1
hr with time for questions.

## 1. Introduction and motivation
### Motivation
- Development environments
- Building software with dependencies
- Upgrading components
- Installing different versions of software side by side
- Deploying software to other machines and distributions
- Keeping systems up to date, rollbacks
### Existing solutions
- Development environments
  - `virtualenv`, `cabal repl`, `docker`
- Building software with dependencies
  - `brew`, `apt`, `ports`, `npm`, `pip`
- Upgrading components
- Installing different versions of software side by side
- Deploying software to other machines and distributions
  - writing package definitions
- Keeping systems up to date, rollbacks
  - `apt`, rollbacks?

### What can Nix do?
Nix can do all of the above and more.  Elaborate on why I think Nix is
poised to revolutionize DevOps, how it already affects my computing at
home, work and school.

- TODO: add content from Dolstra's PhD thesis on Nix
### A Little Theory
- Refresher on binary relations, directed graphs, graph representation
  of relations, transitive reflexive closure of a relation
- Build time dependency: what is needed to build the software
  - e.g. `cmake`, `clang`, `gcc`, `autoconf`
- Runtime dependency: what is needed at runtime 
  - e.g. runtime libraries
- Transitive dependency: "2nd order" dependencies
- Connection between memory management in PLs and software deployment
  - See Dolstra's thesis
- Go through examples of some project READMEs and ask audience what
  the build time/runtime dependencies are, and guess at some
  transitive dependencies
- Topological sort and build plans (e.g. as used in `make`)
### Discussion questions
- [ ] Install Nix on your system (macOS, Linux, WSL).  Ask around for
      help if you have any questions.
- [ ] Look at one of your own projects.  What does it depend on?  How
      much work would it take to get it to build and run on someone
      else's machine?
- [ ] Bit rot: Did you ever work on a project only to revisit it later
      and find out that it no longer built, despite not touching the
      source code at all?  If so, what was the problem?

## 2. Using Nix
Prerequisite: Nix installed

### Nix CLI
- Installing, uninstalling, upgrading packages
- Generations
  - listing, rolling back
- Nix store
  - querying, closures, generating graphs with graphviz
- Nix shell
  - like `virtualenv`, but for anything in Nixpkgs (up to 60K+
    packages)
  - run software without installing it
  - shebangs and reproducible scripts, with examples
    - generate Vanderbilt CS course dependency graph with pygraphviz
    - Haskell palindrome program
- Channels
  - Updating channels
### Nix language
- https://nixos.org/guides/nix-pills/basics-of-language.html
- Nix is a lazy, purely functional language
  - Functional programming, currying, closures
- Nix repl, importing Nixpkgs and library fucntions
- Expressions, sets, builtin functions
- Recursion and recursive sets
- Interesting: show the PR that implements topological sort in Nix
### Discussion questions
- [ ] Look at one of your own projects. Can you enter a Nix shell that
      lets you build and run it?
- [ ] Implement the factorial function in Nix using `lib.fix`.  Extra:
      could you define it without `fix` (Hint: find the definition of
      `fix`).

## 3. Packaging with Nix
- Packages as functions, inputs and outputs
### Build larger and larger programs
- Shell script to print hello
- Hello world in C
- GNU Hello, Ed
- `nix build --check`
### Discussion questions
- [ ] https://github.com/siraben/nix-challenges


TODO: select from topics below
## Can't get enough of Nix?  Some topics to explore
### Technical
- Nix/Nixpkgs manual
- [Nix pills](https://nixos.org/guides/nix-pills/)
- [Eelco Dolstra's PhD Thesis](https://edolstra.github.io/pubs/phd-thesis.pdf)
- [Build systems à la
  Carte](https://dl.acm.org/doi/pdf/10.1145/3236774)

### Nix at work and home
- [Practical examples of Nix use](https://nix.dev)
  - Continuous integration with Nix
  - Generating GitHub Actions artifacts
- Manage user configuration with Nix: Home Manager
- Manage OS configuration with Nix: NixOS, nix-darwin
- Overrides and overlays
- Cross-compilation
- Build-time environment variables and flags
- Even more reproducibility: pinning Nixpkgs
- Niv
- Nix flakes

### Contributing
- Adding a package to Nixpkgs
- Adding a cross toolchain to Nixpkgs
- Reviewing PRs
- Community
  - IRC, Discourse, Reddit, Discord
