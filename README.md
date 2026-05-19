# ds-manifest

The file your design system was always missing.

A machine-readable component manifest for coding agents.

CLAUDE.md tells agents how to behave. DESIGN.md tells agents what your tokens are. Neither tells agents what your components are, when to use them, or when not to.

That is what system.md is for.

## The Problem

Agents do not fail loudly. They improvise quietly.

They read your tokens and rebuild components from scratch because nothing pointed to your library. They use color.brand.primary everywhere because you never wrote down when not to. They get the spacing almost right because "almost right" is what a missing rule produces.

Every wrong output is a missing sentence in your documentation.

## The 3 File Stack

| File | Job |
|------|-----|
| CLAUDE.md | How the agent behaves |
| DESIGN.md | What the tokens are and why |
| system.md | What the components are and how to use them |

DESIGN.md is Google's open-source format. Fork it here: [github.com/google/design-md](https://github.com/google/design-md)


3 files. Each doing a job the others cannot.

## What Is In This Repo

| File | Description |
|------|-------------|
| system.md | The main template. Fork this and replace with your own system. |
| CLAUDE_MD_REFERENCE.md | Example CLAUDE.md with design system rules added. |
| FIGMA_GUIDE.md | Step by step guide to annotate your Figma file for agents. |

## How to Use system.md

1. Fork or copy system.md

2. Replace the placeholder components with your own library

3. Fill in every entry honestly

Not just what the component is. Write the actual rule. "Do not use inside cards or modals." Not "use for primary actions."

4. Reference it in your CLAUDE.md

Add one line:

```
Always read system.md before generating any UI component.
```

5. Update it when your system changes

An outdated system.md is worse than no file. Treat it like code.

## The Figma Side

system.md works best when your Figma variables and Dev Mode notes match it.

**In Figma Variables:** Every variable has a description field. Fill it in. Use the "Use for / Do not use for" format from this file directly.

**In Dev Mode:** Add component annotations that answer 3 questions:

- What is this for?
- When should you use it?
- When should you not?

Write for zero context. Pretend the reader has never seen your system before. Because the agent has not.

See FIGMA_GUIDE.md for the full step by step walkthrough.

## Community Figma File

A ready-to-fork Figma file showing the full annotation pattern. Button and Card components, fully annotated. Tokens page with all variable description fields filled in.

Figma Community: [link coming soon]

## Built Alongside

"I Gave My Agent CLAUDE.md and DESIGN.md. It Ignored My Entire Component Library." by Suren — Suren Publication on Medium

[Medium article link coming soon]

## Contributing

Found a token category or component pattern missing from the template? Open a PR. Keep entries short. Write rules, not rationale.
