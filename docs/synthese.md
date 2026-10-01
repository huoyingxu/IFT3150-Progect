---
title: Synthèse
---

<style>
    @media screen and (min-width: 76em) {
        .md-sidebar--primary {
            display: none !important;
        }
    }
</style>


# Synthèse

This summary covers the work documented during the first four weeks of the project. It will be updated as development and evaluation progress. Weekly details are available in the [project log](suivi.md).

## 1. Études préliminaires

Initial discussions with the professor clarified the project objectives and development tools. Reference images provided examples of how circles, axes, symmetry, and tangency can form Gothic tracery.

The first approach used a JavaScript modeling language with code input to describe geometric elements. Extending it to circles arranged along multiple axes highlighted the importance of making dependencies explicit. More complex constructions, particularly nested circles, were expected to become difficult to manage through code input alone. This motivated the transition to visual control modules.

## 2. Réalisation

The work completed so far includes:

- A first JavaScript modeling language for defining basic geometric elements through code, such as `A = point(0, 0)` and `B = circle(A, 20, 4)`.
- Circle generation along multiple axes by applying the same positional calculation to each axis.
- A rebuilt interface using visual control modules and connections to expose dependencies between geometric elements.

The transition preserved the functionality developed in the initial prototype while making the relationships between modules easier to identify. The [week 4 screenshot](suivi.md#semaine-4-2127-septembre-2026) illustrates the connected modules and the resulting circle pattern.

## 3. Évaluation

## 4. Bilan
