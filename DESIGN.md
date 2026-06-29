# Design System: POPSTOP

## 1. Visual Theme & Atmosphere

POPSTOP should feel like a rebellious snack poster that learned how to be a highly legible utility app.

- **Density: 4/10** — airy enough to understand from several feet away, with no crowded control panels.
- **Variance: 8/10** — asymmetric compositions, offset blocks, and editorial scale changes keep the brand from looking corporate.
- **Motion: 6/10** — active listening states feel alive, but safety alerts remain immediate and unambiguous.
- **Core mood:** warm, tactile, loud, handmade, and useful.
- **Primary visual tension:** oversized irreverent typography paired with simple controls.

The app interface is calmer than the launch page. Personality belongs in headlines, illustrations, and transitions. Listening status, microphone permission, cancel controls, and the stop alert always favor clarity.

## 2. Color Palette & Roles

- **Microwave Cream** (`#F6EEDC`) — default canvas and quiet screen background.
- **Paper White** (`#FFFDF7`) — raised controls, instructional panels, and high-contrast areas.
- **Charcoal Kernel** (`#171512`) — primary text, borders, icons, and dark buttons. Never use pure black.
- **Smoke Gray** (`#6F6960`) — secondary text, metadata, and inactive labels.
- **Alarm Red** (`#D63D29`) — the single interactive accent: primary actions, active states, errors, and the Stop Now screen.
- **Butter Yellow** (`#E9C94A`) — supporting surface for education and ready states; never a competing primary CTA.
- **Bag Pink** (`#DFA0B1`) — supporting editorial surface used sparingly in brand storytelling, never for safety status.
- **Structural Line** (`rgba(23, 21, 18, 0.28)`) — dividers and quiet borders.

### Color Rules

- Alarm Red is the only action accent.
- Yellow and pink are background fields, not additional button systems.
- Never communicate listening, warning, or failure through color alone; pair color with text and shape.
- Maintain WCAG AA contrast for body text and controls.
- Do not use purple, blue neon, gradients, outer glows, or mixed warm/cool neutral systems.

## 3. Typography Rules

- **Display:** `Cabinet Grotesk`, weight 800–900, tight tracking between `-0.06em` and `-0.035em`, line-height `0.9–1`. Use for launch headlines and short app declarations.
- **Editorial Accent:** `Instrument Serif`, weight 500–600, used only for short expressive phrases on marketing surfaces. Never use it for controls, status, instructions, or settings.
- **Interface and Body:** `Satoshi`, weight 400–700, line-height `1.45–1.65`, maximum line length `65ch`.
- **Numbers and Live Status:** `Geist Mono`, weight 600–700, used for timers, app versions, diagnostics, and event counts.

### Type Scale

- Marketing display: `clamp(3rem, 8vw, 7rem)`.
- Mobile app alert: `clamp(3rem, 14vw, 5.5rem)`.
- Screen title: `clamp(2rem, 7vw, 3.25rem)`.
- Body: `1rem` minimum.
- Labels and metadata: `0.8125rem` minimum with increased letter spacing.

Never use Inter, Arial, Helvetica, Times New Roman, Georgia, Garamond, or Palatino in final branded work.

## 4. Component Stylings

- **Primary buttons:** Alarm Red fill, Paper White label, `3px` Charcoal border, square-to-soft corners between `8px` and `14px`, and a `4px 4px 0` Charcoal offset shadow. Active state moves `3px` in both axes and removes most of the shadow.
- **Secondary buttons:** Paper White fill, Charcoal label and border, no competing accent fill.
- **Critical stop action:** full-width or large circular control with explicit text. Never icon-only. It must remain obvious at arm’s length.
- **Cards:** use only for instructions or distinct state groups. Flat supporting-color fill, `3px` Charcoal border, limited offset shadow, and corners no larger than `18px`.
- **Status indicators:** combine a written state, shape, and restrained transform/opacity motion. Approved labels include “Listening,” “Hearing pops,” “Too noisy,” and “Stop now.”
- **Inputs and settings rows:** label above input, helper text below, inline error beneath the relevant control. Focus uses a `2px` Alarm Red outline with `2px` offset.
- **Loaders:** waveform or skeleton matching the final layout. Never use a generic circular spinner.
- **Permission states:** show what access is needed, why it is needed, whether audio leaves the device, and one clear recovery action.
- **Alerts:** use direct language and strong contrast. The Stop Now alert must not disappear automatically.

## 5. Layout Principles

- Use CSS Grid for structural page layouts and normal document flow for content.
- Keep all web content inside a centered `max-width: 1400px` container.
- Marketing heroes use a left-copy/right-visual split or another clearly asymmetric composition.
- App screens use one dominant action per state.
- Never overlap text and imagery. Decorative marks may sit around a composition but cannot obscure content.
- Avoid three identical feature cards in one row. Use an asymmetric `2fr 1fr` grid, a zig-zag explanation, or a stacked sequence.
- Use `min-height: 100dvh` for full-screen web and app states.
- Listening and Stop Now screens must remain readable without scrolling on common phone sizes.
- Minimum touch target: `48px × 48px`.
- Mobile layouts below `768px` collapse to one column with at least `1rem` horizontal padding.
- Horizontal overflow is a critical failure.
- Verify at widths `375px`, `390px`, `768px`, `1024px`, and `1440px`.

### Stitch Screen Direction

When generating screens in Google Stitch:

- Create one screen for one user state.
- Preserve the same color names and roles across every prompt.
- Ask for clean spatial separation and no overlapping layers.
- Keep decorative popcorn artwork subordinate to the primary control.
- Generate Ready, Permission, Listening, Stop Now, Result, and Settings as a visually related set.

## 6. Motion & Interaction

- Use spring-like motion with an intended baseline of `stiffness: 100` and `damping: 20`.
- Animate only `transform` and `opacity` in continuous loops.
- The listening dot may pulse; the waveform may scale vertically; detected-pop feedback may briefly expand and settle.
- New instructions or settings rows may reveal with `70–100ms` staggered delays.
- Button presses should feel tactile through a short translate or `scale(0.98)` response.
- Stop Now interrupts all decorative motion and replaces it with a deliberate alert pulse.
- Respect reduced-motion preferences by removing floating, pulsing, and cascade effects while preserving state changes.
- Avoid motion that could delay permission, cancel, or stop actions.

## 7. Anti-Patterns (Banned)

- No emojis in interface copy, labels, icons, or alt text.
- No banned customer-facing words from `AGENTS.md`.
- No Inter or generic system typography in final branded work.
- No generic serif fonts.
- No pure black.
- No purple or blue neon styling.
- No gradients or outer glows.
- No overlapping text and images.
- No centered marketing hero.
- No three equal feature cards in a row.
- No generic software-dashboard styling.
- No oversized rounded pills on every component.
- No custom cursor.
- No circular loading spinner.
- No tiny icon-only safety controls.
- No invented testimonials, metrics, ratings, or accuracy claims.
- No filler prompts such as “Scroll to explore” or “Swipe down.”
- No AI-copy clichés such as “Elevate,” “Unleash,” “Next-Gen,” or “Revolutionize.”
- No animation of `top`, `left`, `width`, or `height`.
- No `height: 100vh`; use `min-height: 100dvh`.
