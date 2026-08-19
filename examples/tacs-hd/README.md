# Example data set: tACS via a 4x1 HD montage

Single-subject transcranial alternating current stimulation (tACS) delivered through a
high-definition 4x1 ring montage, formatted to the NIBS-BIDS v6.3 structure. It is a basic example
that shows the two things specific to this modality: the `Sinusoid` waveform parameters, and a
multi-contact placement described by several rows in `*_markers.tsv`.

## Protocol

10 Hz tACS over left sensorimotor cortex for 20 minutes. A centre electrode over `C3` delivers a 1 mA
sinusoidal amplitude, and four return electrodes on the surrounding ring (`FC3`, `C1`, `C5`, `CP3`)
each carry -0.25 mA, so the amplitudes sum to zero. Delivered offline, with no concurrent recording.

## What this example shows

- Sinusoid waveform parameters as `*_nibs.tsv` columns: `stimulus_shape = Sinusoid`, `frequency = 10`,
  `starting_phase = 0`.
- A multi-contact montage. One `*_nibs.tsv` row lists five electrodes in `nibs_element_id`, with the
  per-electrode amplitudes in `stimulus_intensity` (`1|-0.25|-0.25|-0.25|-0.25`, summing to 0), and the
  five placements in `*_markers.tsv`, referenced by a `|`-delimited `nibs_position_id`.
- Placements given by 10-10 label only, without coordinates.
- Absolute intensity (`intensity_reference = absolute`), so no `IntensitySet` is needed.
- Offline stimulation: the timeline is in `nibs/*_events.tsv`, and `*_nibs.tsv` is listed in
  `scans.tsv`.

## Files

- `nibs/*_nibs.tsv` and `.json`: waveform parameters, `StimulatorSet`, `ElementSet` (five electrodes).
- `nibs/*_markers.tsv` and `.json`: the five electrode placements.
- `nibs/*_events.tsv` and `.json`: standalone timeline.
