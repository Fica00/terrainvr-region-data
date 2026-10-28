# Terrain VR region data

Data pack for the Terrain VR app (Meta Quest): 3D trees, buildings, rivers and lakes for the walkable region around Tawang, Bomdila, Cona and Sakteng (91.70–92.60 E, 27.10–28.25 N), as 713 binary region tiles.

The app downloads this pack by itself on first start. This repository holds only the data, not the app.

## Releases

Each release is named after the tile format version that app builds read, so an app only downloads tiles it can read.

| Release | Read by | Data version | Notes |
|---|---|---|---|
| `region-v10` | app builds w30 and later | 2026-10-28-w30-buildings-rivers | About 11% more buildings (106,983): OSM aligned to Open Buildings before merging, huts from 8 m², gaps filled from the East Asia building dataset and Microsoft ML footprints, heights over 20 m from storey counts. 2.04 GB zipped in 6 parts, 2.61 GB unpacked |
| `region-v9` | app builds w29 | 2026-10-28-w29-flat-lakes | Flat lakes: one level per lake from Cesium shore samples, shore skirts, `lake_levels.json` (outlines and levels) so the app lowers the terrain inside each lake; river ribbons with skirts that stop inside lakes. 2.03 GB zipped in 6 parts, 2.58 GB unpacked |
| `region-v8` | app builds w28 | 2026-10-28-w28 | Door stairs reach the ground: 18 cm risers counted from the ground under each tread, turning along the wall when a straight flight would need more than 14 steps. Trees as in v7. 2.03 GB zipped in 6 parts, 2.57 GB unpacked |
| `region-v7` | app builds w27 | 2026-10-27-tree-kinds | Nine tree kinds by altitude band and forest type, a colour tint per tree, per-town roof colours. 1.92 GB zipped in 6 parts, 2.37 GB unpacked |
| `region-v6` | app builds w25 and w26 | 2026-10-27-draped-lakes | Lake surfaces follow the shore and the ground inside each lake, a landing and a deep stair base at every door. 1.74 GB zipped, 2.18 GB unpacked |
| `region-v5` | app builds w24 | 2026-10-27 | First release. 1.73 GB zipped, 2.14 GB unpacked |

Each release has:

| File | Contents |
|---|---|
| `manifest.json` | Data version, tile format version, every part with its size and SHA-256, and every file with its size and SHA-256 |
| `region-v<N>-part1.zip` … (5 or 6 parts) | The tiles (`tile_<c>_<r>.rtl`), `index.json`, `lakes.json` and (from v9) `lake_levels.json` |

To install by hand instead (developer mode and adb), unzip all parts into one folder and copy it to the headset:

```
adb shell mkdir -p /sdcard/Android/obb/com.filipk.terrainvrpoc/region
adb push region/. /sdcard/Android/obb/com.filipk.terrainvrpoc/region/
```

## Sources and licence

Buildings, roads, rivers, lakes and land cover come from OpenStreetMap: © OpenStreetMap contributors. The OSM-derived data is available under the Open Database License (ODbL) 1.0, https://opendatacommons.org/licenses/odbl/ . See https://www.openstreetmap.org/copyright .

Tree positions and heights: Meta / WRI High Resolution Canopy Height (CC BY 4.0) and ESA WorldCover 2021 (CC BY 4.0). Tree kinds (from v7): Copernicus Global Land Service CGLS-LC100 Collection 3, 2019 (CC BY 4.0). Tree colours (from v7): ESA WorldCover 2021 Sentinel-2 RGBNIR composite, contains modified Copernicus Sentinel data 2021 (CC BY 4.0). Building footprints: Google Open Buildings v3 (CC BY 4.0) and OpenStreetMap; where neither has a building (from v10): Shi, Q. et al. (2023), "A first high-quality vector data of buildings in East Asian countries", Zenodo, https://doi.org/10.5281/zenodo.8174931 (CC BY 4.0), and Microsoft Global ML Building Footprints (ODbL), both read from the Overture Maps Foundation buildings release.

Building heights use Google Open Buildings 2.5D Temporal where it covers the area (CC BY 4.0). Ground heights were sampled from Cesium World Terrain when the tiles were made.

This database is made available under the Open Database License: http://opendatacommons.org/licenses/odbl/1.0/.
