# HBM Fault-Injection Supplementary Experiments

This repository combines reproducible HBM 1→0 asymmetric bit-flip fault-injection experiments for Qwen3-8B and Llama-3-8B-Instruct. The repository is organized into two independent model sections: [qwen/](qwen/) and [llama/](llama/).

## Repository structure

```text
.
├── README.md
├── qwen/
│   ├── fp16-clean/
│   ├── int8-clean/
│   ├── int8-ber003/
│   ├── specc/
│   ├── srlr/
│   └── package_manifest.json
└── llama/
```

### Qwen3-8B

- [FP16 clean](qwen/fp16-clean/)
- [INT8 clean](qwen/int8-clean/)
- [INT8 BER=0.003](qwen/int8-ber003/)
- [SpECC INT8](qwen/specc/)
- [SRLR INT8](qwen/srlr/)
- [Qwen package manifest](qwen/package_manifest.json)

### Llama-3-8B-Instruct

See [llama/](llama/) for the existing FP16 and Quanto INT8 experiment code, notebooks, documentation, and summary results.

The fault model selects eligible bits whose original value is 1 and flips approximately 0.3% of them to 0. Each experiment records its model configuration, protected or injected weight scope, random seed, GPU, actual changed-bit count, BER, and benchmark accuracy. Large model files, raw masks, caches, and full runtime logs are intentionally excluded.

## Accuracy summary

### Qwen3-8B

| Experiment | MathQA | MMLU | HumanEval |
|---|---:|---:|---:|
| FP16 clean | 84.90% | 72.30% | 82.32% |
| INT8 clean | 84.90% | 72.20% | 83.54% |
| INT8 BER=0.003 | 24.41% | 43.99% | 37.81% |
| SpECC INT8 | 84.39% | 72.36% | 82.87% |
| SRLR INT8 | 80.40% | 71.13% | 78.17% |

### Llama-3-8B-Instruct

| Experiment | MathQA | MMLU | HumanEval |
|---|---:|---:|---:|
| FP16 clean | 48.80% | 48.80% | 60.98% |
| INT8 clean | 48.40% | 65.60% | 65.60% |
| INT8 BER=0.003 | 5.80% | 26.46% | 1.34% |
| SpECC INT8 | 46.49% | 64.82% | 56.83% |
| SRLR INT8 | 36.04% | 59.34% | 43.66% |

## Benchmarks

- MMLU: general knowledge and reasoning.
- MathQA: mathematical problem solving.
- HumanEval: code generation.

## Reproducibility

See the [qwen/](qwen/) and [llama/](llama/) subdirectories for the exact scripts, notebooks, configuration files, experiment descriptions, and selected result summaries. Do not commit model weights, raw masks, caches, or full logs.
