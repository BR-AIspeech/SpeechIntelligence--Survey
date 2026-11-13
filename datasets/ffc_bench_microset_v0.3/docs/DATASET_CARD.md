# Dataset card: FFC-Bench Doubao-Informed Controlled Microset v0.3

## Summary

This is a synthetic Mandarin controlled microset for evaluating interaction decisions in
real-time full-duplex voice systems. It contains 32 semantic templates expanded into three
acoustic conditions, for 96 rendered audio files.

| Field | Value |
| --- | --- |
| Language | Mandarin Chinese (`zh-CN`) |
| Semantic templates | 32 |
| Renderings | 96 |
| Interaction families | 7 |
| Conditions | `clean`, `moderate`, `hard` (32 each) |
| Audio | PCM WAV, mono, 16 kHz, 16 bit |
| Speech renderer | Windows SAPI, `Microsoft Huihui Desktop` |
| Mixer | Deterministic NumPy/soundfile pipeline |
| Human speech | None |
| Personal data | None expected |
| Reference targets | Designer specified; not independently human validated |
| Public distribution | Confirmed by repository owner on 2026-11-13; no additional blanket reuse license |

## Motivation

The microset supports controlled tests of when a system should listen, wait, speak, stop,
continue, ignore, join, ask, clarify, or act. It focuses on decision contracts that are often
collapsed into end-of-turn detection or response generation scores.

## Composition

The 32 templates cover:

- acoustic interference;
- bystander and addressee filtering;
- environment-context use;
- explicit interruption;
- hesitation and self-repair;
- multi-speaker overlap; and
- rapid endpointing.

Each template is rendered in three deterministic conditions. `moderate` and `hard` add generated
noise and controlled overlap; they do not contain captured room, cafe, road, or vehicle ambience.
The manifest includes four strict context-switch pair contracts.

Three clean-condition context-switch pairs intentionally use byte-identical audio on their two
branches while changing a non-waveform context variable (`addressee` or `permission`). Systems
must receive that variable through a documented context interface or mark the contract
unsupported; they must not infer it from the waveform. The fourth strict pair changes active
playback and therefore does not have identical mixed audio.

The independent semantic unit is the template. Acoustic variants are repeated measurements of
the same semantic case and must be clustered together in statistical analysis.

## Generation and provenance

Scenario motifs were informed by the ByteDance Seed article listed in
`SOURCE_AND_PROVENANCE.md`. The article's reported product improvements are not labels, ground
truth, or benchmark scores. Text prompts, scenario contracts, labels, timing windows, acoustic
conditions, and mixing parameters were authored for this research asset.

Speech stems were generated locally through Windows
`System.Speech.Synthesis.SpeechSynthesizer`. All 32 renderer records identify
`Microsoft Huihui Desktop` for user, system, and bystander roles. Audio was normalized and mixed
to mono, 16 kHz, 16-bit PCM.

## Labels

Fields named `gold_*` are retained for evaluator compatibility, but every row declares
`target_status=designer_specified_reference`. They represent the authors' reference contract,
not consensus human judgments. Report agreement with controlled reference targets rather than
human appropriateness or accuracy.

## Intended uses

- Reproducible smoke tests for causal audio adapters and real-time voice agents.
- Family- and condition-stratified action agreement.
- Matched context-switch and acoustic-preservation checks.
- Coverage-aware response and stop timing studies.
- Regression testing of interaction-decision pipelines.

## Out-of-scope uses

- Training a general-purpose speech or conversation model.
- Claims about natural human dialogue, social appropriateness, or population behavior.
- Speaker recognition, speaker diversity, accent coverage, or demographic analysis.
- A single aggregate leaderboard that ignores family, condition, and coverage.
- Treating the 96 renderings as 96 independent conversations.
- Claiming ByteDance/Seed endorsement or treating the audio as vendor-provided recordings.

## Known limitations

1. **Single synthetic voice.** All role metadata records the same installed voice. Speaker roles
   are encoded by scenario structure, not distinct vocal identities.
2. **Synthetic acoustics.** Noise and overlap are generated; the set does not reproduce the
   complexity of natural rooms, devices, codecs, reverberation, or conversational timing.
3. **Small scale.** There are only 32 independent semantic templates and four strict
   context-switch contracts.
4. **Designer targets.** No independent double annotation or adjudication has been completed.
5. **Language and locale.** The set is Mandarin-only and contains China-specific place and
   interaction references.
6. **No demographic coverage.** A single TTS voice cannot support fairness or population claims.
7. **Reuse rights.** The repository owner confirmed public redistribution on 2026-11-13. No additional blanket reuse license is granted; see `../LICENSE_STATUS.md`.

## Privacy and safety

No human voices, credentials, provider responses, or intentionally collected personal data are
included. The prompts describe fictional controlled scenarios. A final secret/PII scan should
still be part of every release build.

## Recommended reporting

- State `N=32 templates / 96 renderings`.
- Report each interaction family and acoustic condition separately.
- Cluster confidence intervals by `base_case_id` or `pair_id`.
- Report missing, late, malformed, and unsupported cases explicitly.
- Keep causal replay and runtime-streaming latency in separate tables.
- Describe reference-action results as controlled-contract agreement.


## Repository publication note

The candidate data and audio are preserved as supplied. Current publication facts are in `../metadata/publication_status.json`; the original candidate status is a historical record. Implementation scripts and the separate 48-case pilot are not included. No evaluation of a speech system is reported by this repository snapshot.
