# Source map for the Doubao-informed microset (v0.3)

## Reference

- Publisher: ByteDance Seed
- Title: Seed Full-Duplex Speech LLM Released: Attentive Listening, Robust Interference Suppression, and More Natural Interaction
- Publication date: 2026-04-09
- URL: https://mp.weixin.qq.com/s/ymyF-nBO-VT7ehnGO255qg
- BibTeX key: `bytedance2026seeduplexwechat`

The article is used only to identify interaction motifs and evaluation dimensions. Its product
claims and relative improvements are vendor-reported observations, not labels, ground truth, or
FFC-Bench scores.

## Motif mapping

| Family | Article motif | Policy contrast exercised |
| --- | --- | --- |
| `acoustic_interference` | Vehicle, navigation, and engine sound | Addressed request versus irrelevant playback; act, stop, or ignore |
| `bystander_addressee` | Cafe, delivery person, and side conversation | Addressee filtering and permission-sensitive participation |
| `multi_speaker_overlap` | Multiple speakers and simultaneous speech | Target attribution, clarification, backchannel preservation |
| `hesitation_repair` | Hesitation and self-correction | Hold the floor instead of treating a pause as an endpoint |
| `rapid_endpoint` | Rapid questions and short completed turns | Low-latency response without indiscriminate interruption |
| `explicit_interruption` | Explicit stop, note-taking, and resume requests | Stop, listen, continue, or resume at a licensed time |
| `environment_context` | Relevant or irrelevant ambient information | Context-conditioned initiative and preservation of silence |

## Release shape

The catalog defines 32 semantic templates: four per family, except eight for
`bystander_addressee` because that family covers both cafe and delivery roles. The manifest
expands every template into `clean`, `moderate`, and `hard` local acoustic conditions, giving 96
episode rows. Four pair contracts are strict context switches over active playback, addressee,
or permission; the lexical event and remaining scene fields are held fixed in each contract.
The companion `doubao_microset_catalog.csv` keeps one human-auditable row per semantic template.
The supplied WAV files were rendered locally using Windows SAPI and a deterministic mixer; implementation scripts are excluded from this repository. SNR, overlap, voice,
and onset settings are our controlled recipe; they are not parameters reported by Seed.

The audio is synthetic and uses installed Windows SAPI voices. Do not describe it as a human
conversation corpus or a recording from ByteDance. Keep the 48-case metadata pilot separate: it
is an evaluator wiring/unit test, whereas this 96-rendering set is a scenario and audio asset for
the proposed FFC-Bench contract.

## Publication snapshot

The 96 supplied WAV files are included unchanged. The separate 48-case metadata pilot is not included. These records describe scenario provenance and a proposed evaluation contract; they do not constitute system benchmark results in the current survey.
