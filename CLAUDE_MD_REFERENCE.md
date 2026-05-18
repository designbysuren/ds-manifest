# CLAUDE.md Reference
> This is a reference example showing what a CLAUDE.md looks like with design system rules added.
> Copy what is relevant into your own CLAUDE.md file in your project root.
> Do not publish this file as-is. Adapt it to your own project.

---

# CLAUDE.md

## Design System Rules
- Always read system.md before generating any UI component
- Always read DESIGN.md before using any token
- Never rebuild a component that exists in the component library
- Never hardcode color, spacing, typography, or radius values
- When in doubt between 2 components, pick the more specific one
- Never use raw HTML elements where a component exists

## Design System Files
- Token values and intent: DESIGN.md
- Component rules and usage: system.md
- When both conflict, system.md takes priority

## Component Rules
- Check system.md for the exact component name before writing any UI
- Use component names exactly as they appear in system.md
- Every interactive element needs an accessible label
- Every form input must be wrapped in FormField

## Token Rules
- Use token names from system.md, not raw hex or px values
- color/brand/primary is for primary actions only
- Never use feedback tokens for decorative purposes
- Always check the Do Not Use column before applying any token

## State Rules
Before generating any component confirm these states are handled:
- Default
- Hover
- Focus (keyboard navigable)
- Disabled
- Loading (if the component is async)
- Error (if the component is a form element)
- Empty (if the component is data-driven)

## Code Rules
- Use TypeScript
- Component names match system.md exactly
- Never use inline styles
- All spacing values use spacing tokens

## What to Do When Unsure
- Check system.md first
- If the component does not exist in system.md, flag it. Do not invent one.
- If the token use is ambiguous, use the most restrictive interpretation
- If a state is not covered in the design, flag it before generating
