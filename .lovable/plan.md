

## Plan: Expandable Explore Location Descriptions

**What**: Make explore result items expandable — clicking a location toggles its full description instead of truncating it. Clicking still also triggers the map pan/info panel.

**Changes in `src/components/ExploreSidebar.tsx`**:
1. Add `expandedIndex` state (`number | null`)
2. On click of a result item, toggle `expandedIndex` (expand/collapse) AND call `onSelect`
3. When expanded, remove `line-clamp-2` from the description so the full text is visible
4. Add a subtle visual indicator (e.g. slight background highlight) for the expanded item

Single file change, minimal complexity.

