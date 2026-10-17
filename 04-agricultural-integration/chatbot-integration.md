# Chatbot Integration Guide
*Surfacing water map data in agricultural advisory systems*

---

## The Problem

A farmer advisory chatbot can answer in the farmer's language. It can troubleshoot
crop disease, recommend planting dates, explain soil amendments. But it cannot answer:
"Where should I dig a well?" or "Will there be water at this location in dry season?"

Water mapping is the missing layer. This guide explains how to connect it.

---

## Two Integration Modes

### Mode 1 — Pre-computed Map Layer
The water map is computed offline (satellite + ground survey) and stored as a spatial
dataset. The chatbot queries the dataset when a water-location question is asked.

**Best for:** Areas with completed surveys. Fast response. Works offline.

**What the system needs:**
- A spatial dataset of candidate water sites with depth estimates and confidence levels
- A query layer that takes GPS coordinates and returns nearest candidate sites
- A plain-language formatter that translates technical output into something the farmer
  can act on ("There is a likely water source 200m north of your location, estimated
  depth 12-18m, medium confidence")

### Mode 2 — Survey Initiation Tool
The chatbot helps the farmer initiate a ground survey — gathering local knowledge,
marking candidate sites, and generating a survey brief for an extension worker.

**Best for:** Areas without completed surveys. The chatbot becomes the data collection
layer, not just the delivery layer.

**What the system needs:**
- A structured interview flow: "Where do you see green in dry season?" "Where do animals
  congregate when it hasn't rained?" "Where are the old wells?"
- GPS marking of mentioned locations
- A summary report generated for the extension worker

---

## Data Format

A simple GeoJSON layer works for both modes:

```json
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [36.8219, -1.2921]
      },
      "properties": {
        "site_id": "KE-LAI-001",
        "confidence": "medium",
        "estimated_depth_m": "12-18",
        "method": "satellite-ert",
        "seasonal": "perennial",
        "notes": "Linear NDVI anomaly confirmed by ERT profile"
      }
    }
  ]
}
```

---

## Farmer-Facing Language

Technical output needs translation. Examples:

| Technical | Farmer-facing |
|-----------|--------------|
| "High NDVI anomaly, SWIR moisture index elevated" | "The satellite shows this area stays green in dry season — usually means water underground" |
| "ERT profile shows low resistivity zone at 15m depth" | "The ground survey found what looks like water at about 15 meters down" |
| "Confidence: medium" | "We think there's a good chance — worth checking with a hand auger before committing to a full borehole" |
| "Seasonal — likely dry-season dependent" | "May only have water after the rains — check before planning year-round irrigation" |

---

## Local Language Considerations

The translation layer above needs localization. "Water underground" maps differently
across languages and cultures. In some contexts, traditional terms for water-bearing
formations exist and should be used.

If you are building this for a specific region, work with local language speakers to
ensure the terms land correctly. The farmer's confidence in the system depends on it
sounding like someone who understands the land, not a foreign instrument.
