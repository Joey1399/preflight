# preflight

Long context increases latency (prefill / TTFT pain)
ttft-lens is a prompt “preflight” profiler that estimates time-to-first-token (TTFT) impact from prompt length, chunk count, and context packing choices. It explains prefill vs decode, tracks token growth over time, and recommends reductions (e.g., smaller context packs, better caching boundaries). Useful for anyone building agents or RAG pipelines where long prompts quietly wreck responsiveness.\

COMING SOON
