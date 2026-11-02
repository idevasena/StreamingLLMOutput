# Prefix Integrity Report: snapkv

Status: FAIL
Classification: DANGEROUS_FOR_PREFIX_SHARING
Danger score: 1.0

Cartridge `cart` (model Qwen/Qwen2.5-7B-Instruct, 256 blocks of 16 tokens, dtype bfloat16), policy `prefix_cache`, cache key ['prefix_hash'].

## Core metrics

- pre_mean: 0.0117
- anchor_survival_mean: 1.0
- recent_survival: 1.0
- contiguous_prefix_survival: 1
- partial_block_rate: 0.97265625
- manifest_stability: 16
- artifact_stability: 16
- same_query_artifact_count: 1
- cr_mean: 1.0122
- cr_cv: 0.007
- read_ranges: 5
- read_amplification: 0.01984126984126984

## Violations (FAIL)

- query-dependent content stored under prefix_hash without query_hash in the cache key (prefix-cache unsafe)
- partial_block_rate=0.976 > 0 on a vanilla block-based prefix-cache path

## Warnings

- PRE 0.012 below threshold 0.7

## Decision

The same prefix can map to different or non-reloadable KV objects. Do not deploy on a prefix-sharing / offload path as-is.

- add query_hash to the cache key or relabel as routing-only
