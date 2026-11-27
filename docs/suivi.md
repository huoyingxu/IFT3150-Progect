---
title: Suivi du projet
---

<style>
    @media screen and (min-width: 76em) {
        .md-sidebar--primary {
            display: none !important;
        }
    }
</style>

# Suivi de projet

## Semaine 1 (31 août–6 septembre 2026)

### Objectifs de la période

- Clarify the main objectives of the project and the tools to be used during development.

### Travail réalisé

Met with the professor to confirm the project's main objectives and the tools to use throughout the project.

![Geometric circle constructions on the left and corresponding Gothic tracery patterns on the right.](assets/images/week-1-tracery-reference.png)

*Reference examples showing geometric constructions and their corresponding Gothic tracery patterns.*

---

## Semaine 2 (7–13 septembre 2026)

### Objectifs de la période

- Establish the basic framework of the modeling language.
- Generate simple geometric elements, including points, axes, and circles, and experiment with symmetry and rotation.

### Travail réalisé

Developed the first version of the modeling language using JavaScript. This version used code input as the main way to create and edit geometric constructions.

For example:

```javascript
A = point(0, 0)
B = circle(A, 20, 4)
```

Here, `A` is a point at the origin and serves as the center of circle `B`. The value `20` specifies the radius, while `4` specifies `nRosy`, the rotational symmetry order.

---

## Semaine 3 (14–20 septembre 2026)

### Objectifs de la période

- Extend the modeling language to generate more complex constructions.
- Generate a corresponding number of circles based on the number of axes.

### Travail réalisé

Implemented circle generation by calculating the positional relationship between a circle and an axis. Applying this calculation to each axis made it possible to determine and render all the corresponding circles.

### Difficultés rencontrées

Although this approach worked for the implemented construction, extending it to more complex structures, such as multiple levels of nested circles, was expected to make the calculations increasingly difficult to organize and manage. Code-based input also made it difficult to identify the dependencies within the current geometric construction.

### Décisions et ajustements

Decided to replace code-based input with visual control modules. This approach was intended to make existing shapes easier to update and dependencies between modules easier to identify.

---

## Semaine 4 (21–27 septembre 2026)

### Objectifs de la période

- Rebuild the implementation around visual control modules.
- Add connections between modules to represent their dependencies.

### Travail réalisé

Reimplemented the functionality developed during the previous weeks as visual control modules and added connections between them. The existing functionality remained available, while dependencies between modules became easier to identify.

![Visual control modules connected in a dependency graph, alongside the generated circle pattern.](assets/images/week-4-control-modules.png)

*Week 4 prototype: connected control modules on the left and the resulting geometry on the right.*

---

## Bilan de période (2 octobre–6 novembre 2026)

### Objectifs de la période

- Extend the visual prototype to construct rose-window patterns from reusable circles, arcs, tangency constraints, and rotational symmetry.
- Preserve construction dependencies when source parameters change.
- Make the node graph easier to understand and prepare an accessible prototype for the second project presentation.

### Travail réalisé

**Geometric construction.** Added self-tangent circle groups, gap circles, and circles defined by three tangency constraints. These operations allow simple circles and groups to serve as inputs to more complex constructions, rather than requiring every circle to be positioned manually.

**Arc construction and display.** Added arc construction, solid/dashed/hidden arc styles, and rotational arc groups. A single arc can be repeated around a reference center to build a symmetric pattern. Display controls make it possible to distinguish construction geometry from the portions intended to remain visible.

**Parametric dependencies.** Revised circle references to use a source node ID and member index. When a source parameter such as `nRosy` changes, dependent constructions retrieve the updated source circles and recompute their constraints. For example, a circle defined by tangency to members of a group can update when that group changes from three to four members, provided the referenced members and a valid selected solution still exist.

**Node graph structure.** Separated geometry nodes from function nodes. Geometry nodes describe circles, groups, and their properties; function nodes specify construction inputs and constraints. The graph now makes the sequence **Geometry → Function → Geometry** explicit, for example **Circle → Self tangent → Circle group**. Automatic graph layout improves the readability of the connections and makes reuse of a result by several operations easier to identify.

**Online prototype.** Published the geometric construction application on GitHub Pages by November 6, so it can be accessed without running a local server: [Graph Creater](https://huoyingxu.github.io/IFT3150/). The live application continues to evolve after this reporting period.

### Difficultés rencontrées et solutions

Two main difficulties guided the changes during this period:

- **Dependencies became invalid when `nRosy` changed.** Dependent constructions could disappear when the source group changed. Identifying source members by node ID and member index allowed valid references to be resolved against the updated geometry. This preserves the construction relationship, but does not guarantee a solution when a referenced member disappears or the constraints become incompatible.
- **Operations and results were mixed in the same node.** This made construction history and responsibilities difficult to read. Separating geometry and function nodes clarified inputs, outputs, and reuse, and made unexpected results easier to trace back to their construction steps.

### Résultat de la période

By the second presentation, the project had an online, node-based prototype capable of combining circles and arcs into reusable geometric constructions, updating dependent geometry, and displaying selected arc portions. The main achievement was a clearer construction model that supports parameter-driven variations of rose-window patterns.

### Prochaines étapes envisagées au 6 novembre

- Develop an interactive editor for selecting points, lines, and other geometric elements directly on the canvas to create custom constructions.
- Explore AI-assisted rendering that relates geometric frameworks to real rose-window images while preserving their underlying structure.

These were planned directions at the time of the second presentation, rather than completed features for this reporting period.

### Présentation de la deuxième mise en commun

[Download the second project presentation (PowerPoint)](assets/presentations/phase-2-november-2026.pptx)

---

## Bilan de période (7–27 novembre 2026)

### Objectifs de la période

- Implement the interactive canvas editor proposed during the second presentation.
- Reuse editing operations across symmetric groups and retain them when construction parameters change.
- Extend circle construction to configurable constraints and improve the workflow for selecting geometric inputs.

### Travail réalisé

**Direct canvas editing.** Added an editor for selecting circle centers and geometric intersections, connecting two selected points with a segment, and applying solid, dashed, or hidden styles. Lines can be extended in both directions to find additional intersections with existing geometry. These extensions are visible only in editor mode, while their construction intersections can be reused as inputs to subsequent operations.

**Arc construction and selection.** Added canvas picking for arc centers and endpoints, including points constructed in the editor. These inputs retain references to their source geometry so that they can be recomputed. Users can switch between alternative arc paths connecting the same endpoints, including paths containing intermediate intersections. A further command keeps the selected arc visible and hides the remaining portions of its circle, avoiding repeated manual hiding.

**Similar segments and parametric updates.** Added operations to hide corresponding segments and create corresponding connections across construction groups, with preview and undo support. Matching now takes the parent construction group into account. Connection endpoints are resolved from updated source geometry, and persistent editing rules are reevaluated when symmetry changes. This extends the earlier dependency handling to canvas edits and repeated connections, including the transition from `nRosy = 3` to `nRosy = 4`.

**Unified circle constraints.** Combined the earlier three-tangency tool and the center-on-circle construction into one configurable workflow. Users choose three constraint types, pick the corresponding geometry on the canvas, and select a valid candidate solution. Available types include tangency to a circle, passing through a point, center on a circle, center on a line, and fixed radius. Presets cover common combinations, such as three tangencies or center on circle + tangency + through point. Hover highlighting and guided picking make the selected inputs easier to identify.

**Rendering preview.** Added a toggle between the editable geometric framework and an engraved-style preview. This is a procedural 2D visualization; it is not a completed 3D model or AI-generated rendering.

### Difficultés rencontrées et solutions

- **Edits were lost or displaced after changing symmetry.** Connections and styles tied to previous geometry did not always follow the new construction. Resolving endpoints from live source references and retaining group-based editing rules improved their behavior when group membership changed.
- **Similar-segment matching selected the wrong arcs.** Matching needed to distinguish corresponding portions within their parent groups. Using construction context improved the consistency of repeated hiding and connection operations.
- **Editor points were unavailable to arc construction.** Construction intersections were integrated into the arc input workflow so that extended lines can contribute reusable points without remaining visible outside editor mode.
- **Selecting and hiding arc portions required too many steps.** Alternative-path selection and the command to keep only a selected arc reduced the need to edit every remaining segment individually.

### Résultat de la période

The prototype now supports direct geometric construction and editing on the canvas, reusable operations across symmetric groups, and a unified circle-constraint workflow. The third presentation illustrates these improvements with canvas screenshots and a comparison of the patterns for `nRosy = 3` and `nRosy = 4`.

Core behavior and regression checks supported these changes. Numerical robustness and cases where the construction topology changes still require broader validation; not every combination of constraints has a valid or unique solution.

### Prochaines étapes

- Save and reload complete projects, including construction dependencies and editing rules.
- Improve handling of degenerate constraints and stability of solution selection.
- Add a dedicated SVG export workflow for external modeling tools.
- Develop detailed three-dimensional ornament in Blender. The current engraved preview remains a 2D step toward this goal.

### Présentation de la troisième mise en commun

[Download the third project presentation (PowerPoint, 5 slides)](assets/presentations/phase-3-november-2026.pptx)
