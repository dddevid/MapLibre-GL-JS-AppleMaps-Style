# MapLibre GL JS — Apple Maps Dark Style

A pixel-faithful recreation of **Apple Maps dark mode** as a [MapLibre GL JS](https://maplibre.org/) style, powered by free and open tile data from [OpenFreeMap](https://openfreemap.org/).

![Preview](https://raw.githubusercontent.com/dddevid/MapLibre-GL-JS-AppleMaps-Style/main/preview.png)

---

## ✨ Features

- **Dark palette** — deep charcoal backgrounds with carefully tuned land-use, water, and vegetation tones
- **Layered road rendering** — all casings drawn before fills, ensuring clean junctions and correct z-ordering across all road classes (motorway → trunk → primary → secondary → minor → service)
- **Round caps & joins** — smooth road terminations and curves at every zoom level
- **3D buildings** — fill-extrusion layer kicks in at zoom 15 with subtle height variation
- **Inter typeface** — clean, modern labels using the Inter font family
- **Full POI coverage** — parks, transit hubs, and general points of interest with class-specific colours
- **No external dependencies** — tiles, glyphs, and sprites all served from OpenFreeMap's CDN

---

## 🚀 Quick Start

### Via URL

Point your MapLibre GL JS instance directly at the raw file:

```js
import maplibregl from 'maplibre-gl';

const map = new maplibregl.Map({
  container: 'map',
  style: 'https://raw.githubusercontent.com/dddevid/MapLibre-GL-JS-AppleMaps-Style/main/apple-maps-dark.json',
  center: [9.18, 45.46], // Milan
  zoom: 12,
});
```

### Local copy

```bash
git clone https://github.com/dddevid/MapLibre-GL-JS-AppleMaps-Style.git
```

Then reference the file locally:

```js
import style from './MapLibre-GL-JS-AppleMaps-Style/apple-maps-dark.json';

const map = new maplibregl.Map({
  container: 'map',
  style,
});
```

---

## 📁 Repository Structure

```
MapLibre-GL-JS-AppleMaps-Style/
└── apple-maps-dark.json   # The complete MapLibre GL JS style spec
```

---

## 🗺️ Data Sources

| Resource | Provider |
|----------|----------|
| Vector tiles | [OpenFreeMap](https://openfreemap.org/) (`planet` schema) |
| Glyphs (fonts) | `tiles.openfreemap.org/fonts` |
| Sprites | `tiles.openfreemap.org/natural_earth` |

All sources are **free to use** with no API key required.

---

## 🎨 Style Overview

### Layer categories

| Category | Layers |
|----------|--------|
| Base & land | Background, landcover (ice, sand, grass, wood, wetland), landuse (residential, commercial, industrial, park, hospital, school, cemetery, military) |
| Water | Fill, outline, waterways (rivers, canals, streams) |
| Infrastructure | Aeroway (apron, runway, taxiway), buildings (flat + 3D extrusion) |
| Roads | Path, service, minor, secondary, tertiary, primary, trunk, motorway — each with a dedicated casing layer |
| Rail | Line + cross-hatching |
| Boundaries | Country (bg + line), state/region |
| Labels | Countries, states, cities (large/medium/small), towns, villages, water bodies, road names, POIs |

### Road rendering order

Roads follow the **casing-first pattern** — all casing layers are rendered before all fill layers, from lowest to highest road class. This ensures that motorway fills always sit cleanly on top at complex interchanges.

```
[all casings: service → minor → secondary → primary → trunk → motorway]
[all fills:   service → minor → secondary → primary → trunk → motorway]
```

---

## 🛠️ Customisation

The style is a plain JSON file — open it in any text editor or paste it into the [MapLibre Style Editor](https://maplibre.org/maputnik/) for live editing.

Common tweaks:

- **Colours** — search for hex values in the `paint` blocks
- **Road widths** — adjust the `line-width` interpolation stops in each road layer
- **Fonts** — replace `Inter Bold / Inter Regular / Inter Italic` with any font available on your glyph server
- **Zoom ranges** — tweak `minzoom` / `maxzoom` on any layer

---

## 📋 Requirements

- **MapLibre GL JS** v3 or later
- A modern browser with WebGL support

---

## 📄 License

Released under the [MIT License](LICENSE). The underlying tile data is provided by OpenFreeMap under its own open terms — see [openfreemap.org](https://openfreemap.org/) for details.

---

## 🙏 Acknowledgements

- [MapLibre GL JS](https://maplibre.org/) — the open-source WebGL map renderer
- [OpenFreeMap](https://openfreemap.org/) — free vector tiles, glyphs, and sprites
- [OpenStreetMap contributors](https://www.openstreetmap.org/copyright) — the underlying geodata

---

<p align="center">Made with ♥ by <a href="https://github.com/dddevid">dddevid</a></p>
