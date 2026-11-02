# Prefix Integrity Report: streaming_llm

Status: WARN
Classification: SAFE_FOR_PREFIX_OFFLOAD
Danger score: 0.3312

Cartridge `cart` (model Qwen/Qwen2.5-7B-Instruct, 256 blocks of 16 tokens, dtype bfloat16), policy `prefix_cache`, cache key ['prefix_hash'].

## Core metrics

- pre_mean: 0.0625
- anchor_survival_mean: 1.0
- recent_survival: 1.0
- contiguous_prefix_survival: 1
- partial_block_rate: 0.0
- manifest_stability: 1
- artifact_stability: 1
- same_query_artifact_count: 1
- cr_mean: 16.0
- cr_cv: 0.0
- read_ranges: 2
- read_amplification: 0.125

## Warnings

- PRE 0.062 below threshold 0.7

## Decision

Shape-preserving, deterministic, and prefix_hash-safe. Safe to store and share under prefix_hash in an ordinary prefix-cache / offload path.
