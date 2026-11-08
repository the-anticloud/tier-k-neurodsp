# Developer Cookbook — K_NEURODSP
**Stack:** Python 3.11, neurodsp 2.x, numpy, scipy, PAX 27B, AIOSS_FORMAT
**Domain:** NeuroDSP: digital signal processing for neural time series in Anticloud

## Filter and analyze neural signal
```python
from k_neurodsp import NeuroDSPPipeline

pipeline = NeuroDSPPipeline(
    pax_model="./pax-27b-q4.gguf",
    aioss_chain="./neurodsp.aioss"
)

eeg = load_eeg("./patient_001.edf")  # shape: (n_channels, n_samples)
result = pipeline.process(
    signal=eeg,
    fs=256,
    steps=[
        {"type": "bandpass", "f_range": (1, 45)},
        {"type": "notch", "f0": 50},
        {"type": "burst_detection", "band": "theta", "threshold": 2.0}
    ]
)
print(f"Bursts detected: {result.n_bursts}")
print(f"Mean burst duration: {result.mean_burst_duration_s:.3f}s")
```

## AIOSS Chain Append
```python
import hashlib, time

def aioss_append(chain_path, payload: bytes, module_id: str):
    entry_hash = hashlib.sha3_256(payload).digest()
    ts = int(time.time_ns()).to_bytes(8, 'big')
    with open(chain_path, 'rb') as f:
        f.seek(-32, 2); prev_hash = f.read(32)
    new_hash = hashlib.sha3_256(prev_hash + entry_hash + ts).digest()
    with open(chain_path, 'ab') as f:
        f.write(ts + entry_hash + new_hash)
    return new_hash.hex()
```
