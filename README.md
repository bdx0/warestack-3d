# WareStack 3D — Logistics World v4

**Live:** https://bdx0.github.io/warestack-3d/

A self-contained WebGL logistics-world simulation inspired by the WareTrack demo. The UI, 3D procedural geometry and fallback renderer are embedded in a single `index.html`; there are no external 3D assets, libraries, CDN requests or APIs.

## What's in the world?

- 9 warehouse buildings across three camera-focus regions: Riverside, Northgate, Eastport.
- Two open racking areas; docks, aisles, pallets and inventory staging.
- Interconnected roads, security checkpoint, container yard, service/charging bay and control tower.
- 6 trucks, 8 forklifts, animated routes, trees, light poles, marked lanes.
- 270 selectable world entities, including 240 independently identifiable storage bins with SKU, quantity, lot and capacity.
- Clickable minimap, overview/region shortcuts, pause, time-speed, labels, search and fleet/inventory filters.
- WebGL rendering with depth buffer, plus Canvas 2D fallback and built-in diagnostics.
- Responsive layout, swipe to orbit, two-finger pan, cursor-anchored wheel zoom, bounded pinch zoom and safe reset. No page scroll.

### Warehouse Explorer

Click **🏭 Vào kho** to focus WH-01, WH-03 or WH-06 and hide the roof for a cutaway look. Each room contains shelves and individually selectable locations (72 + 72 + 96 = **240**). Select a slot in the 3D view or bin list to inspect SKU, quantity, lot and shelf position. **Mái** switches automatic / hidden / visible. **⌂** restores the full-campus camera. These inventory values are simulated, not synchronized to a WMS.

### Fixed zoom behavior

All wheel, +/- and pinch paths use the same bounded camera range. Wheel zoom is anchored at the pointer; +/- zoom around the camera center. Two-finger pan no longer accumulates camera-origin errors. A visibility safeguard recenters when all world objects leave the visible frame. If rendering fails, open **Debug 3D** and copy the report.

## What *world model* means here

The demonstration separates **spatial geometry** (buildings, roads, vehicles), **domain entities** (warehouses, trucks, forklifts, stock), **simulated state** (capacity, battery, deliveries, tasks) and **view state** (camera, selection, filters, simulation speed).

The three regions are a **synthetic network atlas**; they are not real georeferenced warehouse sites. Every operational value is demo data, and animated routes are simulated. This is not a live digital twin and is not connected to WMS, TMS, GPS, ERP or IoT telemetry.

## Controls

| | Desktop | Mobile |
|---|---|---|
| Orbit camera | Drag | One-finger drag |
| Pan camera | Shift + drag | Two-finger drag |
| Zoom | Wheel, +/− | Pinch, +/− |
| Inspect objects | Click | Tap, then Kho hàng panel |
| Navigate | A/B/C buttons, overview, minimap | Same |
| Debug | Debug 3D | Debug 3D |

If rendering fails, open **Debug 3D**, select **Kiểm tra GPU**, then **Sao chép báo cáo**.

## Next steps for a true digital twin

Connect real WMS/TMS/IoT event feeds with freshness indicators; add precise site floorplans and world coordinates; implement route planning/collision checks; introduce GPU instancing, frustum culling and LOD for larger scenes.

Changes pushed to `main` are deployed via `.github/workflows/pages.yml`.
