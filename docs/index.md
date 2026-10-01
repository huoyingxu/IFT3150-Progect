---
title: Vue d'ensemble du projet
---

<style>
    @media screen and (min-width: 76em) {
        .md-sidebar--primary {
            display: none !important;
        }
    }
</style>

# Vue d'ensemble du projet

!!! info "Informations générales"
    **Session**: Fall 2026  
    **Auteur(s)**: Yingxu Huo  
    **Thème(s)**: Parametric Gothic Tracery Design   
    **Superviseur(s)**: Jing Ren   
    **Collaborateur(s):** None   
 
## Description du projet

This project aims to design a parametric modeling language for generating Gothic tracery from 2D outlines and symmetry constraints. The goal is to represent the geometric principles underlying these designs so that they can be reproduced, modified, and eventually used to synthesize new patterns.

### Contexte

Gothic tracery consists of networks of curves that structure and decorate windows and rose windows. Their visual diversity is underpinned by geometric constructions based on circles, arcs, axes, and symmetry or tangency relationships. Computational modeling makes it possible to explore these construction rules and produce parametric variations.

This project falls within geometric modeling and computer-aided design. It draws on historical tracery examples and an explicit representation of the relationships between design elements.

### Problématique

Reproducing a pattern's outline is not enough to describe how it is constructed. When a circle's radius, center, or symmetry order changes, dependent elements must be recalculated to preserve the intended geometric relationships. A description based solely on independent positions and dimensions makes these changes difficult to manage.

The central question is therefore: **how can Gothic tracery be represented and edited while preserving its geometric dependencies and symmetry and tangency constraints?** 

### Proposition et objectifs

The proposed solution is a parametric modeling language accompanied by a visual editor. A construction is represented as a directed graph: nodes describe geometric elements or construction operations, and connections express their dependencies. A preview shows how parameter changes affect the design.

The project has the following objectives:

1. **Define a structured representation** of points, symmetry axes, circles, and groups of circles, with clearly identified inputs and parameters.
2. **Implement essential geometric constructions**, including the generation of circles tangent to one another and to their enclosing circle, and the reuse of a resulting circle in a nested construction.
3. **Support interactive graph editing**, parameter changes, and updates to dependent elements in the geometric preview.
4. **Evaluate the representation using a documented set of examples**, examining construction fidelity, constraint preservation, and encountered limitations.

The main scope is two-dimensional construction. Selecting the arcs needed for the final tracery remains an area to explore. Additional decoration, extension to 3D, and automatic pattern synthesis are directions for future work.

### Méthodologie

The project follows three main steps:

1. Study reference patterns to identify their geometric rules.
2. Develop a node-based modeling tool with an interactive preview.
3. Test simple and nested constructions, then refine the tool through regular feedback from the supervisor.

### Validation et évaluation

The tool will be evaluated by:

- Reproducing reference patterns and checking their symmetry and tangency.
- Changing parameters to verify that dependent shapes update correctly.
- Testing node editing and invalid inputs to check usability and error handling.

Results and limitations will be documented in the [project summary](synthese.md).

## Échéancier

!!! info
    Le suivi complet est disponible dans la page [Suivi de projet](suivi.md).

| Week | Dates (2026) | Summary |
| --- | --- | --- |
| 1 | August 31–September 6 | Met with the professor to confirm the project objectives and development tools. |
| 2 | September 7–13 | Built the first JavaScript modeling language using code input to create basic geometric elements. |
| 3 | September 14–20 | Implemented circle generation along multiple axes. Identified difficulties with complex dependencies and decided to switch to visual control modules. |
| 4 | September 21–27 | Rebuilt the existing functionality as visual control modules with connections that make dependencies easier to identify. |
| 5 | September 28–October 4 | Progress has not yet been documented in the project log. |
