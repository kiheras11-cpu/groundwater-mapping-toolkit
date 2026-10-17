# Kenya Corridor — Groundwater Survey Methodology
*Case study: Laikipia Plateau + Kirinyaga region*
*Lucent Labs internal methodology reference | 2026-10-16*

---

## Overview

The East Africa corridor study (research/east-africa-corridor/) produced a satellite
scan methodology over six Sentinel-2 scenes covering the Laikipia Plateau, Kirinyaga,
Eldoret, Cherangani, and Turkana regions. The methodology applied here to groundwater
mapping follows the same satellite-first approach.

---

## Methodology Used

### Phase 1 — Sentinel-2 Baseline
- Six scenes, dry-season imagery (minimizes cloud cover, maximizes soil moisture signal)
- Consistent 5.0° near-cardinal orientation anomalies across all scans
- NDVI analysis for vegetation anomalies in expected dry zones
- SWIR ratio for subsurface moisture indicators
- DEM-derived drainage network and flow accumulation

### Phase 2 — Anomaly Classification
Anomalies classified by:
- Spatial coherence (how consistent is the signature across multiple dates)
- Shape (linear = fracture/fault control; circular = solution feature; irregular = paleochannel)
- Orientation (consistent orientation across a region = structural control)

Laikipia result: coherence 0.50 (highest of all scans). 80.7ha feature near Namoratunga
with aspect ratio 1.00 — consistent with a structurally controlled water-bearing formation.

### Phase 3 — Ground Truth Protocol (pending)
- Hand auger at 2-3 highest-confidence sites
- VES survey at Namoratunga anomaly (equipment: ABEM Terrameter or equivalent)
- Community knowledge integration: water-keeper oral tradition active in the Wanyua clan

### Local Knowledge Integration
The Wanyua clan (Emmanuel's matrilineal lineage) are documented water-keepers —
the clan name encodes an active relationship to water sources ("she drinks" — not
a noun but a verb, a living practice). This oral tradition is a primary data source
for water site identification, not supplementary.

---

## Applicability to Agricultural Planning

The Laikipia corridor runs through active smallholder farming zones. A groundwater
map derived from the satellite scan + VES survey would provide:
- Candidate borehole sites with depth estimates
- Seasonal vs. perennial water source classification
- Water table depth variation across the corridor

This feeds directly into the sovereign farmer chatbot infrastructure — water source
data as a queryable layer in the advisory system.
