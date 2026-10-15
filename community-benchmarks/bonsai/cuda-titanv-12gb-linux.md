# NVIDIA TITAN V 12 GB — CUDA — Bonsai-27B (1-bit)

## Summary

TITAN V 12 GB (GV100, Volta sm_70, HBM2; driver 580.173.02; ~$0.114/hr) measured with the PrismML llama.cpp fork `prism-b10777-e3de715`
(linux-cuda-12.4 assets) on a vast.ai pod, `llama-bench -ngl 99 -fa 1 -p 512 -n 128 -r 3`.

| file | pp512 (t/s) | tg128 (t/s) |
|------|------------:|------------:|
| `Q1_0` (3.53 GiB) | 552.38 ± 0.51 | 56.47 ± 0.10 |

## Configuration

- fork `prism-b10777-e3de715` CUDA-12.4; upstream b11630 runs `Q1_0` too (fully merged)
- Model: `prism-ml/Ternary-Bonsai-27B-gguf` — `Ternary-Bonsai-27B-Q2_g64.gguf` sha256 `59a45d1ecef702b14531b06d22949f33b25c1897da31a8c0b298e01e4d9138eb` (digest identical across the whole fleet).
- Per the formats guide, current builds expect `PQ2_0` (group-128) **and** `Q2_0` group-64; this entry measures the group-64 file on a current fork build. `PQ2_0` (this gen) not yet run — follow-up planned.
- Rented pod destroyed after capture; ± = llama-bench dispersion over 3 reps.

## Notes

3.53 GiB leaves ~8 GB for context on a 12 GB card; decode beats the same machine's ternary row (51.25 t/s, [../ternary-bonsai/cuda-titanv-12gb-linux.md]).

## Hardware

```
NVIDIA TITAN V, 12288 MiB; driver 580.173.02
```
