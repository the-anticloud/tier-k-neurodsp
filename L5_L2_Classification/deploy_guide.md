# Deploy Guide — K_NEURODSP
**Tier:** TIER_7_BIOSIGNALS_NEURO | **Stack:** Python 3.11, neurodsp 2.x, numpy, scipy, PAX 27B, AIOSS_FORMAT
**Air-gap capable after initial setup.**

## Prerequisites
Python 3.11+, neurodsp 2.2+, numpy 1.26+, scipy 1.13+. CPU-only for DSP.

## Environment
4GB RAM. CPU-only for signal processing. GPU for PAX analysis.

## AIOSS Integration
```bash
aioss init --module K_NEURODSP --output ./k_neurodsp.aioss
aioss append --chain ./k_neurodsp.aioss --payload ./output.bin --module K_NEURODSP
aioss verify --chain ./k_neurodsp.aioss
```

## Air-Gap Setup
```bash
pip download -r requirements.txt -d ./wheels/
pip install --no-index --find-links ./wheels/ -r requirements.txt
```

## PAX 27B Harness Wiring
```python
from anticloud_pax import PAXHarness
harness = PAXHarness(
    model_path="./pax-27b-q4.gguf",
    module="K_NEURODSP",
    aioss_chain="./K_NEURODSP.aioss",
    classification="L5_NARROW_L2_GENERAL"
)
result = harness.process(input_data)
```

## Verification
```bash
aioss verify --chain ./K_NEURODSP.aioss --verbose
python -m K_NEURODSP.tests.smoke
```
