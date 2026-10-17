# Groundwater Mapping Toolkit

**Open-source tools for subsurface water detection, mapping, and agricultural planning.**

*Published by Lucent Labs | 2026-10-16 | CC0 — Public Domain*

---

## What This Is

Smallholder farmers need to know where water is. Aquifer mapping has historically required
expensive equipment, government surveys, or large NGO projects. That access gap is solvable
with open satellite data, electrical resistivity methods, and the kind of systematic survey
methodology that was developed for large institutions but works just as well at village scale.

This toolkit is designed to plug directly into agricultural advisory systems — including
farmer chatbots operating in local languages — so that water source mapping becomes an
actionable layer for the farmer, not just a research output.

---

## What's In Here

```
groundwater-mapping-toolkit/
├── 01-satellite-survey/            # Remote sensing — where to look before you dig
│   ├── README.md                   # How satellite data reveals surface expressions of subsurface water
│   ├── sentinel-2-guide.md         # Free ESA imagery — bands, resolution, access
│   ├── anomaly-detection.md        # What to look for: NDVI anomalies, drainage patterns, lineaments
│   ├── dem-analysis.md             # Digital elevation models — flow accumulation, watershed delineation
│   └── interpretation-guide.md    # Going from satellite signature to candidate site
│
├── 02-ground-survey/               # Field methods — validating what the satellite suggested
│   ├── README.md
│   ├── ert-method.md               # Electrical Resistivity Tomography — the core ground method
│   ├── ves-method.md               # Vertical Electrical Sounding — simpler, lower cost
│   ├── equipment-guide.md          # What equipment is needed, cost ranges, rental vs. build
│   └── survey-protocols.md        # Step-by-step field survey procedure
│
├── 03-data-processing/             # Turning field data into a map
│   ├── README.md
│   ├── open-source-tools.md        # QGIS, SAGA, Res2DInv alternatives, Python stack
│   ├── resistivity-inversion.md    # How to interpret resistivity profiles
│   └── uncertainty.md             # Being honest about what the map does and does not show
│
├── 04-agricultural-integration/    # Making the map useful for farmers
│   ├── README.md
│   ├── water-table-depth.md        # Translating depth estimates to borehole planning
│   ├── seasonal-variation.md       # Aquifer behavior through dry/wet seasons
│   ├── crop-water-matching.md      # Matching water availability to crop selection
│   └── chatbot-integration.md     # How to surface water map data in an advisory system
│
├── 05-community-survey-design/     # Running a survey with and for a community
│   ├── README.md
│   ├── participatory-methods.md    # Local knowledge as a primary input
│   ├── data-sovereignty.md         # Who owns the map; community data governance
│   └── cost-sharing-models.md     # How to structure a community survey without dependency
│
├── 06-case-studies/
│   ├── README.md
│   └── kenya-laikipia/            # Corridor mapping methodology — satellite scan approach
│       └── methodology.md
│
└── resources/
    ├── glossary.md
    ├── open-data-sources.md        # SRTM, Copernicus, GRACE groundwater anomaly data
    └── learning-path.md
```

---

## Who This Is For

- Agricultural extension workers who need to advise on water access
- Community-level organizations planning boreholes or wells
- Farmers working with advisory systems who need localized water data
- Developers building agricultural chatbots who need a water-layer tool
- Regional governments running sovereign agricultural infrastructure

---

## The Integration Problem This Solves

A farmer chatbot that can troubleshoot crop disease, recommend planting schedules, and
explain soil amendments in the farmer's own language still cannot tell the farmer where
water is or whether a borehole will yield at a given site.

Water mapping has been the missing infrastructure layer for agricultural advisory systems.
This toolkit is designed to be called by those systems — either as a planning tool for
extension workers or as a data layer surfaced directly to farmers.

---

## Methods

### Primary: Satellite Pre-Survey
Free ESA Sentinel-2 imagery combined with SRTM or Copernicus DEM data for:
- NDVI anomaly detection (vegetation responding to subsurface moisture)
- Drainage network and watershed delineation
- Lineament mapping (faults and fractures that channel groundwater)
- Soil moisture indices (SWIR band ratios)

This narrows the candidate zone before any ground equipment is deployed.

### Secondary: Electrical Resistivity Survey
Resistivity contrasts between dry rock, saturated rock, and clay allow subsurface
imaging without drilling. Two accessible approaches:
- **VES (Vertical Electrical Sounding):** Low equipment cost, one-dimensional profile, identifies depth to water table
- **ERT (Electrical Resistivity Tomography):** More equipment, two-dimensional cross-section, better for complex geology

Both can be performed with equipment buildable for under $2,000 or rentable through
regional geological survey agencies.

### Tertiary: Community Knowledge Integration
Local knowledge of seasonal springs, traditional wells, dry-season water points, and
animal behavior (where livestock congregate in dry season) is a primary data source.
This is not supplementary — it is often the most precise information available about
seasonal and perennial water behavior in a specific location.

---

## Data Sources (All Free)

| Dataset | What It Provides | Source |
|---------|-----------------|--------|
| Sentinel-2 | 10m multispectral imagery, 5-day revisit | ESA Copernicus / Google Earth Engine |
| SRTM | 30m global elevation model | NASA / USGS Earth Explorer |
| Copernicus DEM | 30m global elevation, higher quality | ESA Copernicus |
| GRACE-FO | Monthly groundwater storage anomalies (~300km resolution) | NASA / GFZ |
| ALOS PALSAR | SAR — penetrates cloud cover, sees soil moisture | JAXA (free registration) |
| Global Surface Water | 30-year water presence/absence | JRC / Google Earth Engine |

All free. All accessible with a browser and a free account.

---

## License

All original content: **Creative Commons Zero (CC0)**. No rights reserved.

Use it, adapt it, build it into your system. The only thing we ask (not legally require):
if you use this with a community, make sure the community has the map.

---

## Contributing

Open an issue. Open a PR. Especially looking for:
- Case studies from specific regions
- Lower-cost equipment builds
- Integration examples with agricultural advisory systems
- Translations of the farmer-facing content

---

*Lucent Labs | lucent.social*
