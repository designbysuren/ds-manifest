# Figma Community File: Complete Step by Step Guide
> How to build an agent-ready design system file in Figma.
> Follow this guide to create your own version or to understand how the community file was built.

---

## Overview

This guide walks through building a Figma file with 3 pages:

1. Components - Button and Card components with Dev Mode annotations
2. Tokens - All variables with usage rules
3. How to Use This File - Documentation and links

---

## Step 1: Set Up Variables

### Create the collection
1. Click the grid icon at the top right of Figma
2. Click "Local variables"
3. Click the plus icon next to Collections
4. Rename "Collection 1" to "Tokens"

### Important: Use forward slash for grouping
Figma does not allow dots in variable names.
Use forward slash instead: `color/brand/primary` not `color.brand.primary`
The slash creates nested folder groups automatically in the variables panel.

---

### Color Variables

Add these variables under the "Tokens" collection:

| Variable Name | Value | Description to add in description field |
|---|---|---|
| color/brand/primary | #2563EB | Use for primary actions only. Not hover states, backgrounds, borders, or decorative elements. |
| color/neutral/subtle | #F5F5F5 | Use for non-interactive background surfaces only. Not for text, borders, icons, or interactive elements. |
| color/neutral/strong | #171717 | Use for primary text and headings only. Not on light backgrounds where contrast fails. |
| color/feedback/error | #DC2626 | Use for error states and destructive actions only. Not for warnings or general alerts. |

### Spacing Variables

| Variable Name | Value | Description to add in description field |
|---|---|---|
| spacing/sm | 8 | Use for internal component padding on small elements. Not for section or layout gaps. |
| spacing/md | 16 | Use for internal component padding on default elements. Not between unrelated sections. |
| spacing/lg | 24 | Use for gaps between related content groups. Not inside a single component. |
| spacing/xl | 40 | Use for section-level gaps only. Not for component-level spacing. |

### Radius Variables

| Variable Name | Value | Description to add in description field |
|---|---|---|
| radius/sm | 4 | Use for tags, badges, and chips only. |
| radius/md | 8 | Use for cards, inputs, and buttons. |
| radius/lg | 12 | Use for modals, sheets, and popovers. |
| radius/full | 9999 | Use for avatars, toggles, and pill shapes only. |

### How to add description fields
1. Right click any variable row
2. Click "Edit variable"
3. Find the Description field at the bottom of the panel
4. Paste the description from the table above
5. Press Enter to save
6. Repeat for every variable

Do not skip this. The description field is the entire point of the variables setup.

---

## Step 2: Build the Button Component

### Create the base frame with auto layout
1. Press F to create a frame, draw any size
2. With the frame selected press Shift + A to add auto layout
3. Set direction to horizontal
4. Set horizontal padding to 16 - link to spacing/md variable
5. Set vertical padding to 12 - hardcode this value, no variable needed
6. Set alignment to center horizontal and center vertical

### Add the label
1. Press T to add a text layer inside the frame
2. Type "Label"
3. Set font to Inter, size 16, weight 600
4. Set color to #FFFFFF

### Set the fill and radius
1. Click the fill color swatch
2. Switch to the variable picker
3. Select color/brand/primary
4. Click the corner radius field
5. Switch to the variable picker
6. Select radius/md

### Create the component
1. Select the frame
2. Right click, choose "Create component"
3. Name it exactly: ButtonPrimary

### Add ButtonSecondary variant
1. Duplicate ButtonPrimary
2. Remove the fill
3. Add a stroke: 1.5px, link color to color/brand/primary variable
4. Change label color to color/brand/primary
5. Name it: ButtonSecondary

### Add ButtonGhost variant
1. Duplicate ButtonPrimary
2. Remove the fill
3. Remove any stroke
4. Add a transparent fill: #000000 at 0% opacity so the layer registers
5. Change label color to color/neutral/strong
6. Name it: ButtonGhost

### Combine into component set
1. Select all 3 button components
2. Right click, choose "Combine as variants"
3. Rename the component set to: Button
4. Remove any stroke on the outer component set wrapper
5. Add a property called "Type" with values Primary, Secondary, Ghost

---

## Step 3: Build the Card Component

### Create the base frame with auto layout
1. Press F to create a frame, draw any size
2. Press Shift + A to add auto layout
3. Set direction to vertical
4. Set width to 320
5. Set height to hug contents
6. Set padding all sides to 24 - link to spacing/lg variable
7. Set gap between items to 16 - link to spacing/md variable

### Set fill, radius, and shadow
1. Add fill: #FFFFFF
2. Link corner radius to radius/md variable
3. Click the plus icon next to Effects
4. Choose Drop Shadow
5. Set: X 0, Y 1, Blur 3, Spread 0, Color #000000 at 10% opacity

### Add content layers
1. Press T, add text: "Card Title"
   - Inter, 18px, weight 600
   - Link color to color/neutral/strong variable

2. Press T, add text: "Card description goes here"
   - Inter, 14px, weight 400
   - Color: #737373 hardcoded

3. From Assets panel drag ButtonPrimary into the card
   - Select it inside the card
   - Set horizontal sizing to Fill so it stretches edge to edge

### Create the component
1. Select the whole card frame
2. Right click, choose "Create component"
3. Name it exactly: CardWithCTA

### Create CardDefault variant
1. Select CardWithCTA, press Cmd + D to duplicate
2. Inside the duplicate delete the ButtonPrimary layer
3. Name this component: CardDefault

### Combine into component set
1. Select both card components
2. Right click, choose "Combine as variants"
3. Rename the component set to: Card
4. Remove any stroke on the outer component set wrapper
5. Add a property called "Type" with values WithCTA, Default

---

## Step 4: Add Dev Mode Annotations

### How to add annotations
1. Stay in Design mode (not Dev Mode)
2. Select the component you want to annotate
3. Press Shift + A
4. Click anywhere on the component to drop the annotation
5. Paste the text below
6. Click outside to save

### ButtonPrimary annotation
```
What: Primary action button. Highest visual weight in the system.
Use: Single primary action per view. One per screen section.
Do not use: Inside cards, inside modals, or repeated in a list.
Never: Place 2 ButtonPrimary components in the same section.
States required: default, hover, active, focus, disabled.
```

### ButtonSecondary annotation
```
What: Supporting action button. Use alongside a primary action.
Use: When a secondary choice exists next to a primary action.
Do not use: As a standalone CTA with no primary button present.
States required: default, hover, active, focus, disabled.
```

### ButtonGhost annotation
```
What: Tertiary action button. Lowest visual weight in the system.
Use: Cancel flows, destructive confirmations, low priority actions.
Do not use: Replace primary or secondary buttons.
States required: default, hover, active, focus, disabled.
```

### CardWithCTA annotation
```
What: Content card with a single required action.
Use: When the card content leads to exactly one primary action.
Do not use: Dashboard widgets, read-only content, multiple actions.
Always: Pair with ButtonPrimary only. Never a text link.
States required: default, hover, loading, empty.
```

### CardDefault annotation
```
What: Read-only content card with no required action.
Use: Displaying information that requires no interaction.
Do not use: When any action or click is needed.
States required: default, empty.
```

---

## Step 5: Add the Tokens Page

1. Click the plus icon next to Pages in the left panel
2. Name the new page: "Tokens"
3. Press F to create a frame, set width 800, hug height
4. Press Shift + A, padding 48 all sides, gap 32
5. Set fill to #0F0F0F

Add these text layers in order:

Title: "Tokens" - Inter 40px weight 700 color #FFFFFF
Subtitle: "All variables with usage rules" - Inter 18px weight 400 color #737373

Section heading "Color" - Inter 14px weight 600 color #2563EB
Then a text block with all color token entries and their use/do not use rules.

Section heading "Spacing" - same style
Then a text block with all spacing token entries and their use/do not use rules.

Section heading "Radius" - same style
Then a text block with all radius token entries and their use rules.

---

## Step 6: Add the Documentation Page

1. Add a new page, name it: "How to Use This File"
2. Press F, frame width 800, hug height
3. Press Shift + A, padding 48, gap 32
4. Fill #0F0F0F

Add these text layers:

Title: "system.md" - Inter 40px weight 700 color #FFFFFF
Subtitle: "Agent-Ready Design System Template" - Inter 18px weight 400 color #737373

Body text - Inter 16px weight 400 color #A3A3A3 line height 28:
```
This file exists for one reason.
Coding agents cannot open your Figma library mid-session.
They cannot ask your team what a component is for.
They only have what is written down.

Every variable has a description field explaining when to use it
and when not to. Every component has a Development annotation
answering 3 questions: what it is, when to use it, when not to.

The 3 file stack:

CLAUDE.md      How the agent behaves
DESIGN.md      What your tokens are and why
system.md      What your components are and how to use them

How to use this file:
1. Fork it
2. Replace the components with your own library
3. Fill in every description field for your own tokens
4. Add annotations to every component
5. Export your token rules to system.md

GitHub: github.com/designbysuren/ds-manifest
Article: [your Medium link after publishing]
```

---

## Step 7: Publish to Figma Community

### Before publishing checklist
- [ ] Collection renamed to "Tokens"
- [ ] All 12 variable description fields filled in
- [ ] All 5 components have Dev Mode annotations
- [ ] Tokens page complete
- [ ] Documentation page complete with real links
- [ ] Cover image ready at 1920x960

### How to publish
1. Click the Figma logo at top left
2. Go to "File"
3. Click "Publish to Community"

### Publish form details

Name:
```
system.md - Agent-Ready Design System Template
```

Description:
```
A minimal Figma file showing how to annotate your design system for coding agents.

Every variable has a description field explaining when to use it and when not to.
Every component has a Development annotation answering 3 questions:
what it is, when to use it, when not to.

The 3 file stack:
CLAUDE.md - how the agent behaves
DESIGN.md - what your tokens are and why
system.md - what your components are and how to use them

Fork this file. Replace with your own system.
Apply the same annotation pattern to every token and component.

Built alongside the Medium article:
I Gave My Agent CLAUDE.md and DESIGN.md. It Ignored My Entire Component Library.
By Suren - Suren Publication on Medium.
```

Tags:
```
design systems, AI, agents, tokens, components,
CLAUDE.md, DESIGN.md, system.md, Figma variables, Dev Mode
```

### After approval
1. Community file is live: https://www.figma.com/community/file/1638386195517568464/system-md-agent-ready-design-system-template
2. Add it to the Medium article as the first comment on publish day
3. Update the placeholder link in the documentation page
