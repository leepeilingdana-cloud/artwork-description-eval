# Artwork Description Evaluation — Pilot Study

This repository contains a pilot implementation of the claim-based evaluation framework proposed in my IMPRS-MDH research application.

## Research Question

When a multimodal AI system generates a description of a cultural heritage object, can its claims be traced back to available evidence — visual, metadata, or scholarly — or do they rest on unverifiable inference?

## Four Artworks

| Artwork | Artist | Year | Selection Rationale |
|---|---|---|---|
| The Calling of Saint Matthew | Caravaggio | 1600 | High documentation, Western canon |
| Trinity | Andrei Rublev | 1411 | Non-Western image tradition |
| The School of Athens | Raphael | 1511 | Complex spatial structure |
| Palazzo Farnese (archival photo) | Unknown | c.1920 | Low documentation, archival image |

## Annotation Scheme

Each description is segmented into claim units and annotated across four dimensions:

- **claim_type**: VISUAL / HISTORICAL / INTERPRETIVE / ATTRIBUTIVE
- **evidence_source**: IMAGE_VISIBLE / METADATA / SCHOLARLY / UNTRACED
- **accuracy**: GROUNDED / PLAUSIBLE / HALLUCINATED / OMISSION
- **hedging**: HEDGED / UNHEDGED

## Key Finding

The pilot annotated 56 claim units across four artworks. The Palazzo Farnese archival photograph — the least documented object in the set — showed the highest proportion of UNTRACED evidence, consistent with the hypothesis that AI-generated descriptions of less-documented cultural objects rely more heavily on unverifiable inference. Full study will use model-generated outputs directly to test this pattern at scale.

## Structure

- `01_data_collection.ipynb` — artwork metadata, image collection, description generation
- `02_annotation.ipynb` — claim segmentation and annotation
- `03_analysis.ipynb` — quantitative analysis and visualizations
- `data/annotation_template.csv` — full annotated dataset