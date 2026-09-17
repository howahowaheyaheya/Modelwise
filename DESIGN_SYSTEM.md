# ModelWise Design System

## Brand idea

ModelWise is the calm, evidence-led guide for choosing and mastering AI. Its personality combines the Sage and Guide archetypes: precise, candid, optimistic, and useful.

## Recognizable signature

1. **Midnight + cobalt + mint** — `#07152F`, `#0866FF`, and `#31C99B` form the primary visual signature.
2. **The model orbit** — concentric decision paths and nodes represent comparison, judgment, and progress without using generic robot imagery.
3. **Editorial scale** — large, tightly tracked headings contrast with compact uppercase evidence labels.
4. **Evidence panels** — bordered, low-radius cards feel precise and professional; status color is reserved for meaning.
5. **Learning intelligence** — tutor and coach surfaces use a pale cobalt field, mint signal, and the `MODELWISE INTELLIGENCE` label.

## Typography

- UI and body: system sans stack for fast rendering and excellent device support.
- Hero: `clamp(55px, 7vw, 100px)`, 0.92 line height, strongly negative tracking.
- Page title: 38–68px depending on context.
- Body: 16px, 1.6–1.75 line height; lesson copy is capped at 900px.
- Labels: 10–12px, 700–800 weight, 0.1–0.16em tracking.

## Spatial system

- Base unit: 4px.
- Common steps: 8, 12, 16, 24, 32, 48, 64, 96px.
- Marketing content uses 7vw side gutters and wide negative space.
- Application surfaces use a 255px desktop rail, 76px compact rail, and mobile bottom navigation.
- Readable learning content stays below 900px.

## Interaction

- Fast state changes: 150ms.
- Card and panel transitions: 220ms using `cubic-bezier(0.2, 0.8, 0.2, 1)`.
- Focus is always visible with a 3px light-cobalt ring.
- Reduced-motion preferences disable nonessential animation.

## Components

- Primary buttons use cobalt with white text; secondary buttons use a white surface and cool-gray border.
- Cards use thin borders, low radii, and subtle elevation on hover.
- Status tags use semantic colors and never rely on color alone.
- Admin tables retain headers and horizontal scrolling on narrow screens.
- AI Tutor and Coach panels have a cobalt-to-white wash, mint signal, and explicit intelligence label.

## Accessibility

The core text/background combinations meet WCAG AA contrast. Controls are keyboard reachable, use semantic elements, retain visible focus, and respect `prefers-reduced-motion`. Touch controls remain at least 44px where primary actions are used.
