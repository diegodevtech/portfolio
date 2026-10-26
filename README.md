# Diego Cunha · Portfolio

A one-page portfolio for **Diego Cunha, Lead Frontend Engineer**, built like a motion-design reel. It is a single HTML file, with no JavaScript, no build step and no dependencies. Every animation is done in CSS.

> Storefronts, component libraries and design systems for Sally Beauty, CosmoProf and Good Sam.

---

## What's on the page

| Section | What it shows | Motion |
| --- | --- | --- |
| **Hero** | Name, role, links and four key numbers | Letters rise in one by one on a variable font. The role types itself out. A mock editor window shows a product card assembling itself from design tokens, with a timeline, playhead and running timecode. |
| **Stack marquee** | Technologies I work with | A loop that runs forever and pauses on hover. |
| **Sally Beauty & CosmoProf** | Current role: lead frontend on two SFCC storefronts | One component re-themed live between two brands, only by changing token values. |
| **Good Sam** | Design system and CMS platform work | A component counter that counts up as you scroll, a wall of example components, an animated publishing flow from design to Storybook to Payload to Vercel, and impact bars. |
| **How I build** | Tokens → primitives → components → patterns → pages | A 3D stack of layers that pulls apart and highlights each layer in step with the list. |
| **Before that** | Earlier roles at FITec, ITRIAD and SEDECTI | Each role fades in as you scroll. |
| **Contact** | Email, LinkedIn and GitHub | Outlined headline words breathe through weight changes, with an orbiting accent behind them. |

## How it's built

The whole page is [`index.html`](index.html): about 2,900 lines of CSS followed by the markup. The CSS techniques that do the work:

- **Registered custom properties (`@property`).** Colors, lengths and integers are typed, so CSS can animate them. This drives the brand switch (`--tb`, `--tf`, `--ta`, `--tr`), the `90+` counter (`--n`), the timecode (`--sec`, `--fr`) and the 3D stack spacing (`--gap`).
- **CSS counters for numbers that change.** The counter and the `00:00:0X:YY` timecode are made with `counter()` in `::after`, so they need no script.
- **Scroll-driven animations.** `animation-timeline: scroll()` runs the reading progress bar. `view()` runs section reveals, the parallax effect, the counter and the impact bars.
- **Variable fonts.** The Anybody font's width and weight axes (`wdth`, `wght`) are animated directly for the name, the counter and the contact headline.
- **Container queries.** Large headings size themselves with `cqi` units, so they fill their own column instead of the viewport.
- **Separate themes per section.** Each employer section sets its own `--rule`, `--hi`, `--chip` and `--hi-ink`, so shared components such as lists, tech chips and links pick up that section's colours automatically. This mirrors how the real work themes one system for several brands.
- **One shared loop length.** All the studio animations use one `--loop` duration (9s) with matching keyframe percentages, so the card, tokens, cursor and playhead stay in sync.

### Design tokens

| Token | Use |
| --- | --- |
| `--paper`, `--ink`, `--accent` | Base reel: light steel, near-black, electric blue |
| `--s-*` | Sally Beauty / CosmoProf section: plum, blush, gold |
| `--g-*` | Good Sam section: forest, amber, signal red |
| `--f-display`, `--f-body`, `--f-mono` | Anybody, Geist, Geist Mono (Google Fonts) |
| `--ease-out`, `--ease-spring`, `--ease-io` | The three easing curves used across the page |

## Accessibility

- **Reduced motion.** With `prefers-reduced-motion: reduce`, every animation and transition is turned off and the page shows its final state. For example, the counter reads `90+` straight away, and decorative pieces like the cursor and playhead are hidden.
- **Content before decoration.** All decorative graphics are `aria-hidden`. The hero name has a plain `aria-label`, and the visual counter has text for screen readers.
- **Nothing starts hidden.** Scroll reveals begin from a partly visible state, so content is never stuck invisible if an animation doesn't run.
- **Landmarks and focus.** The page uses semantic sections with `aria-labelledby`, a labelled nav, and `:focus-visible` outlines.

## Browser support

The page works in any modern browser. Browsers that support scroll-driven animations get the scroll effects. Others get a fully visible, static layout, and the counter falls back to a timed count-up on load (`@supports not (animation-timeline: view())`).

## Running it locally

There is nothing to install.

```bash
git clone https://github.com/diegodevtech/portfolio.git
cd portfolio
```

Then open `index.html` in a browser, or serve the folder with any static server:

```bash
npx serve .
```

## Deploying

Any static host works: GitHub Pages, Vercel, Netlify or Cloudflare Pages. Point it at the repository root.

## Contact

- Email: [diegocunhaam@gmail.com](mailto:diegocunhaam@gmail.com)
- LinkedIn: [linkedin.com/in/diego-cunha-dev](https://www.linkedin.com/in/diego-cunha-dev/)
- GitHub: [github.com/diegodevtech](https://github.com/diegodevtech)

---

© 2026 Diego Cunha. Animated with CSS only.
