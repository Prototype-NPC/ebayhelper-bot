# Design System Document: The Utility Auteur

## 1. Overview & Creative North Star
**Creative North Star: The Precision Curator**
This design system rejects the "marketplace clutter" of traditional e-commerce. Instead, it adopts the persona of a high-end digital concierge—a "Precision Curator." We are merging the high-octane vibrance of the eBay brand with the dark, disciplined soul of the "Linear" aesthetic. 

To move beyond a generic tech template, the system utilizes **Intentional Asymmetry** and **Tonal Depth**. We break the grid by allowing functional accents to bleed into the margins and using extreme typographic contrast. This isn't just a bot; it's a professional-grade instrument for power users who value speed, silence, and sophisticated utility.

---

## 2. Colors
Our palette translates iconic brand heritage into a dark-mode architecture. We move away from "blocks of color" toward "light as a functional signal."

### The Functional Spectrum
*   **Primary (`#adc6ff` / `#0064d2`):** Reserved for Search, Discovery, and "Buying" logic. Use for the primary path.
*   **Secondary (`#a3d73a` / `#7cad01`):** Logic associated with Profit, Success, and "Sold" data.
*   **Tertiary (`#ffb3ae` / `#cb1c29`):** High-priority alerts, "Outbid" states, or critical system errors.
*   **Surface / Background (`#131313`):** The deep foundation. Every element emerges from this void.

### The Rules of Engagement
*   **The "No-Line" Rule:** 1px solid borders are strictly prohibited for sectioning. Boundaries must be defined through background shifts. Place a `surface_container_low` card on a `surface` background to create a seam.
*   **Surface Hierarchy & Nesting:** Treat the UI as stacked sheets of obsidian. 
    *   *Level 0:* `surface` (The canvas)
    *   *Level 1:* `surface_container_low` (Secondary content/Sidebars)
    *   *Level 2:* `surface_container` (Primary cards/Main interaction)
    *   *Level 3:* `surface_container_highest` (Active Modals/Popovers)
*   **The "Glass & Gradient" Rule:** Floating elements (Modals, Tooltips) must use `surface_container_highest` with a 20px backdrop-blur and 85% opacity. CTAs should utilize a subtle linear gradient from `primary` to `primary_container` at a 135-degree angle to provide "optical volume."

---

## 3. Typography
We use **Inter** as a structural element, not just a font. To achieve the premium editorial look, we lean into high contrast and aggressive tracking.

*   **Display & Headlines (`display-lg` to `headline-sm`):** Set to `font-weight: 700` with a letter-spacing of `-0.04em`. These should feel like heavy, architectural blocks.
*   **Titles (`title-lg` to `title-sm`):** Set to `font-weight: 600` with `-0.02em` tracking. Use these to anchor content modules.
*   **Body (`body-lg` to `body-md`):** Set to `font-weight: 400`. Tracking is `0`. Used for data descriptions and log outputs.
*   **Labels (`label-md` to `label-sm`):** Set to `font-weight: 500` and `text-transform: uppercase`. Letter-spacing: `0.05em`. These are functional signposts.

**Editorial Hierarchy:** Pair a `display-sm` value with a `label-sm` immediately above it to create an "authoritative header" lockup.

---

## 4. Elevation & Depth
In this system, depth is a product of light and layering, not structural lines.

*   **The Layering Principle:** Avoid drop shadows for static layout components. Instead, use the spacing scale (e.g., `spacing-4`) and tonal shifts. A card using `surface_container_lowest` nested inside a `surface_container` creates a "recessed" look that feels more modern than a shadow.
*   **Ambient Shadows:** For floating action buttons or elevated modals, use a "Shadow Bloom":
    *   *Color:* `on_surface` at 6% opacity.
    *   *Blur:* 40px to 60px.
    *   *Offset:* 12px Y-axis. 
*   **The "Ghost Border" Fallback:** If a container requires a border for focus (e.g., an active input), use `outline_variant` at 15% opacity. Never use 100% opaque lines.
*   **Glassmorphism:** Use `surface_variant` with a 0.8 alpha and `backdrop-filter: blur(12px)` for navigation bars to let the background content softly bleed through as the user scrolls.

---

## 5. Components

### Buttons
*   **Primary:** Gradient of `primary` to `primary_container`. Border-radius: `rounded-md`. Text: `label-md` in `on_primary`.
*   **Secondary:** Ghost style. Transparent background with a 10% `outline` border.
*   **States:** Hover should increase the brightness of the surface by 10%. Active state should scale the button to 0.98.

### Input Fields
*   **Style:** Minimalist. No bottom line. Fill color: `surface_container_high`. 
*   **Focus:** A subtle `primary` outer glow (4px blur) and the text label shifts to `primary` color.
*   **Validation:** Use `tertiary` (Red) for error states, but only on the label and a small 2px left-accent bar, not a full red box.

### Cards & Lists
*   **The Divider Ban:** Never use horizontal rules (`<hr>`). Use `spacing-6` or a 1-step shift in `surface_container` values to separate items.
*   **Interactive Lists:** On hover, a list item should transition to `surface_container_highest` with a `rounded-sm` corner.

### Signature Component: The "Data Pulse"
A custom component for 'EbayHelper Bot'—a small, glowing dot using `secondary` (Green) or `primary` (Blue) with a CSS pulse animation. This sits next to "Live Monitoring" labels to indicate the bot is active without distracting from the UI.

---

## 6. Do's and Don'ts

### Do
*   **Do** use vertical white space aggressively. If it feels too empty, add 10% more space.
*   **Do** use `secondary` (Green) and `tertiary` (Red) sparingly as "surgical" accents to denote profit/loss.
*   **Do** align all typography to a strict baseline grid to maintain the "Linear" aesthetic.

### Don't
*   **Don't** use pure white (`#FFFFFF`) for text. Use `on_surface` or `on_surface_variant` to prevent eye strain on the dark background.
*   **Don't** use rounded-full (pill) shapes for anything other than status chips. Keep the system's "Precision" feel with `rounded-md` or `rounded-sm`.
*   **Don't** use standard "Select All" checkboxes. Use custom toggle switches or "Tile" selections to maintain a premium feel.