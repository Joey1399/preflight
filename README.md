# preflight

Long context increases latency (prefill / TTFT pain)
ttft-lens is a prompt “preflight” profiler that estimates time-to-first-token (TTFT) impact from prompt length, chunk count, and context packing choices. It explains prefill vs decode, tracks token growth over time, and recommends reductions (e.g., smaller context packs, better caching boundaries). Useful for anyone building agents or RAG pipelines where long prompts quietly wreck responsiveness.\

## Long context increases latency (prefill/KV-cache pain)

**Goal:** minimize prefill work and maximize reuse.

- **Reduce tokens at the source:** context bundles (Problem #3) are the biggest lever for TTFT.
- **Maximize KV-cache reuse:** stable prefixes + caching can drastically cut prefill compute; a lot of inference optimization revolves around keeping more context “resident” in KV cache. ([NVIDIA Developer][9])
- **If self-hosting:** use engines/features designed for throughput + caching (e.g., vLLM batching knobs) and consider external/persistent KV caching approaches where appropriate. ([vLLM][10])
- **Expose TTFT metrics:** your context manager can report “tokens sent” and “expected TTFT impact” per run so users see why things got slow.

COMING SOON
