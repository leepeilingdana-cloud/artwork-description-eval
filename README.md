# Artwork Description Evaluation — Pilot Study

A pilot implementation of the claim-based evaluation framework proposed in my
IMPRS-MDH (Multimodal Digital Humanities, UZH / Bibliotheca Hertziana) research
application.

## Research question

When a multimodal AI system generates a description of a cultural heritage
object, can its individual claims be traced back to available evidence —
**visual, documentary, iconographic, or scholarly** — or do they rest on
unverifiable inference?

## Approach

The framework treats the individual **claim**, not the whole description, as the
unit of analysis. Each AI-generated description is segmented into claim units
and annotated along two axes:

**Axis 1 — Linguistic expression of the claim**
- Claim type: visual-descriptive, art-historical, interpretive, or contextual
- Hedging: asserted as fact vs. qualified with uncertainty markers
- Evidentiality: attributed to a source, or stated without attribution
- Evaluative stance: confidence level, appraisal, genericity

**Axis 2 — Four-layer evidence verification**
Each claim is assigned one of five evidence-source values:

| Code | Layer | Evidence source |
|------|-------|----------------|
| V | Visual | Image itself, accessed via IIIF Image API |
| D | Documentary | KG², DataHub, Urbs, provenance records, historical texts |
| I | Iconographic | ICONCLASS classification (queried via Wikidata P1257 and Europeana) |
| S | Scholarly | Museum catalogue records, Bibliography of the History of Art (BHA) |
| N | None | Untraceable at any layer |

A claim classified as N is not necessarily wrong — it is **unaccountable**: no
available evidence can confirm, challenge, or engage with what it asserts.

## Proof-of-concept (this repository)

An initial set of publicly accessible art-historical objects was described by a
multimodal AI system, segmented into claim units, and annotated across the four
dimensions above. The exercise confirmed the framework's workability and
surfaced an early pattern: **objects with less available documentation drew a
higher proportion of claims with no traceable evidential basis** (N
classifications).

**Methodological note.** The proof-of-concept descriptions were prepared under
researcher control rather than generated autonomously across varied prompt and
evidence conditions. They are therefore more grounded than fully model-generated
output is likely to be. In the full study, where outputs are collected directly
from AI systems under controlled input conditions, the divergence between
evidence and asserted claim is expected to be substantially higher.

## Target corpus — Bibliotheca Hertziana Fotothek

The full study draws its materials from the **Photographic Collection (Fotothek)
of the Bibliotheca Hertziana – Max Planck Institute for Art History**, accessed
through the IIIF Image and Presentation APIs and, for openly licensed records,
via Europeana (data provider: Bibliotheca Hertziana; metadata licensed
CC BY-SA-NC 4.0).

Objects are selected to span contrasting **documentation density** — the core
independent variable of the study. Four representative objects:

| Object | Type | Documentation density |
|--------|------|-----------------------|
| *Amanti in un paesaggio* (The Lovers in a Landscape), Titian or school of Titian, c.1510–1520 — Bibliotheca Hertziana collection | Painting | High |
| Sant'Andrea della Valle, façade, Rome (Carlo Rainaldi, 1655–1665) | Architecture | High |
| Palazzo della Consulta rooftop sculptures, Piazza del Quirinale (Ferdinando Fuga, 18th c.) | Sculpture (photograph) | Lower |
| *Tobias and Sara taking leave of Raguel and Edna*, Maarten van Heemskerck, 1555 — Corpus Photographicum of Drawings | Drawing | Sparse / variable |

This spread lets the framework test whether richer documentation reduces
untraceable AI claims, or merely makes them *sound* more authoritative.

## AI systems under evaluation

The full study compares outputs from:
- **Closed-source**: GPT-4o (OpenAI), Claude 3.5 Sonnet (Anthropic), Gemini 1.5 Pro (Google)
- **Open-source**: LLaVA-1.6

Comparing across systems guards against a key methodological risk: that findings
reflect one model's stylistic habits rather than anything general about how
multimodal AI handles art-historical evidence.

## Repository contents

- `01_data_collection.ipynb` — object metadata, image retrieval, AI description generation
- `02_annotation.ipynb` — claim segmentation and two-axis annotation workflow
- `03_analysis.ipynb` — summary statistics and visualisations
- `data/annotation_template.csv` — annotation schema

## Resources

- Bibliotheca Hertziana Fotothek — https://foto.biblhertz.it
- IIIF API documentation — https://www.mdh.uzh.ch/en/Resources.html
- Europeana (BHMPI Fotothek) — https://www.europeana.eu
- ICONCLASS — https://iconclass.org
- Wikidata P1257 (ICONCLASS notation) — https://www.wikidata.org/wiki/Property:P1257
