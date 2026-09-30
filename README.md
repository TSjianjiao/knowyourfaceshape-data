# knowyourfaceshape-data

The reusable data behind [knowyourfaceshape.com](https://knowyourfaceshape.com/) — the face-shape classification rule set and every dated comparison table the site publishes, in open formats, for anyone to check, reuse or build on.

## What is here

| Path | Contents |
|---|---|
| [`classification/ruleset.json`](./classification/ruleset.json) | The full classification rule set: seven shape prototypes on two measurement scales, per-feature spread, weights, the manual-angle boost, and the disclosed limitations. These are the same constants the live classifier imports — the site's [/about](https://knowyourfaceshape.com/about/) page publishes them in prose. |
| [`classification/ruleset.md`](./classification/ruleset.md) | The same rule set as a human-readable table. |
| [`tables/`](./tables/README.md) | Every dated comparison table the site publishes — 74 tables, 570 rows across 31 articles — as Markdown (reading) and JSON (machines), one file pair per article, each linked back to the live page. |

## What these tables are

One row per table is one **published** position: the date it was published, what kind of source published it, and the number or instruction it gave, ordered oldest first. Sources are named so that every row can be independently checked; links to them are deliberately not included. Each article then states which rows moved over the covered period and which did not.

## Provenance and freshness

Exported from the article sources on 2026-09-19; refreshed 2026-09-30. The rule set carries its own calibration history and limitations inside the JSON (`disclosed_limitations`) — they are part of the data, not a footnote: three of the seven prototypes are interpolated rather than measured, and the calibration set cannot separate square from round by jaw angle alone.

## License

Data and tables: [CC BY 4.0](./LICENSE). Attribution: "knowyourfaceshape.com" with a link to the originating article where one exists. The third-party positions quoted inside the tables belong to their publishers; this archive records what was published, with dates, and claims no ownership of it.

## Cite as

A frozen v1.0 snapshot of this repository (2026-09-19) is archived on Zenodo: [DOI 10.5281/zenodo.22842019](https://doi.org/10.5281/zenodo.22842019).

> knowyourfaceshape.com (2026). *KnowYourFaceShape Open Data: a face-shape classification rule set and 27 dated comparison tables of published styling advice* (v1.0) [Data set]. Zenodo. https://doi.org/10.5281/zenodo.22842019

