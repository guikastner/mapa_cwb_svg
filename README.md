# Curitiba SVG Map

This project contains a vector map of Curitiba in SVG format and a derived version adapted for technical use in web applications, interactive visualizations, and data-driven interfaces.

The map represents the administrative division of the city, including administrative regions and neighborhoods drawn as vector polygons. The purpose of the project is to turn that graphic asset into something easier to consume programmatically, without depending on labels rendered directly on the map.

## Project Goal

The main goal of this project is to provide an SVG map of Curitiba that can be used as a code-friendly graphical asset.

In practice, this makes it possible to:

- identify neighborhoods by SVG element `id`;
- apply different styles to each region;
- add interactions such as hover, click, tooltip, and highlight behavior;
- bind external indicators, statistics, or metadata to specific neighborhoods;
- reuse the map in dashboards, public portals, administrative panels, or geovisualization projects.

The derived SVG version was created specifically for that purpose: replacing visual text labels with structured identifiers on the map elements.

## Files

- `Divisao_administrativa_Curitiba.svg`
  Original map file, containing the region and neighborhood polygons as well as the visible text labels rendered in the artwork.

- `Divisao_administrativa_Curitiba_bairros_ids.svg`
  Derived map version where text labels were removed and neighborhood polygons received descriptive `id` values in `snake_case`.

## ID Convention

In `Divisao_administrativa_Curitiba_bairros_ids.svg`, neighborhoods were assigned ASCII-only `snake_case` IDs.

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

## Important Note

The neighborhood `id` mapping was generated automatically based on label positions in the original SVG. This provides good confidence, but it does not replace a final visual review if the file will be used in production, publication, or any critical integration.

## Suggested Uses

The `Divisao_administrativa_Curitiba_bairros_ids.svg` file is useful for:

- styling neighborhoods individually with CSS or JavaScript;
- adding interactivity through element IDs;
- linking external datasets to each neighborhood;
- building map-based dashboards and visual interfaces.
