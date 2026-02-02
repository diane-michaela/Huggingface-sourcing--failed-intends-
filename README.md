Hugging Face Retrieval / Search Talent Sourcer
(Models + Datasets + Author Enrichment)

What this script does
- This script automatically discovers AI engineers working on Search & Retrieval systems by scanning public Hugging Face model and dataset repositories, then exporting the results to a structured Excel file for recruiting.

Instead of relying on resumes or LinkedIn titles, it sources proof-of-work:
- embedding models
- retrieval and re-ranking systems
- search training datasets
- evaluation artifacts

What problem it solves
Recruiting senior ML / Search engineers from LinkedIn alone has poor signal.

Hugging Face hosts:
- real fine-tuned models
- retrieval pipelines
- ranking datasets
- production-oriented ML work

This script turns Hugging Face into a recruiting signal source, similar to how GitHub is used for engineers — but focused on LLM + Search.

What you actually ran
1) You queried Hugging Face for relevant work

The script searched public Hugging Face repositories using small, targeted queries, not one big keyword search.
Model queries (Search / Retrieval focus)
- embedding
- retrieval
- reranker
- ranker
- dense retrieval
- bi-encoder
- cross-encoder
- dual encoder
- colbert
- splade
- contriever

Dataset queries (training & evaluation data)
- retrieval
- ranking
- query
- qrels
- hard negatives
- triplets
- query passage
- query-document pairs
- pairwise ranking

Each query was run independently, then merged and deduplicated.

2) You filtered for recent, active work

Only repositories updated between 2023–2026 were kept.

This avoids:
- abandoned experiments
- outdated academic artifacts

3) You enriched creators (people & orgs)

For every model or dataset:
- The script extracted the author namespace
- Looked up:
  - Hugging Face user or organization profiles
  - bio, website, GitHub, LinkedIn (if public)
- Cached profiles to avoid duplicate calls

This is how:
- Qwen, BAAI, etc. (organizations) are handled correctly
- Individuals are enriched when available

4) You authenticated correctly (important)

You created a Hugging Face access token and stored it locally in:
token_hf.py


This allowed:
- higher rate limits
- stable enrichment
- fewer API errors

The script confirmed this with:
Authorization header present: True

5) You ran it from PowerShell (intentionally)

You ran the script from PowerShell because:
- it guarantees correct file paths
- it avoids VS Code environment confusion
- it ensures Python sees your token

Command used:

cd C:\Users\Diane Rocher\Desktop\API
python huggingface_retrieval_sourcer_excel.py


This is the most reliable way to run sourcing scripts.

What the output contains

The script produces an Excel file containing:
- Repo information
- model or dataset name
- Hugging Face link
- tags (retrieval, ranking, embeddings, etc.)
- downloads and likes
- license
- last update date

Matching signals
- which keywords matched (retrieval, reranker, etc.)
- relevance score (0–100)

Author enrichment
- Hugging Face profile link
- name (if public)
- bio
- GitHub link (if found)
- LinkedIn link (if found)
- website / other links

This allows quick recruiter triage.

Why this is high-signal for recruiting

Someone who:
- publishes embedding models
- builds rerankers
- creates retrieval datasets
- documents evaluation metrics

…is almost always:
- a real Search / ML engineer
- working hands-on with LLM systems
- senior or staff-level in practice
- This goes far beyond job titles.

What you now have

You now have:
- a repeatable sourcing pipeline
- a non-LinkedIn talent source
- a way to find Search + LLM Ops engineers by real work

Glad you read till the end ( ͡° ͜ʖ ͡°)
