# Quick Reference — UI/UX Rules by Priority

### 1. Accessibility (CRITICAL)

- `color-contrast` - Minimum 4.5:1 ratio for normal text (large text 3:1)
- `focus-states` - Visible focus rings on interactive elements (2–4px)
- `alt-text` - Descriptive alt text for meaningful images
- `aria-labels` - aria-label for icon-only buttons; accessibilityLabel in native
- `keyboard-nav` - Tab order matches visual order; full keyboard support
- `form-labels` - Use label with for attribute
- `skip-links` - Skip to main content for keyboard users
- `heading-hierarchy` - Sequential h1→h6, no level skip
- `color-not-only` - Don't convey info by color alone (add icon/text)
- `dynamic-type` - Support system text scaling; avoid truncation as text grows
- `reduced-motion` - Respect prefers-reduced-motion
- `voiceover-sr` - Meaningful accessibilityLabel/accessibilityHint; logical reading order
- `escape-routes` - Provide cancel/back in modals and multi-step flows
- `keyboard-shortcuts` - Preserve system and a11y shortcuts

### 2. Touch & Interaction (CRITICAL)

- `touch-target-size` - Min 44×44pt (Apple) / 48×48dp (Material)
- `touch-spacing` - Minimum 8px/8dp gap between touch targets
- `hover-vs-tap` - Use click/tap for primary interactions; don't rely on hover alone
- `loading-buttons` - Disable button during async operations; show spinner or progress
- `error-feedback` - Clear error messages near problem
- `cursor-pointer` - Add cursor-pointer to clickable elements (Web)
- `gesture-conflicts` - Avoid horizontal swipe on main content; prefer vertical scroll
- `tap-delay` - Use touch-action: manipulation to reduce 300ms delay (Web)
- `standard-gestures` - Use platform standard gestures consistently
- `system-gestures` - Don't block system gestures (Control Center, back swipe, etc.)
- `press-feedback` - Visual feedback on press (ripple/highlight)
- `haptic-feedback` - Use haptic for confirmations and important actions; avoid overuse
- `gesture-alternative` - Don't rely on gesture-only interactions; always provide visible controls
- `safe-area-awareness` - Keep primary touch targets away from notch, Dynamic Island, gesture bar
- `no-precision-required` - Avoid requiring pixel-perfect taps on small icons
- `swipe-clarity` - Swipe actions must show clear affordance or hint
- `drag-threshold` - Use a movement threshold before starting drag

### 3. Performance (HIGH)

- `image-optimization` - Use WebP/AVIF, responsive images, lazy load non-critical assets
- `image-dimension` - Declare width/height or use aspect-ratio to prevent layout shift
- `font-loading` - Use font-display: swap/optional to avoid FOIT
- `font-preload` - Preload only critical fonts
- `critical-css` - Prioritize above-the-fold CSS
- `lazy-loading` - Lazy load non-hero components via dynamic import / route-level splitting
- `bundle-splitting` - Split code by route/feature to reduce initial load and TTI
- `third-party-scripts` - Load third-party scripts async/defer
- `reduce-reflows` - Avoid frequent layout reads/writes; batch DOM reads then writes
- `content-jumping` - Reserve space for async content to avoid layout jumps
- `virtualize-lists` - Virtualize lists with 50+ items
- `main-thread-budget` - Keep per-frame work under ~16ms for 60fps
- `progressive-loading` - Use skeleton screens / shimmer instead of spinners for >1s operations
- `input-latency` - Keep input latency under ~100ms for taps/scrolls
- `debounce-throttle` - Use debounce/throttle for high-frequency events
- `offline-support` - Provide offline state messaging and basic fallback

### 4. Style Selection (HIGH)

- `style-match` - Match style to product type (use `--design-system` for recommendations)
- `consistency` - Use same style across all pages
- `no-emoji-icons` - Use SVG icons (Heroicons, Lucide), not emojis
- `effects-match-style` - Shadows, blur, radius aligned with chosen style
- `platform-adaptive` - Respect platform idioms (iOS HIG vs Material)
- `state-clarity` - Make hover/pressed/disabled states visually distinct
- `elevation-consistent` - Use a consistent elevation/shadow scale
- `dark-mode-pairing` - Design light/dark variants together
- `icon-style-consistent` - Use one icon set/visual language across the product
- `system-controls` - Prefer native/system controls over fully custom ones
- `primary-action` - Each screen should have only one primary CTA

### 5. Layout & Responsive (HIGH)

- `viewport-meta` - width=device-width initial-scale=1 (never disable zoom)
- `mobile-first` - Design mobile-first, then scale up
- `breakpoint-consistency` - Use systematic breakpoints (375 / 768 / 1024 / 1440)
- `readable-font-size` - Minimum 16px body text on mobile
- `line-length-control` - Mobile 35–60 chars; desktop 60–75 chars
- `horizontal-scroll` - No horizontal scroll on mobile
- `spacing-scale` - Use 4pt/8dp incremental spacing system
- `container-width` - Consistent max-width on desktop
- `z-index-management` - Define layered z-index scale
- `orientation-support` - Keep layout readable in landscape mode
- `content-priority` - Show core content first on mobile
- `visual-hierarchy` - Establish hierarchy via size, spacing, contrast — not color alone

### 6. Typography & Color (MEDIUM)

- `line-height` - Use 1.5-1.75 for body text
- `line-length` - Limit to 65-75 characters per line
- `font-pairing` - Match heading/body font personalities
- `font-scale` - Consistent type scale (e.g. 12 14 16 18 24 32)
- `color-semantic` - Define semantic color tokens not raw hex in components
- `color-dark-mode` - Dark mode uses desaturated/lighter tonal variants, not inverted colors
- `color-accessible-pairs` - Foreground/background pairs must meet 4.5:1 (AA) or 7:1 (AAA)
- `truncation-strategy` - Prefer wrapping over truncation
- `number-tabular` - Use tabular/monospaced figures for data columns and prices
- `whitespace-balance` - Use whitespace intentionally to group related items

### 7. Animation (MEDIUM)

- `duration-timing` - 150–300ms for micro-interactions; complex transitions ≤400ms
- `transform-performance` - Use transform/opacity only; avoid animating width/height
- `loading-states` - Show skeleton or progress indicator when loading exceeds 300ms
- `easing` - Use ease-out for entering, ease-in for exiting
- `motion-meaning` - Every animation must express cause-effect, not just be decorative
- `spring-physics` - Prefer spring/physics-based curves for natural feel
- `exit-faster-than-enter` - Exit animations shorter (~60–70% of enter duration)
- `stagger-sequence` - Stagger list/grid item entrance by 30–50ms per item
- `interruptible` - Animations must be interruptible by user gesture
- `no-blocking-animation` - Never block user input during an animation
- `navigation-direction` - Forward = left/up; backward = right/down
- `layout-shift-avoid` - Animations must not cause layout reflow or CLS

### 8. Forms & Feedback (MEDIUM)

- `input-labels` - Visible label per input (not placeholder-only)
- `error-placement` - Show error below the related field
- `submit-feedback` - Loading then success/error state on submit
- `empty-states` - Helpful message and action when no content
- `toast-dismiss` - Auto-dismiss toasts in 3-5s
- `confirmation-dialogs` - Confirm before destructive actions
- `progressive-disclosure` - Reveal complex options progressively
- `inline-validation` - Validate on blur (not keystroke)
- `input-type-keyboard` - Use semantic input types to trigger correct mobile keyboard
- `undo-support` - Allow undo for destructive or bulk actions
- `error-clarity` - Error messages must state cause + how to fix
- `focus-management` - After submit error, auto-focus the first invalid field
- `destructive-emphasis` - Destructive actions use danger color and are visually separated

### 9. Navigation Patterns (HIGH)

- `bottom-nav-limit` - Bottom navigation max 5 items; use labels with icons
- `back-behavior` - Back navigation must be predictable; preserve scroll/state
- `deep-linking` - All key screens must be reachable via deep link / URL
- `nav-label-icon` - Navigation items must have both icon and text label
- `nav-state-active` - Current location must be visually highlighted in navigation
- `modal-escape` - Modals must offer clear close/dismiss affordance
- `state-preservation` - Navigating back must restore previous scroll/filter/input state
- `gesture-nav-support` - Support system gesture navigation without conflict
- `adaptive-navigation` - Large screens prefer sidebar; small screens use bottom/top nav
- `navigation-consistency` - Navigation placement stays the same across all pages
- `persistent-nav` - Core navigation must remain reachable from deep pages

### 10. Charts & Data (LOW)

- `chart-type` - Match chart to data (trend → line, comparison → bar, proportion → pie)
- `color-guidance` - Use accessible color palettes; avoid red/green only pairs
- `pattern-texture` - Supplement color with patterns/textures/shapes
- `legend-visible` - Always show legend; position near chart
- `tooltip-on-interact` - Provide tooltips/data labels on hover or tap
- `responsive-chart` - Charts must reflow or simplify on small screens
- `empty-data-state` - Show meaningful empty state when no data exists
- `no-pie-overuse` - Avoid pie/donut for >5 categories; switch to bar chart
- `screen-reader-summary` - Provide text summary or aria-label for screen readers
- `time-scale-clarity` - Time series must clearly label time granularity
