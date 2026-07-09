# 3D 山城互動地圖 — 大甲溪河階・山城五鄉鎮

**Live:** https://shou-li.github.io/shancheng-3d/

大甲溪中上游「山城五鄉鎮」（東勢・新社・石岡・和平・卓蘭）的 3D 地形互動地圖，作為文史教學與田野展示工具。範圍 120.76–120.99°E、24.13–24.38°N（約 23×28 km），高程 168–2447 m，DEM 網格 1800×2132（約 13 m）。

## 三種檢視

1. **等高線** — 地貌分層設色（hypsometric）＋東北低角度暈渲（凸顯大甲溪河階崖），可疊地名／道路／水文
2. **衛星** — Sentinel-2 無雲鑲嵌（EOX s2cloudless-2023）
3. **主題** — 灰階暈渲底圖＋可獨立開關圖層：農業用地、分棟建物、灌溉水圳、道路（含省道路徽）、廟宇（126）、農會（19）、農業資材行（136）

操作：左鍵旋轉、滾輪縮放、右鍵平移、雙擊飛至該點、滑鼠停留顯示海拔／坡度／經緯度。支援手機觸控（自動降採樣）。

## 資料來源

| 圖層 | 來源 |
|------|------|
| 高程 | AWS Terrain Tiles（Terrarium, z15） |
| 衛星 | EOX s2cloudless-2023 WMS |
| 農業用地／建物 | 內政部國土測繪中心 WMTS（LUIMAP01／BUILDX） |
| 灌溉水圳 | 農田水利署 灌排渠道系統圖 WMS |
| 道路／水文／聚落／廟宇／農會 | OpenStreetMap（Overpass API） |
| 農業資材行 | 葉守禮（2021）論文附錄「山城地區農業資材行列表」，Google Maps 地理編碼 |

圖資擷取時間：2026-07。

## 架構

單一自包含 `index.html`（約 7 MB）：Three.js r128 內嵌、DEM 以 base64 PNG 內嵌（R×256+G＝公尺）；衛星 `sat.jpg` 與四張主題疊圖 `th_*.png` 為外部檔案，切換至該模式才延遲載入。`preview.jpg` 為社群分享預覽圖。

產生器（`gen_shancheng.py`）與原始資料不在本 repo，由作者本機維護。

## 授權

- 地圖程式：© 葉守禮（Feng Chia University）× Claude，2026
- OpenStreetMap 資料 © OpenStreetMap contributors（ODbL）
- 國土測繪中心、農田水利署圖資依政府資料開放授權條款使用
- Sentinel-2 影像：Contains modified Copernicus Sentinel data；EOX s2cloudless（CC BY 4.0）
