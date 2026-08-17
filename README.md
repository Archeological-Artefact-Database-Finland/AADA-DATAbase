# Archaeological Artefact Database of Finland (AADA)

> **Pesonen, P., Moilanen, U., Roose, M., Saipio, J., Tiilikkala, J., Sanwal, M. U., Immonen, V., Vesakoski, O. & Onkamo, P.** Archaeological Artefact Database of Finland (AADA). *Nature Scientific Data 11, 815 (2024).*

[![Article](https://img.shields.io/badge/Nature-Scientific_Data-blue)](https://doi.org/10.1038/s41597-024-03602-8)
[![Zenodo](https://img.shields.io/badge/Zenodo-10.5281%2Fzenodo.10437704-blue)](https://zenodo.org/records/10437704)
[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](LICENSE.md)

---

## Overview

The Archaeological Artefact Database of Finland (AADA) is a comprehensive, systematically structured repository of prehistoric artefacts recovered from Finnish museum collections. The database is organised thematically across three chronological periods the Stone Age, Bronze Age, and Iron Agee. Each row in the dataset represents a single artefact, while each column encodes a specific attribute, including typological classification, provenance, spatial coordinates, and physical measurements. An exception is made for pottery, where each row denotes the presence of a pottery type or style within a given collection accession number rather than an individual vessel.

The full methodological description of data collection and structure is provided in Pesonen et al. Nature Scientific Data 11, 815 (2024).

---

## Repository Structure

```
AADA-DATABase/
├── data-raw/
    └── master_data.csv          # Merged master table from all periods
│   ├── AADA_Bronze_Age/         # Per-category CSV files for the Bronze Age period
│   │   └── AADA_Bronze_Age_master.csv   # Merged master table for the Bronze Age
│   ├── AADA_Iron_Age/           # Per-category CSV files for the Iron Age period
│   │   └── AADA_Iron_Age_master.csv     # Merged master table for the Iron Age
│   ├── AADA_Stone_Age/          # Per-category CSV files for the Stone Age period
│   │   └── AADA_Stone_Age_master.csv    # Merged master table for the Stone Age
├── examples/                    # Annotated R scripts, TÄNNE TULISI SITTEN R-PAKETIN KÄYTTÖESIMERKKEJÄ NYKYISTEN LISÄKSI
├── LICENSE.md
└── README.md
```

The `data-raw/` directory constitutes the primary source of truth for all artefact data. Each period subdirectory contains the original per-category CSV files alongside a master CSV that consolidates all finds for that period. The master CSVs are intended for users who require a single flat file per chronological period and are directly usable in Python, Excel, or any other environment without requiring R.

---

## Data Access

### Stable releases (Zenodo)
Versioned snapshots of the dataset are archived in CERN's Zenodo repository and should be used for all citations in publications:

> [https://zenodo.org/records/10437704](https://zenodo.org/records/10437704)

### Photograph repository
Artefact photographs are maintained in a separate Zenodo repository:

> Moilanen, U., Pesonen, P., Saipio, J., Tiilikkala, J., Sanwal, M. 2024. *Archaeological Artefact Database of Finland (AADA), photograph repository.* [https://zenodo.org/records/10417384](https://zenodo.org/records/10417384)

### Development version (this repository)
This GitHub repository is the primary location for ongoing maintenance and versioning. CSV files can be downloaded directly from `data-raw/` for use in Python, Excel, or any other analytical environment without requiring R.

---

## Database Structure

### Chronological Periods and Artefact Categories

| Period | Artefact Categories |
|--------|-------------------|
| **Stone Age** (8900–1900 calBC) | Pottery, Stone tools, Clay artefacts, Bone artefacts, Wooden artefacts, Amber, Birch bark tar |
| **Bronze Age** (1900–500 calBC) | Pottery, Stone tools, Clay artefacts, Bone artefacts, Wooden artefacts, Bronze objects |
| **Iron Age** (500 calBC–1300 calAD) | Pottery, Stone tools, Clay artefacts, Bone artefacts, Wooden artefacts, Bronze artefacts, Iron artefacts, Silver and golden artefacts, Beads, Organic materials |

The Iron Age tables additionally include detailed sub-tables for pottery and stone tools in which dating is specified according to Iron Age sub-periods.

---

## Column Descriptions

### General and Spatial Information

| Column | Description |
|--------|-------------|
| `Collection` | Museum collection identifier (e.g., `KM` = Kansallismuseo / National Museum of Finland). See below for full list. |
| `Main number` | Diary accession number representing a single delivery of artefacts (e.g., an excavation). |
| `Sub-number` | Find context identifier within a main number accession. |
| `Municipality` | Place of origin, reflecting municipal boundaries as of 2020. Historic parish names are used for ceded Karelia and other pre-1945 territories. |
| `Site id` | Site identifier in accordance with the Register of Archaeological Sites (Finnish Heritage Agency). |
| `Site name` | Name of the find location. |
| `Phase` | Broad chronological period: `SA` (Stone Age), `BA` (Bronze Age), `IA` (Iron Age). |
| `p` | Coordinate northing, KKJ / Finland Uniform Coordinate System (EPSG:2393). |
| `i` | Coordinate easting, KKJ / Finland Uniform Coordinate System (EPSG:2393). |
| `z` | Elevation above sea level (m). |
| `X` | Latitude (WGS84). |
| `Y` | Longitude (WGS84). |

#### Museum Collection Codes

| Code | Local Name | English Name |
|------|-------------|--------------|
| KM | Kansallismuseo | National Museum of Finland |
| ÅM | Ålands Museum | Ålands Museum |
| TYA | Turun Yliopisto Arkeologia | University of Turku, Archaeology |
| TMM | Turun museokeskus | Turku Museum Centre (current signum TMK, dataset uses TMM) |
| SatM | Satakunnan Museo | Museum of Satakunta |
| KHMESIE | Kuopion kulttuurihistoriallinen museo | Kuopio Cultural History Museum |
| EKM | Etelä-Karjalan museo | Museum of South Karelia |
| BM | Porvoon Museo | Porvoo Museum (sw. Borgå Museum) |
| HM | Hämeen museo | Häme Museum, Museum Centre Vapriikki, Tampere |
| Hal | Halikon museo | Halikko Museum (part of Salo Historical Museum) |
| Per | Perniön museo | Perniö Museum (part of Salo Historical Museum) |
| Linder | Linder | Linder collections, Turku Museum Centre |
| Nyberg | Nyberg | Nyberg collections, EKTA Museum Raasepori |
| SII | Pöljän kotiseutumuseo | Curated by Kuopio Cultural History Museum |
| KARTT/VI | Karttulan kotiseutumuseo | Curated by Kuopio Cultural History Museum |
| KIUR | Kiuruveden museo | Kiuruvesi Museum, curated by Kuopio Cultural History Museum |
| Lauri Nautela kok | Lauri Nautela Museum | Lauri Nautela Museum, Lieto |
| SHH | Stockholm Historiska Museet | Swedish History Museum, Sweden |

### Temporal Information

Dating methodology varies by material type. For pottery, stone tools, clay artefacts, bronze and iron objects, and beads, dating is based on typological analysis. For amber, bone, birch bark, and wooden artefacts, datable associated finds from the same site are used as the primary dating criterion.

| Code | Period |
|------|--------|
| `m1` | Early Mesolithic: 8900–8200 BC |
| `m2` | Middle Mesolithic: 8200–6200 BC |
| `m3` | Late Mesolithic: 6200–5100 BC |
| `n1` | Early Neolithic: 5100–3900 BC |
| `n2` | Middle Neolithic: 3900–2900 BC |
| `n3` | Late Neolithic: 2900–2400 BC |
| `n4` | Final Neolithic: 2400–1700 BC |
| `p1` | Early Bronze Age (Montelius I–III): 1700–1100 BC |
| `p2` | Late Bronze Age (Montelius IV–VI): 1100–500 BC |
| `Mon1`–`Mon6` | Montelius Bronze Age sub-periods |
| `r1` | Early Iron Age (Pre-Roman through Late Roman): 500 BC–400 AD |
| `r2` | Late Iron Age (Merovingian through Medieval): 600–1530 AD |
| `Preroman IA` | Pre-Roman Iron Age: 500–1 BC |
| `Early Roman IA` | Early Roman Iron Age: 0–200 AD |
| `Late Roman IA` | Late Roman Iron Age: 200–400 AD |
| `Migration period` | 400–600 AD |
| `Merovingian period` | 600–800 AD |
| `Viking period` | 800–1050 AD |
| `Crusade period` | 1050–1150/1300 AD |

Note: The periodisation of the Late Iron Age is regionally variable. In eastern Finland and Karelia the Late Iron Age is generally extended to at least c. 1300 AD, and in some parts of northern Finland this extension is longer still.

### Typological Information

| Column | Description |
|--------|-------------|
| `Category` | Highest-level artefact classification (e.g., "Bronze artefacts"). |
| `Type` | Mid-level typological classification (e.g., "Bronze axe"). |
| `Type (Finnish)` | Type designation in Finnish. |
| `Subtype` | Finer typological classification (e.g., "Palstave"). |
| `Subtype (Finnish)` | Subtype designation in Finnish (e.g., "Olkakirves"). |
| `Subtype 2` | Lower-order subtype hierarchy, present for selected artefact classes (e.g., Stone Age stone tools). |
| `Subtype 2 (Finnish)` | Lower-order subtype in Finnish. |
| `Certainty` | Compiler's subjective confidence in typological identification: 1 = certain, 2 = probable, 3 = possible. |

### Physical Attributes

| Column | Description |
|--------|-------------|
| `Integrity` | Whether the artefact is intact (`TRUE`/`FALSE`). |
| `Length (mm)` | Length of intact artefact. |
| `Width (mm)` | Width of intact artefact. |
| `Thickness (mm)` | Thickness of intact artefact. |
| `Fragment length (mm)` | Length of fragment. |
| `Fragment width (mm)` | Width of fragment. |
| `Fragment thickness (mm)` | Thickness of fragment. |
| `Wall thickness 1–2 (mm)` | Pottery wall thickness measurements. |
| `Rim thickness 1–2 (mm)` | Pottery rim thickness measurements. |
| `Rock type (Finnish)` | Stone tool raw material (Finnish); based on rapid visual inspection and should be considered indicative only. |

### Pottery-Specific Attributes

| Column | Description |
|--------|-------------|
| `Main temper (Finnish)` | Primary temper material (Finnish); not to be taken as definitive. |
| `Other tempers (Finnish)` | Secondary temper materials (Finnish); not to be taken as definitive. |
| `Decoration` | Presence of decoration (`TRUE`/`FALSE`). |
| `Decoration elements (Finnish)` | Description of decorative elements (Finnish). |
| `Wave motif` | Presence of wave motif decoration. |
| `Grid motif` | Presence of grid motif decoration. |
| `Cord impression` | Presence of cord impression decoration. |
| `Crust` | Presence of food crusts on Iron Age pottery surfaces. In Stone and Bronze Age pottery, this information appears in the `Other notes` column in Finnish ("karsta"). |
| `Count 1–10` / `Count 10–100` / `Count >100` | Relative quantity of pottery sherds per collection number. |

### Site Context (Iron Age)

| Column | Description |
|--------|-------------|
| `Settlement site` | Artefact recovered from a settlement context. |
| `Cremation cemetery` | Artefact recovered from a cremation cemetery. |
| `Inhumation cemetery` | Artefact recovered from an inhumation cemetery. |
| `Cairn` | Artefact recovered from a cairn. |
| `Stray find` | Artefact recorded as a stray find. |
| `Hoard` | Artefact recovered from a hoard deposit. |
| `Other context` | Artefact from a context not covered by the above categories. |

### Photography

| Column | Description |
|--------|-------------|
| `PhotoID` | Unique artefact identifier formatted as `Collection` + `Main number` + `_` + `Sub-number` (e.g., `KM 12345_5`). Corresponds directly to filenames in the photograph repository. Multiple images of the same artefact are distinguished by appended letters (e.g., `KM 12345_5b.jpg`). |

Photographs are available in a separate Zenodo repository (Moilanen et al. 2024, see above). To link photographs to tabular data, users should download the photograph repository and follow the instructions provided in its accompanying README. Note that most pottery records do not have associated photographs due to the highly fragmented nature of the material.

### Other Notes

The `Other notes` column contains supplementary observations recorded in Finnish during data collection. These annotations are impressionistic in character and should not be treated as definitive information. No English translation is available.

---

## Known Limitations

- Approximately 45–50% of Finnish Iron Age material has not yet been incorporated into the database (excluding metal detector finds from the past two decades).
- Documentation of Stone Age stone tools is incomplete, particularly for small local museum collections and for material held at the National Museum of Finland acquired in the 1910s and 1920s. Similar gaps apply to parts of the Ålands Museum and Tampere Museum collections.
- Geographic coverage emphasises southern Finland, as data collection in 2020 was constrained by restrictions associated with the COVID-19 pandemic. Collections from museums in northern and eastern Finland were not studied during the initial phase.

---

## Citation

If you use AADA data in a publication, please cite both the dataset and the associated paper:

**Dataset:**
> Pesonen, P., Moilanen, U., Roose, M., Saipio, J., Tiilikkala, J., Sanwal, M. U., Immonen, V., Vesakoski, O. & Onkamo, P. *Archaeological Artefact Database of Finland (AADA).* Zenodo. [https://zenodo.org/records/10437704](https://zenodo.org/records/10437704)

**Paper:**
> Pesonen, P., Moilanen, U., Roose, M., Saipio, J., Tiilikkala, J., Sanwal, U., Immonen, V., Vesakoski, O. & Onkamo, P. 2024. Archaeological Artefact Database of Finland (AADA). *Manuscript submitted to Nature Scientific Data.*

---

## License

The AADA dataset is freely and openly available for non-commercial use, subject to attribution. See [LICENSE.md](LICENSE.md) for full terms.
