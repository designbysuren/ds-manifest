# truth-layer.md

Defines which artifact layer holds authority for which kind of product decision.

Prevents "which version is correct" from becoming the wrong question.

---

## The 3 Layers

| Layer | Artifact | Preserves | Governs |

|---|---|---|---|

| Design intent | Figma | What the team deliberately chose before implementation | Visual and interaction decisions |

| Executable behavior | Storybook | What the component actually does across implemented states | Behavioral correctness and state coverage |

| Delivered reality | Production | What customers are experiencing after every business rule, permission model, experiment, and constraint has shaped the outcome | Whether the system is actually serving users |

---

## The Routing Rule

When drift surfaces between layers, ask which kind of truth the gap belongs to before filing a ticket.

- Visual or interaction gap: route to Figma

- Behavioral or state gap: route to Storybook

- Gap between system promise and user reality: route to production first, then propagate the correction upstream into Storybook and Figma

The direction of the fix matters as much as the fix itself.

---

## Healthy Adaptation vs Experience Drift

Not every divergence is a problem. The distinction that matters:

Healthy adaptation: production reveals something true that design never modeled. The insight flows back upstream. Figma and Storybook update to account for the new state. The system gets stronger.

Experience Drift: production changes. Design stays unchanged. Storybook stays unchanged. The layers keep moving apart. Nobody notices until the gap becomes expensive.

A production edge case that gets patched without flowing back upstream is not a solved problem. It is drift accumulating.

---

## What This Is Not

This is not a hierarchy where one layer wins.

It is an authority map. Each layer is correct for its own kind of decision.

Disagreements between layers are not failures. They are signals about which layer needs updating and in which direction.

---

## Relationship to Experience Drift and Living Product Systems

Experience Drift accumulates when layers diverge without anyone asking which layer should have triggered the update. The truth-layer convention makes that routing explicit before drift compounds.

Living Product Systems require continuous alignment across all 3 layers. A single source of truth cannot represent a product that keeps moving. Truth-layer routing is how alignment stays operational without requiring one artifact to carry authority it cannot sustain.

---

## Related conventions

- system.md — base layer and product layer inheritance rules

- CLAUDE_MD_REFERENCE.md — Claude context and design system intelligence

- FIGMA_GUIDE.md — Figma file structure and component documentation standards

---

See: [The Design File Is No Longer the Source of Truth](#) — Part 4 of the AI-Native Product Design Series
