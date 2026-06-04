# AglandECON_USD — Agricultural Land Ecosystem Service Value

## File
`AglandECON_Yan.tif`

## Description
Spatially explicit total annual monetary value of four ecosystem services from agricultural land across Illinois. The raster is the cell-wise sum of food production, carbon sequestration, water regulation, and cultural services. Values are expressed in USD per cell per year.

## Specifications

| Property | Value |
|----------|-------|
| Units | USD per cell per year |
| CRS | NAD 1983 UTM Zone 16N (EPSG:26916) |
| Extent | Illinois land area only  |
| Resolution | 30 m × 30 m |
| Pixel Type | Float32 |
| Format | TIFF |

| Ecosystem Service | Annual Value | Share |
|------------------|-------------|-------|
| Food Production | $17,002,869,000 | ~72.1% |
| Water Regulation | $5,506,312,714 | ~23.3% |
| Cultural Services | $944,450,000 | ~4.0% |
| Carbon Sequestration | $131,032,000 | ~0.6% |
| **TOTAL** | **$23,584,663,714** | 100% |

## Components

The raster is the cell-wise sum of four ecosystem services:

| Service | Pathway | Statewide Total |
|---------|---------|-----------------|
| Food Production | Crop yield (ton/ha/yr) × market price (USD/ton); Corn $165/ton, Soybeans $375/ton, Wheat $199/ton (2024 USDA) | $17,002,869,000 |
| Water Regulation | SCS-CN reduced runoff (ES_water = P − Q) × stormwater replacement cost ($3.38/1,000 gal, central); 102 counties, 6,166,764,841 m³/yr retained | $5,506,312,714 |
| Cultural Services | Ag land area (22,486,764 acres) × unit value ($42/acre/yr); Aesthetic $23 + Recreation $19  | $944,450,000 |
| Carbon Sequestration | SOC stock change (BD × D × OC) × 3.67 tCO₂e/tC × $22/tCO₂e (SCC central) | $131,032,000 |

## Notes

- Carbon sequestration values are based on soil organic carbon (SOC) stock change estimates. Carbon price ($22/tCO₂e) is a reference value and may need updating to reflect current market rates.
- Cultural service unit values ($23/acre/yr aesthetic, $19/acre/yr recreation) are transferred from West Michigan cropland estimates (GVSU WRI); benefit transfer uncertainty applies. Cultural services are **not** spatially distributed at pixel level but allocated uniformly across all agricultural cells.
- Water regulation total is derived from county-level zonal statistics across 102 Illinois counties. Stormwater unit cost ($3.38/1,000 gal) is a central estimate and may need updating to reflect local rates.

## Provenance
Derived from crop production statistics (2024 USDA NASS) for food production, county-level SCS-CN runoff model outputs aggregated in `ZonalSt_water_v3` for water regulation, USDA NASS Cropland (2020) for carbon sequestration, and GVSU WRI regional valuation estimates for cultural services. Aggregation script sums all four service rasters cell-wise across the agricultural land mask.
