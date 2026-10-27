# Terrain VR region data

Data pack for the Terrain VR app (Meta Quest): 3D trees, buildings, rivers and lakes for the walkable region around Tawang, Bomdila, Cona and Sakteng (91.70–92.60 E, 27.10–28.25 N), as 698 binary region tiles.

The app downloads this pack by itself on first start. This repository holds only the data, not the app.

## Release `region-v5`

| File | Contents |
|---|---|
| `manifest.json` | Data version, tile format version (5), every part with its size and SHA-256, and every file with its size and SHA-256 |
| `region-v5-part1.zip` … `region-v5-part5.zip` | The tiles (`tile_<c>_<r>.rtl`), `index.json` and `lakes.json`, about 1.7 GB zipped, 2.1 GB unpacked |

To install by hand instead (developer mode and adb), unzip all parts into one folder and copy it to the headset:

```
adb shell mkdir -p /sdcard/Android/obb/com.filipk.terrainvrpoc/region
adb push region/. /sdcard/Android/obb/com.filipk.terrainvrpoc/region/
```

## Sources and licence

Buildings, roads, rivers, lakes and land cover come from OpenStreetMap: © OpenStreetMap contributors. The OSM-derived data is available under the Open Database License (ODbL) 1.0, https://opendatacommons.org/licenses/odbl/ . See https://www.openstreetmap.org/copyright .

Building heights use Google Open Buildings 2.5D Temporal where it covers the area (CC BY 4.0). Ground heights were sampled from Cesium World Terrain when the tiles were made.

This database is made available under the Open Database License: http://opendatacommons.org/licenses/odbl/1.0/.
