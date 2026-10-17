# Sentinel-2 Satellite Survey Guide
*For groundwater candidate site identification*

---

## Why Sentinel-2

Free. Global coverage. 10m resolution for key bands. 5-day revisit cycle.
Available through ESA Copernicus, Google Earth Engine, and Copernicus Browser — no account
required for basic access, free registration for bulk download.

This is the starting point for any groundwater survey. Before any ground equipment is
deployed, satellite analysis narrows the candidate zone.

---

## The Bands That Matter for Water

| Band | Wavelength | Resolution | Use |
|------|-----------|-----------|-----|
| B2 (Blue) | 490nm | 10m | Baseline, water body detection |
| B3 (Green) | 560nm | 10m | Vegetation health |
| B4 (Red) | 665nm | 10m | NDVI (with B8) |
| B8 (NIR) | 842nm | 10m | NDVI, moisture |
| B11 (SWIR-1) | 1610nm | 20m | Soil moisture, NDWI |
| B12 (SWIR-2) | 2190nm | 20m | Dry soil / mineral mapping |

---

## Key Indices

### NDVI (Normalized Difference Vegetation Index)
```
NDVI = (B8 - B4) / (B8 + B4)
```
Range: -1 to +1. Healthy vegetation: 0.3–0.8.

**Groundwater signature:** Anomalously high NDVI in dry season, in zones where no surface water exists, often indicates shallow water table supporting vegetation. Linear NDVI anomalies often follow fractures or paleochannels carrying subsurface water.

### NDWI (Normalized Difference Water Index)
```
NDWI = (B3 - B8) / (B3 + B8)   # Surface water
NDWI2 = (B8 - B11) / (B8 + B11)  # Soil/vegetation moisture
```

### SWIR Ratio (Soil Moisture)
```
Soil Moisture Index = B8 / B11
```
Lower values = higher moisture content in soil.

---

## Access — Three Ways

### 1. Copernicus Browser (easiest, no code)
https://browser.dataspace.copernicus.eu/
- Draw area of interest
- Select date range (get dry season for clearest groundwater signal)
- Download true color or calculated indices directly

### 2. Google Earth Engine (best for time series, requires free account)
```javascript
var sentinel = ee.ImageCollection('COPERNICUS/S2_SR_HARMONIZED')
  .filterDate('2024-01-01', '2024-04-30')  // dry season
  .filterBounds(geometry)
  .filter(ee.Filter.lt('CLOUDY_PIXEL_PERCENTAGE', 10))
  .median();

var ndvi = sentinel.normalizedDifference(['B8', 'B4']).rename('NDVI');
```

### 3. USGS Earth Explorer (bulk download)
https://earthexplorer.usgs.gov/ — free registration, good for full scene downloads.

---

## What to Look For

1. **Dry-season NDVI anomalies** — green in places that should be brown
2. **Linear features** — straight or slightly curved high-NDVI lines often follow faults
3. **Topographic convergence zones** — valleys, depressions where flow accumulates
4. **Soil tone anomalies** — darker soil in dry season = retained moisture
5. **Drainage network terminations** — where surface drainage disappears underground

---

## Ground Truth

Every satellite candidate needs ground confirmation. The satellite tells you where to look.
The ground survey tells you whether water is actually there and at what depth.
