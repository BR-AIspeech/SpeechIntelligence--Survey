# FFC-Bench Doubao-Informed Controlled Microset v0.3

This publication snapshot accompanies the [Speech Intelligence Survey](../../README.md). It preserves the supplied candidate's original scenario data and 96 synthetic WAV files, while excluding implementation scripts.

- 32 Mandarin semantic templates in 7 interaction families.
- 3 acoustic conditions per template: `clean`, `moderate`, and `hard`.
- 96 rendered WAV files: PCM, mono, 16 kHz, 16 bit, 483.276 seconds in total.
- Windows SAPI rendering with Microsoft Huihui Desktop and deterministic mixing.
- Designer-specified reference actions; no independent human-gold validation.

## Status and relationship to the paper

The repository owner confirmed on 2026-11-13 that the audio can be publicly redistributed. No additional blanket reuse license is granted. See [LICENSE_STATUS.md](LICENSE_STATUS.md).

This dataset is provided for possible future validation. The current survey does not contain a completed evaluation on these cases. Signal-format QA is not evidence of system capability or a validation of IPL levels.

## Files

| Path | Meaning |
|---|---|
| `audio/mixed/` | 96 WAV renderings |
| `data/doubao_microset_catalog.csv` | One row per semantic template (32 rows) |
| `data/doubao_microset_manifest.jsonl` | Condition-expanded design specification (96 rows) |
| `data/doubao_microset_rendered_manifest.jsonl` | Rendered audio and timing metadata (96 rows) |
| `metadata/audio_inventory.csv` | Per-file format, duration, byte size, and SHA-256 |
| `metadata/render/` | 32 renderer provenance records |
| `metadata/publication_status.json` | Current repository publication facts |
| `metadata/publication_audio_qa.json` | Independent format and integrity recheck for this publication |
| `metadata/original_candidate_release_summary.json` | Historical candidate status, preserved as supplied |
| `docs/` | Dataset card, source map, evaluation protocol, and trace schema |

## Reading the original metadata

The original data and metadata are preserved byte for byte. Some fields describe an earlier preparation stage: `audio_available=false` in the specification manifest and `audio_status=recipe_only` in the original summary are design-stage values. For the audio actually included here, use the rendered manifest, inventory, and publication status.

The historical candidate release summary records the earlier pending-clearance status and original package contents. It is not the status of this repository snapshot. The 48-case metadata pilot mentioned in the original protocol is not included.

Some matched clean-condition context-switch branches intentionally have identical WAV contents while their supplied addressee or permission context differs. Do not infer an inaudible context variable from the waveform.

## Interpretation

Report N=32 semantic templates / 96 renderings. Keep acoustic variants and repeated runs together in statistical analysis. Report results by family, condition, and supported contract. These are synthetic controlled episodes, not a population sample, natural conversations, distinct-speaker recordings, or vendor-supplied audio.

No generation, mixing, validation, or scoring source code is included in this repository. The paper's current citation is supplied in [CITATION.cff](CITATION.cff); dataset creator names are retained from the supplied candidate.
