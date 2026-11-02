# Prefix Integrity Report: streaming_llm

Status: FAIL
Classification: SAFE_FOR_PREFIX_OFFLOAD
Danger score: 0.5757

Cartridge `cart` (model Qwen/Qwen2.5-7B-Instruct, 256 blocks of 16 tokens, dtype bfloat16), policy `prefix_cache`, cache key ['prefix_hash'].

## Core metrics

- pre_mean: 0.75
- anchor_survival_mean: 1.0
- recent_survival: 1.0
- contiguous_prefix_survival: 1
- partial_block_rate: 0.0
- manifest_stability: 1
- artifact_stability: 1
- same_query_artifact_count: 1
- cr_mean: 1.3333
- cr_cv: 0.0
- read_ranges: 2
- read_amplification: 0.010416666666666666
- kl: 0.4215
- top1: 0.8125

## Violations (FAIL)

- semantic drift KL 0.4215 above 0.05, not repairable

## Warnings

- top-1 agreement 0.812 below 0.9

## Decision

Contract verdict (geometry/cache-key) below, but the run FAILED on quality -- do not deploy as-is despite the contract being clean.

Shape-preserving, deterministic, and prefix_hash-safe. Safe to store and share under prefix_hash in an ordinary prefix-cache / offload path.
