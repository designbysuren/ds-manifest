# system.md

Machine-readable component manifest for coding agents. Last updated: [DATE] | Maintained by: [TEAM]

## How to Use This File

Every entry answers 3 questions: what it is, when to use it, when not to. Keep entries short. Write rules, not rationale.

## Tokens

### Color

| Token | Value | Use | Do Not Use |
|-------|-------|-----|------------|
| color/brand/primary | #2563EB | Primary actions, active states | Hover states, backgrounds, borders, decorative elements |
| color/brand/secondary | #1E40AF | Secondary actions, supporting accents | Replace primary, use on text |
| color/neutral/subtle | #F5F5F5 | Non-interactive background surfaces | Text, borders, icons, interactive elements |
| color/neutral/default | #E5E5E5 | Dividers, inactive borders | Primary content areas |
| color/neutral/strong | #171717 | Primary text, headings | Light backgrounds where contrast fails |
| color/feedback/error | #DC2626 | Error states, destructive actions | Warnings, general alerts |
| color/feedback/warning | #D97706 | Warning states only | Errors, success states |
| color/feedback/success | #16A34A | Confirmation, completed states | Decorative use |

### Spacing

| Token | Value | Use | Do Not Use |
|-------|-------|-----|------------|
| spacing/xs | 4px | Icon padding, tight inline gaps | Component-level spacing |
| spacing/sm | 8px | Internal component padding on small elements | Section or layout gaps |
| spacing/md | 16px | Internal component padding on default elements | Between unrelated sections |
| spacing/lg | 24px | Gaps between related content groups | Inside a single component |
| spacing/xl | 40px | Section-level gaps only | Component-level spacing |
| spacing/2xl | 64px | Page-level section separation | Anything smaller than a section |

### Typography

| Token | Value | Use | Do Not Use |
|-------|-------|-----|------------|
| text/display | 48px / 700 | Hero headings, page titles only | Section headings, cards |
| text/heading/lg | 32px / 600 | Primary section headings | Body content |
| text/heading/md | 24px / 600 | Sub-section headings, card titles | Replace body text |
| text/heading/sm | 18px / 500 | Tertiary headings, labels | Body or caption text |
| text/body/lg | 16px / 400 | Primary body content | Headings, captions |
| text/body/sm | 14px / 400 | Secondary body, helper text | Primary content |
| text/caption | 12px / 400 | Metadata, timestamps, footnotes | Body content |

### Border Radius

| Token | Value | Use |
|-------|-------|-----|
| radius/sm | 4px | Tags, badges, chips |
| radius/md | 8px | Cards, inputs, buttons |
| radius/lg | 12px | Modals, sheets, popovers |
| radius/full | 9999px | Avatars, toggles, pills |

## Components

### Buttons

#### ButtonPrimary

What: Primary action button. Highest visual weight in the system.

Use: Single primary action per view. One per screen section.

Do not use: Inside cards, inside modals, or repeated in a list.

Never: Place 2 ButtonPrimary components in the same section.

States required: default, hover, active, focus, disabled.

#### ButtonSecondary

What: Supporting action button. Use alongside a primary action.

Use: When a secondary choice exists next to a primary action.

Do not use: As a standalone CTA with no primary button present.

States required: default, hover, active, focus, disabled.

#### ButtonGhost

What: Tertiary action button. Lowest visual weight in the system.

Use: Cancel flows, destructive confirmations, low priority actions.

Do not use: Replace primary or secondary buttons.

States required: default, hover, active, focus, disabled.

#### ButtonIcon

What: Compact action button with icon only, no label.

Use: Toolbars, inline actions where label is not required.

Always: Include an aria-label. Never leave it empty.

States required: default, hover, active, focus, disabled.

### Form Elements

#### FormField

What: Wrapper for all form inputs in the system.

Use: Wraps every input, textarea, and select.

Do not use: Raw input elements directly. Always wrap with FormField.

Always: Include label, helper text slot, and error state slot even if empty.

States required: default, focus, filled, error, disabled.

#### InputText

What: Single-line text entry field.

Use: Single-line text input only.

Do not use: Multi-line content. Use Textarea instead.

States required: default, focus, filled, error, disabled.

#### InputSelect

What: Dropdown selection for 4 or more options.

Use: When there are 4 or more options to choose from.

Do not use: Binary choices. Use Toggle or RadioGroup instead.

States required: default, open, selected, error, disabled.

#### RadioGroup

What: Mutually exclusive option selector.

Use: 2 to 5 mutually exclusive options, all visible at once.

Do not use: More than 5 options. Use InputSelect instead.

States required: default, selected, error, disabled.

#### Toggle

What: Binary on/off switch with immediate effect.

Use: Binary on/off settings that take effect immediately.

Do not use: Form submissions that require confirmation.

States required: off, on, disabled.

### Cards

#### CardWithCTA

What: Content card with a single required action.

Use: When the card content leads to exactly one primary action.

Do not use: Dashboard widgets, read-only content, multiple actions.

Always: Pair with ButtonPrimary only. Never a text link.

States required: default, hover, loading, empty.

#### CardDefault

What: Read-only content card with no required action.

Use: Displaying information that requires no interaction.

Do not use: When any action or click is needed.

States required: default, empty.

#### CardInteractive

What: Fully clickable card that navigates to a detail view.

Use: When the entire card is the clickable target.

Do not use: When only part of the card is interactive.

States required: default, hover, active, focus.

### Navigation

#### NavBar

What: Top-level navigation bar. One per page.

Use: Top-level navigation only.

Do not use: Inside modals, drawers, or nested views.

States required: default, scrolled, mobile.

#### TabBar

What: Switcher between peer-level content sections.

Use: Switching between sections of equal hierarchy.

Do not use: Sequential flows or steps. Use Stepper instead.

States required: default, active, disabled.

#### Breadcrumb

What: Hierarchical location indicator.

Use: Pages 2 levels or deeper in the hierarchy.

Do not use: Top-level pages, modal flows.

States required: default, hover.

### Feedback

#### AlertBanner

What: Page-level system message for errors, warnings, or announcements.

Use: Page-level system messages only.

Do not use: Inline field validation. Use FormField error state instead.

Always: Include a dismiss action unless the message is critical.

States required: error, warning, success, info.

#### Toast

What: Transient confirmation of a completed action.

Use: Confirming a completed action. Disappears automatically.

Do not use: Errors requiring user action. Use AlertBanner instead.

Never: Stack more than 3 toasts simultaneously.

States required: default, success, error.

#### EmptyState

What: Placeholder for views that return zero results.

Use: Every list, table, or data view that can return zero results.

Always: Include a primary action to resolve the empty state.

States required: default, with action, loading.

## Global Rules

### Component Rules

Never rebuild a component that exists in this library.

Always check this manifest before generating any UI.

When in doubt between 2 components, pick the more specific one.

Never use raw HTML elements where a component exists.

### Spacing Rules

Use spacing tokens only. Never hardcode px values.

### Color Rules

Never mix feedback colors for decorative purposes.

color/brand/primary is for actions only. Not decoration.

### Typography Rules

One text/display per page maximum.

text/body/sm is for supporting content only.

### Accessibility Rules

Every interactive element needs an accessible label.

Never rely on color alone to communicate state.

Touch targets minimum 44x44px.

Always include focus states on interactive components.

### States Every Component Must Handle

- [ ] Default
- [ ] Hover
- [ ] Active / Pressed
- [ ] Focus (keyboard)
- [ ] Disabled
- [ ] Loading (if async)
- [ ] Error (if form element)
- [ ] Empty (if data-driven)

## What This File Is Not

This is not your Storybook. Not your Zeroheight. Not your Figma library. This file exists for agents that cannot ask questions or use intuition.

Keep it updated. Keep it honest. Keep it ruthlessly short.
