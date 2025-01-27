# gsi-terrain-dem-on-maplibre-gl-js-demo
## Public Website
https://shiwaku.github.io/gsi-terrain-dem-on-maplibre-gl-js-demo/

## 標高タイルをTerrainRGBに変換するモジュールの使い方
- index.htmlのheadに変換モジュール(maplibre-gl-gsi-terrain-fast-png.js)の読み込みを記述します。
```
<html>

<head>
    <title>国土地理院 標高タイル（DEM10B）</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src='https://unpkg.com/maplibre-gl@3.4.1/dist/maplibre-gl.js'></script>
    <link href='https://unpkg.com/maplibre-gl@3.4.1/dist/maplibre-gl.css' rel='stylesheet' />
    <script src="https://unpkg.com/pmtiles@2.10.0/dist/index.js"></script>
    <script type="module" src="maplibre-gl-gsi-terrain-fast-png.js"></script>
```
- index.htmlのmap.addSourceのtilesを下記のとおりにします。
- `gsidem://https://cyberjapandata.gsi.go.jp/xyz/dem_png/{z}/{x}/{y}.png`とすることで、標高タイルがTerrain-RGB形式に変換されます。
```
            map.addSource("gsidem", {
                type: 'raster-dem',
                tiles: [
                    'gsidem://https://cyberjapandata.gsi.go.jp/xyz/dem_png/{z}/{x}/{y}.png',
                ],
                attribution: '<a href="https://maps.gsi.go.jp/development/ichiran.html#dem" target="_blank">地理院タイル(標高タイル)</a>',
                tileSize: 256
            });
```
