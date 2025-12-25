# Structural Explainability: Identity Regimes

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Build Status](https://github.com/civic-interconnect/IdentityRegimes/actions/workflows/ci.yml/badge.svg)
[![Check Links](https://github.com/civic-interconnect/IdentityRegimes/actions/workflows/links.yml/badge.svg)](https://github.com/civic-interconnect/IdentityRegimes/actions/workflows/links.yml)

> Lean 4 formalization of the Identity Regimes Theorem:
> a structural necessity-and-sufficiency result for neutral accountability substrates.

## Overview

This repository formalizes a foundational result about accountability-oriented
ontological substrates designed to remain stable under persistent
interpretive disagreement.

The core result shows that, under neutrality and independence assumptions:

- At least six distinct identity-and-persistence regimes are required, and
- Six regimes suffice to satisfy the full set of accountability constraints.

The formalization is abstract:
it does not name concrete kinds (Actor, Event, etc.),
embed causal or normative semantics, or assume a specific ontology design.

## Main Result (Informal)

For substrates optimized for neutrality and stability:

- Any substrate satisfying the six structural accountability requirements must contain at least six distinct regimes.
- There exists a substrate with exactly six regimes that satisfies all requirements.

Together, these establish a tight lower bound.

## Lean Statement (Simplified)

The main result is packaged as necessity and sufficiency:

```lean
six_regimes_theorem :
  (∀ (satisfies : Regime -> Requirement -> Prop)
     (S : Substrate Regime),
     S.satisfiesAll satisfies -> S.card >= 6)
  ∧
  (∃ S : Substrate CanonicalRegime,
     S.card = 6 ∧ S.satisfiesAll canonicalSatisfies)
```

## Domain Scope

The formalization applies to ontological substrates optimized for:

- Stability under durable interpretive disagreement
- Accountability across legal, political, and analytic frameworks
- Neutrality, understood as exclusion of causal and normative execution
- Structural sufficiency

It does not apply to:

- Ontologies embedding causal or normative conclusions
- Systems relying on negotiated or consensus semantics
- Role-based or context-discriminated substrates
- Single-framework modeling environments

## Paper (In Progress)

Case, D. M. (2025). "Substrate Stability Under Persistent Disagreement: 
Structural Constraints for Neutral Ontologies."

## Verification

To typecheck all proofs and run the verification executable:

```bash
lake update
lake build
lake exe identityregimes
```

## Documentation

- [Paper to Lean Mapping](./docs/MAPPING.md)
- [Lean 4 Quick Reference](./docs/LEAN.md)

## Project Structure

| Item         | Value                                           |
| ------------ | ----------------------------------------------- |
| Project name | `IdentityRegimes`                               |
| Namespace    | `StructuralExplainability`                      |
| Library      | `StructuralExplainability`                      |
| Executable   | `identityregimes`                               |
| Main proof   | `StructuralExplainability/IdentityRegimes.lean` |

This formalization assumes the neutrality constraint established in
[Structural Explainability: Neutral Substrate](https://github.com/civic-interconnect/NeutralSubstrate), 
which proves that substrates stable under persistent disagreement
must be pre-causal and pre-normative.
This work derives additional structural constraints under that assumption.

## License

[MIT](./LICENSE)
