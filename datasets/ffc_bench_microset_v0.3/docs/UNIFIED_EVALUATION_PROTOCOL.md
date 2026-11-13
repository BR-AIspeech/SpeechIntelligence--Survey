# FFC-Bench unified system evaluation protocol

This protocol separates prerecorded causal replay from live runtime execution. Results may share
behavioral denominators, but latency values from different system boundaries must not be ranked in
one column.

## Evaluation assets

- Primary controlled asset: 32 Mandarin semantic templates, each rendered under `clean`,
  `moderate`, and `hard` conditions, for 96 audio renderings.
- Independent unit: the semantic template (`N=32`), not each acoustic rendering.
- Strict context switches: four semantic contracts, each under three acoustic conditions.
- Acoustic preservation: compare the three conditions of the same `base_case_id`.
- A separate 48-case metadata pilot mentioned in the source materials is not included in this release.

The manifest's `gold_*` schema fields are designer-specified reference targets. Until independent
review is completed, report agreement with those targets rather than human-gold accuracy.

## Mode A: causal replay

Use for open checkpoints and local controllers.

1. Stream the prerecorded waveform in fixed, timestamped chunks at the declared media cadence.
2. Never expose samples or transcripts beyond the current media time.
3. Record model action, output onset/suppression, tool events, and optional state/gate traces.
4. Report media-clock action delay and local inference timing (`RTF`, per-chunk P95) separately.
5. A model that reads the completed waveform is a full-context upper bound, not a streaming run.

## Mode B: runtime streaming

Use for native local servers and hosted realtime APIs.

1. Push the same waveform at real-time cadence through the documented WebSocket/WebRTC transport.
2. Use one monotonic harness clock for input writes, server events, received audio, playback,
   suppression, tool events, and failures.
3. Measure end-to-end response and stop latency at the audible playback boundary, including
   network, service, synthesis, buffering, and queued audio.
4. Record endpoint/model id, date, region, account configuration, prompt, voice, sample rate,
   chunk size, server VAD settings, adapter revision, retries, failures, and total cost.
5. Do not store credentials in traces or release artifacts.

## Common action normalization

Normalize observable behavior to `listen`, `wait`, `speak`, `stop`, `ignore`, `continue`, `join`,
`ask`, `clarify`, or `act`. A black-box product exposes behavior, not its internal state: do not
use an external judge to invent state, gate, or calibration scores. When `permission` or
`addressee` is not audible, inject it through a documented context interface; otherwise mark that
contract unsupported.

## Primary metrics

- Participation: PD-F1 when a gate is observable, UPR, MRR, and response coverage.
- Action: acceptable-action agreement and macro action-F1, stratified by family and condition.
- Timing/overlap: PRR, MIR, BFSR, FRR, response latency median/P90, and stop latency median/P90.
- Matched tests: exact correct-change on four context-switch contracts and acoustic preservation
  across clean/moderate/hard. With only four independent semantic pairs, do not claim asymptotic
  significance.
- Runtime reporting: failure/timeout rate and cost; open-system diagnostics may additionally
  include state macro-F1, ECE/Brier, RTF, and per-chunk P95 inference time.

Latency is always accompanied by coverage, and missed deadlines remain in the behavioral
denominator. Stochastic systems require at least three repeats per case. Cluster confidence
intervals by `base_case_id` or `pair_id`, keeping acoustic variants and repeats together.

## Inaccessible or failed systems

- API access unavailable or unaffordable: mark `N/A` with reason and access date, or replace it
  before the evaluation freeze with a representative system from the same access stratum.
- Product UI only: report a dated qualitative case study; exclude it from scripted latency tables.
- Checkpoint not reproducibly executable: record repository revision, environment, and failure;
  do not assign a zero and do not copy a paper-reported number into the unified table.
- No hosted system run: restrict conclusions to an open-system audit.
- No natural-speech validation: restrict conclusions to synthetic controlled behavior.

## Relationship to the current survey

This protocol is a proposal for possible future validation. The current survey does not include an experimental section reporting these runs. Any later evaluation should document its executed configuration, publish supported results and failures, and distinguish replay from runtime measurements.
