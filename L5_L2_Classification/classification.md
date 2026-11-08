# L5 Narrow / L2 General Classification — K_NEURODSP
**Platform:** Anticloud | **Tier:** TIER_7_BIOSIGNALS_NEURO | **PAX:** 27B
**IP:** USPTO pending 2026, Anticloud FZ LLE, 0-1.gg | **License:** Apache-2.0

## L5 Narrow
K_NEURODSP provides digital signal processing tools optimized for neural time series: bandpass filtering, spectral analysis, aperiodic component estimation (1/f noise), and burst detection. Narrow scope: Anticloud EEG/LFP signal processing.

## L2 General
L2 General: K_NEURODSP's signal processing is the first stage in all Anticloud biosignal pipelines. TIER_7 clinical EEG and TIER_5 neuro-embodied research both depend on K_NEURODSP for clean signals.

## PAX 27B Integration
PAX 27B receives K_NEURODSP-processed signals and generates clinical notes: 'After bandpass filtering, theta burst activity detected in frontal channels at 220ms post-stimulus.'

## AIOSS Audit Chain
Every signal processing step (raw signal hash + filter params hash + processed signal hash + burst detections hash) is chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Offline-verifiable, tamper-evident, zero cloud dependency.

## Regulatory / Compliance
IEC 62304 (medical software). Good Clinical Practice (GCP).
