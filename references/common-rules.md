# Common Rules for Professional UI

Frequently overlooked issues that make UI look unprofessional.

## Icons & Visual Elements

| Rule | Standard | Avoid |
|------|----------|-------|
| No Emoji as Structural Icons | Use vector-based icons (Lucide, react-native-vector-icons) | Emojis for navigation, settings, or system controls |
| Vector-Only Assets | SVG or platform vector icons that scale cleanly | Raster PNG icons that blur or pixelate |
| Stable Interaction States | Color, opacity, or elevation transitions without changing layout bounds | Layout-shifting transforms that cause jitter |
| Correct Brand Logos | Official brand assets with correct proportions and clear space | Guessing logo paths, recoloring unofficially |
| Consistent Icon Sizing | Define icon sizes as design tokens (icon-sm, icon-md=24pt, icon-lg) | Mixing arbitrary values randomly |
| Stroke Consistency | Consistent stroke width within same visual layer | Mixing thick and thin stroke styles |
| Touch Target Minimum | 44×44pt interactive area (use hitSlop if icon is smaller) | Small icons without expanded tap area |

## Interaction (App)

| Rule | Do | Don't |
|------|----|----- |
| Tap feedback | Clear pressed feedback (ripple/opacity/elevation) within 80-150ms | No visual response on tap |
| Animation timing | Micro-interactions 150-300ms with platform-native easing | Instant transitions or slow animations (>500ms) |
| Accessibility focus | Screen reader focus matches visual order; descriptive labels | Unlabeled controls or confusing focus traversal |
| Disabled state | Reduced opacity (0.38–0.5) + cursor change + semantic attribute | Controls that look tappable but do nothing |
| Touch target | >=44x44pt (iOS) or >=48x48dp (Android) | Tiny tap targets without padding |
| Gesture conflicts | One primary gesture per region | Overlapping gestures causing accidental actions |
| Semantic controls | Native interactive primitives with proper accessibility roles | Generic containers without semantics |

## Light/Dark Mode Contrast

| Rule | Do | Don't |
|------|----|----- |
| Text contrast (light) | Body text contrast >=4.5:1 against light surfaces | Low-contrast gray body text |
| Text contrast (dark) | Primary text >=4.5:1 and secondary >=3:1 on dark surfaces | Text that blends into background |
| Border visibility | Separators visible in both themes | Borders disappearing in one mode |
| State contrast parity | Pressed/focused/disabled states distinguishable in both themes | States defined for one theme only |
| Token-driven theming | Semantic color tokens mapped per theme | Hardcoded per-screen hex values |
| Scrim legibility | Modal scrim 40-60% black to isolate foreground | Weak scrim with competing background |

## Layout & Spacing

| Rule | Do | Don't |
|------|----|----- |
| Safe-area compliance | Respect top/bottom safe areas for fixed headers, tab bars, CTA bars | UI under notch, status bar, or gesture area |
| Consistent content width | Predictable content width per device class | Mixing arbitrary widths between screens |
| 8dp spacing rhythm | Consistent 4/8dp spacing for padding/gaps/sections | Random spacing increments |
| Readable text measure | Long-form text readable on large devices | Edge-to-edge paragraphs on tablets |
| Adaptive gutters | Increase horizontal insets on larger widths and landscape | Same narrow gutter on all sizes |
| Scroll coexistence | Bottom/top content insets so lists not hidden behind fixed bars | Content obscured by sticky headers/footers |
