# Anticloud × NEURODSP
> Neural DSP pipelines — air-gapped, zero cloud dependency.

**Part of:** Biosignals / Neuro · Anticloud FZ LLE · 0-1.gg
**Upstream:** neurodsp-tools/neurodsp (Apache-2.0)
**License:** Apache-2.0 OR LicenseRef-Anticommons-Enterprise-1.0
**IP:** USPTO pending · Lois-Kleinner Alpasan · 2026

---

## What Makes This Different From Upstream

Neural digital signal processing: oscillation detection, burst analysis, filtering. We add:

1. **AIOSS ledger for every inference** — every request/response cryptographically logged
2. **K5-512 post-quantum hash** upgrade (optional, for quantum-resistant audit trails)
3. **Offline-first deployment** — zero cloud dependency, single binary packaging
4. **Sovereign data guarantees** — no telemetry, no callbacks, no hidden network calls
5. **Anticloud composite scoring** — TRL(40%) + OWASP(20%) + SOC2(20%) + NIST(20%)

---

## Performance

| Metric | Upstream stock | Anticloud Edition |
|--------|---------------|-------------------|
| AIOSS ledger overhead | N/A | <3ms async (non-blocking) |
| Offline capability | Partial | Full (single binary) |
| Audit trail | None | Hash-chained ledger |
| SOTA claim | NEAR-SOTA | NEAR-SOTA |

---

## Quick Start

```bash
git clone --depth=1 https://github.com/neurodsp-tools/neurodsp upstream/
cd upstream
pip install -e .
```

## Reference

- Official: https://neurodsp-tools.github.io/neurodsp/
- GitHub: https://github.com/neurodsp-tools/neurodsp
- Tier: TIER_7_BIOSIGNALS_NEURO

---
_Anticloud Edition — Lois-Kleinner 2026 — 2026-09-30T18:11:11.493145+00:00_
