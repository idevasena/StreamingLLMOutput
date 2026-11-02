# Prefix Integrity Report: knorm

Status: FAIL
Classification: SAFE_ONLY_WITH_CUSTOM_CONNECTOR
Danger score: 0.8965

Cartridge `cart` (model Qwen/Qwen2.5-7B-Instruct, 256 blocks of 16 tokens, dtype bfloat16), policy `prefix_cache`, cache key ['prefix_hash'].

## Core metrics

- pre_mean: 0.0117
- anchor_survival_mean: 1.0
- recent_survival: 1.0
- contiguous_prefix_survival: 1
- partial_block_rate: 0.97265625
- manifest_stability: 1
- artifact_stability: 1
- same_query_artifact_count: 1
- cr_mean: 1.0159
- cr_cv: 0.0
- read_ranges: 5
- read_amplification: 0.01984126984126984

## Violations (FAIL)

- partial_block_rate=0.973 > 0 on a vanilla block-based prefix-cache path

## Warnings

- PRE 0.012 below threshold 0.7

## Decision

Contract verdict (geometry/cache-key) below, but the run FAILED on quality -- do not deploy as-is despite the contract being clean.

Uses partial blocks, merging, sub-block masks, or variable-shape tensors. Not reusable by vanilla block-hash prefix caching without a custom connector and extra metadata.

- partial blocks need a custom connector or whole-block policy
