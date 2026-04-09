# Curitiba SVG Map

This project contains a vector map of Curitiba in SVG format and derived versions adapted for technical use in web applications, interactive visualizations, and data-driven interfaces.

The map represents the administrative division of the city, including administrative regions and neighborhoods drawn as vector polygons. The purpose of the project is to turn that graphic asset into something easier to consume programmatically, without depending on labels rendered directly on the map.

## Project Goal

The main goal of this project is to provide an SVG map of Curitiba that can be used as a code-friendly graphical asset.

In practice, this makes it possible to:

- identify neighborhoods by SVG element `id`;
- apply different styles to each region;
- add interactions such as hover, click, tooltip, and highlight behavior;
- bind external indicators, statistics, or metadata to specific neighborhoods;
- reuse the map in dashboards, public portals, administrative panels, or geovisualization projects.

The derived SVG versions were created specifically for that purpose: replacing visual text labels with structured identifiers on the map elements and providing a neutral visual base for reuse.

## Files

- `Divisao_administrativa_Curitiba.svg`
  Original map file, containing the region and neighborhood polygons as well as the visible text labels rendered in the artwork.

- `Divisao_administrativa_Curitiba_bairros_ids.svg`
  Derived map version where text labels were removed and neighborhood polygons received descriptive `id` values in `snake_case`.

- `Divisao_administrativa_Curitiba_bairros_ids_gray.svg`
  Derived map version with the same neighborhood IDs, no text labels, and a uniform light gray fill applied across the map.

## Current Deliverables

The repository currently provides three practical map variants:

- the original labeled SVG;
- an unlabeled SVG with neighborhood IDs;
- an unlabeled SVG with neighborhood IDs and a uniform light gray visual style.

This makes it possible to choose between preserving the original artwork and using a cleaner technical asset for code-driven styling and interaction.

## ID Convention

In `Divisao_administrativa_Curitiba_bairros_ids.svg` and `Divisao_administrativa_Curitiba_bairros_ids_gray.svg`, neighborhoods were assigned ASCII-only `snake_case` IDs.

Examples:

- `caximba`
- `campo_de_santana`
- `cidade_industrial`
- `agua_verde`
- `alto_da_rua_xv`

In addition to the `id`, each neighborhood also includes a `data-bairro` attribute with the original human-readable name, including accents when applicable.

Example:

```xml
<path id="agua_verde" data-bairro="Água Verde" ... />
```

## How the Mapping Was Created

The derived file was generated from the original SVG using the following process:

1. Read the neighborhood labels present in the original map.
2. Geometrically identify which polygon contains each label.
3. Rename the corresponding `path` element with the neighborhood name.
4. Remove all `<text>` elements from the final SVG.

The resulting neighborhood map includes:

- `75` neighborhood polygons with mapped IDs;
- a `data-bairro` attribute for each mapped neighborhood;
- no visible text labels in the derived outputs.

## Gray Version

The `Divisao_administrativa_Curitiba_bairros_ids_gray.svg` file was created from the ID-based version as a neutral presentation layer.

Its purpose is to provide a clean default map that can be restyled later with CSS, JavaScript, or external data bindings.

Characteristics:

- all mapped neighborhoods use the same light gray fill color: `#d9d9d9`;
- neighborhood IDs and `data-bairro` attributes are preserved;
- text labels remain removed;
- auxiliary colored shapes that remained from the original artwork were also normalized to the same gray tone.

## Important Note

The neighborhood `id` mapping was generated automatically based on label positions in the original SVG. This provides good confidence, but it does not replace a final visual review if the file will be used in production, publication, or any critical integration.

The mapping process produced a one-to-one result between detected neighborhood labels and renamed polygons, but the final semantic correctness of every neighborhood should still be visually verified if strict accuracy is required.

## Suggested Uses

The derived SVG files are useful for:

- styling neighborhoods individually with CSS or JavaScript;
- adding interactivity through element IDs;
- linking external datasets to each neighborhood;
- building map-based dashboards and visual interfaces.

Typical usage patterns include:

- choropleth-style highlighting by neighborhood;
- hover and click interactions in municipal dashboards;
- filtering neighborhoods by external indicators;
- using the gray base SVG as a neutral thematic layer before applying runtime colors.
