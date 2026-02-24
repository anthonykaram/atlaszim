# Offline World Map for Kiwix (.ZIM)

![Offline World Map running fully offline in Kiwix](offline_world_map_demo.gif)

![Offline world map – global view](screenshot-world-map.png)
![Offline satellite imagery – global view](screenshot-world-satellite.png)

![Offline OpenStreetMap tiles – Tokyo](screenshot-tokyo-map.png)
![Offline satellite imagery – Tokyo](screenshot-tokyo-satellite.png)

Offline World Map is an **interactive offline world atlas** packaged as a single **ZIM file** for use with **Kiwix**.
It behaves like a website that works entirely offline: pan and zoom around the world, switch layers, and **search for places offline**.

This project demonstrates that the ZIM format can be used not only for wiki-style content, but also to deliver a fully interactive, pan-and-zoom map experience using standard web technologies.

---

## When to use this

Use Offline World Map when you want:

- A **fully offline** world map / digital atlas experience (no network required at runtime)
- A **single-file** map you can archive, copy, and share easily (`.zim`)
- An offline geographic reference that runs on platforms supported by **Kiwix** (desktop + mobile)
- Offline **place-name lookup/search** (GeoNames-backed)

Not intended for:

- Turn-by-turn navigation, routing, or directions
- Live traffic, real-time updates, or online map APIs
- Scenarios where you need frequently refreshed map data (this is an offline snapshot)

---

## What this is

The Offline World Map is a self-contained map application bundled inside a single `.zim` file.
When opened in Kiwix, it behaves like an offline website.

It includes:

- **OpenStreetMap-based raster map tiles**
- **Sentinel-2 cloudless satellite imagery**
- A **Leaflet**-based JavaScript map viewer
- An offline place search UI built with **Leaflet.Control.Search** and **GeoNames** data

---

## Why ZIM instead of traditional offline map formats?

Most offline maps are distributed as MBTiles, vector databases, or app-specific formats.
This project explores a different approach: using **ZIM as an offline web container**.

Advantages:

- **Single-file distribution**
- Works on all platforms supported by **Kiwix** (desktop and mobile)
- No dedicated map application required
- Easy to archive and share

---

## Features

- Global coverage
- Multiple zoom levels
- Map and satellite imagery layers
- Fully offline pan-and-zoom navigation
- Offline place search
- Runs entirely inside the Kiwix reader

---

## Design decisions

This project intentionally uses pre-rendered raster tiles rather than vector tiles.

While vector tiles can significantly reduce storage requirements, they shift cost to client-side computation (geometry decoding, rendering, memory usage), which is difficult to predict across the wide range of devices that run Kiwix.

By serving simple raster tiles from a ZIM file, the map remains lightweight to render and behaves consistently even on older or low-power devices. The large file size also acts as a natural capability filter: devices that can store tens of gigabytes of tiles almost certainly have sufficient CPU and RAM to handle raster rendering smoothly.

Additionally, because a substantial portion of the dataset is satellite imagery — which is inherently raster — vector tiles would not reduce total size as dramatically in this context. The goal is maximum compatibility and predictable performance rather than minimal disk usage.

---

## Downloads

The ZIM file is available here:

- **Gumroad:** [Offline World Map – ZIM file](https://anthonykaram.gumroad.com/l/offline_world_map)

---

## Videos

- **Demo of v5 (introduced search):** [Offline World Map for Kiwix (v5)](https://youtu.be/hfey3ogmVC8)
- **Demo of v4 (added Leaflet navigation):** [Offline World Map for Kiwix (v4)](https://youtu.be/XYoBKyg8tH4)
- **Demo of v1 (initial release):** [Offline World Map for Kiwix (v1)](https://youtu.be/5qq_W7qMxxs)

---

## Data sources, licensing, and attribution

This project is a compilation and packaging effort. Individual components are licensed separately:

- **OpenStreetMap** data © OpenStreetMap contributors (ODbL)
- **Satellite imagery:** Sentinel-2 cloudless (CC BY 4.0, EOX IT Services GmbH)
- **Place search data:** GeoNames (CC BY 4.0)
- **Leaflet** © Vladimir Agafonkin and contributors (BSD 2-Clause)
- **Leaflet.Control.Search** (MIT-style license)

Compilation, integration, and packaging © Anthony Karam.

---

## Project metadata

- **Project name:** Offline World Map
- **Format:** ZIM file
- **Platform:** Kiwix (desktop and mobile)
- **Category:** Offline maps / geographic reference / digital atlas
- **Technologies:** Leaflet, OpenStreetMap, Sentinel-2, GeoNames
- **Author:** Anthony Karam
- **Canonical URL:** https://anthonykaram.github.io/offline-world-map/
