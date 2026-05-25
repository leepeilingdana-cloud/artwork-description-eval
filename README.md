# Artwork Description Evaluation — Pilot Study

A pilot implementation of the claim-based evaluation framework proposed in my
IMPRS-MDH (Multimodal Digital Humanities, UZH / Bibliotheca Hertziana) research
application.

## Research question

When a multimodal AI system generates a description of a cultural heritage
object, can its individual claims be traced back to available evidence —
**visual, metadata, or scholarly** — or do they rest on unverifiable inference?

## Approach

The framework treats the individual **claim**, not the whole description, as the
unit of analysis. Each AI-generated description is segmented into claim units,
and every claim is annotated along four dimensions:

- **Claim type** — visual-descriptive, art-historical, interpretive, or contextual
- **Evidence source** — image, metadata, scholarly text, knowledge graph, or none
- **Accuracy** — supported / partially supported / unsupported / contradicted
- **Hedging** — asserted as fact vs. appropriately qualified

The visual layer is treated as a primary source of evidence in its own right:
a claim is tested first against *what is actually visible in the image*, and only
then against metadata and scholarly text. This makes the image an explicit
evidence layer rather than a mere prompt for description.

## Proof-of-concept (this repository)

To validate that the segmentation protocol and annotation scheme can be applied
consistently, an initial set of publicly accessible art-historical objects was
described by a multimodal AI system, segmented into claim units, and annotated
across the four dimensions above. The exercise confirmed the framework's
workability and surfaced an early pattern: objects with **less available
documentation drew a higher proportion of claims with no traceable evidential
basis**.

**Methodological constraint.** The proof-of-concept descriptions were prepared
under researcher control rather than generated autonomously across varied prompt
and evidence conditions. They are therefore more grounded than fully
model-generated output is likely to be; in the full study, where model outputs
are collected directly, the divergence between evidence and asserted claim is
expected to be substantially higher. Naming this limitation is part of the point:
the framework is built to measure exactly that divergence.

## Target corpus — Bibliotheca Hertziana Fotothek

The full study draws its materials from the **Photographic Collection (Fotothek)
of the Bibliotheca Hertziana – Max Planck Institute for Art History**, accessed
through the institute's **IIIF Image and Presentation APIs** and, for openly
licensed records, via **Europeana** (data provider: Bibliotheca Hertziana,
Fotothek; metadata and images licensed CC BY-SA-NC 4.0).

Objects are selected to span contrasting **documentation density** — the core
independent variable of the study. Four representative objects from the Fotothek:

| Object | Type | Documentation density |
|--------|------|------------------------|
| Venetian Renaissance painting of an amorous couple in a landscape (Galleria Nazionale d'Arte Antica) | Painting | High |
| Sant'Andrea della Valle, façade, Rome (1665) | Architecture | High |
| Architectural sculpture group, rooftop figures (Fototeca / D'Onofrio campaign) | Sculpture (photograph) | Lower |
| Old master drawing, Corpus Photographicum of Drawings | Drawing | Sparse / variable |

This spread lets the framework test directly whether richer documentation
*reduces* unsupported AI claims, or merely makes them *sound* more authoritative.

## Repository contents

- `01_data_collection.ipynb` — object metadata, image retrieval, AI description generation
- `02_annotation.ipynb` — claim segmentation and the four-dimension annotation workflow
- `03_analysis.ipynb` — summary statistics and visualisations
- `data/annotation_template.csv` — annotation schema

## Resources

- Bibliotheca Hertziana Fotothek — https://foto.biblhertz.it
- IIIF Image / Presentation API (see "Resources") — https://www.mdh.uzh.ch/en/Resources.html
- Europeana (BHMPI Fotothek) — https://www.europeana.eu
