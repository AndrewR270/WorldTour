

## Problem

The panel uses dark-theme CSS variables where `text-foreground` resolves to near-white (`95% lightness`). Combined with the `backdrop-blur` and semi-transparent background, the panel appears light but all text renders in white — making it unreadable (as shown in the screenshot).

## Solution

Switch the InfoPanel to use explicit dark text colors for all body content, section headers, and metadata. Keep white text only for the location name overlay on the hero image (where it sits on a dark gradient).

## Changes

### `src/components/InfoPanel.tsx`

1. **Section header card** (line ~259): Change `text-foreground` → `text-gray-900` for the tab label heading (e.g. "History")
2. **Section subtitle** (line ~263): Change `text-muted-foreground` → `text-gray-500` for the location name under the heading
3. **RichContent component** (~line 101-106): Change all `text-foreground/80` → `text-gray-800` for paragraph and list item text
4. **RichLine bold** (~line 85): Change `text-foreground` → `text-gray-900` for bold text
5. **Empty state text** (~line 275): Change `text-muted-foreground` → `text-gray-500`
6. **Panel background**: Change `bg-card/98` to a solid light background like `bg-white` or `bg-gray-50` so text contrast is guaranteed regardless of backdrop blur
7. **Tab bar border, footer text**: Update to use gray-scale colors that work on a light panel background
8. **Tabs**: Inactive tabs use dark text (`text-gray-700`), active tabs keep the primary color scheme
9. **Loading state text**: Switch to dark colors (`text-gray-800`, `text-gray-500`)

### What stays white
- Location name on the hero image (has dark gradient behind it)
- Coordinate text on the hero image

This ensures all readable body content uses dark text on a light panel, matching standard map-app UX patterns.

