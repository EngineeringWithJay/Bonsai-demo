# NVIDIA GeForce RTX 2060 12 GB — CUDA — Bonsai-27B (1-bit)

## Summary

RTX 2060 12 GB (TU106, Turing sm_75; driver 580.178.04; ~$0.100/hr) measured with the PrismML llama.cpp fork `prism-b10777-e3de715`
(linux-cuda-12.4 assets) on a vast.ai pod, `llama-bench -ngl 99 -fa 1 -p 512 -n 128 -r 3`.

| file | pp512 (t/s) | tg128 (t/s) |
|------|------------:|------------:|
| `Q1_0` (3.53 GiB) | 431.23 ± 4.28 | 29.96 ± 0.05 |

## Configuration

- fork `prism-b10777-e3de715` CUDA-12.4
- Model: `prism-ml/Ternary-Bonsai-27B-gguf` — `Ternary-Bonsai-27B-Q2_g64.gguf` sha256 `59a45d1ecef702b14531b06d22949f33b25c1897da31a8c0b298e01e4d9138eb` (digest identical across the whole fleet).
- Per the formats guide, current builds expect `PQ2_0` (group-128) **and** `Q2_0` group-64; this entry measures the group-64 file on a current fork build. `PQ2_0` (this gen) not yet run — follow-up planned.
- Rented pod destroyed after capture; ± = llama-bench dispersion over 3 reps.

## Notes

Same card as the ternary entry: 1-bit gives +3.7% prefill, +17% decode, half the bytes.

## Hardware

```
NVIDIA GeForce RTX 2060, 12288 MiB; driver 580.178.04
```
