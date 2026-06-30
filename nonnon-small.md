# Model Card: nonnon-small

## Model Summary

NONNON-small is a closed-weight legal reasoning system served through an OpenAI-compatible API. It is designed for LegalBench-style tasks and evaluated through the public endpoint `https://small.nonnon.ai/v1/chat/completions`.

## Intended Use

- LegalBench-style legal reasoning evaluation
- Research benchmarking
- Reproducibility checks through the public API

## Out-of-Scope Use

- Legal advice
- High-stakes legal, financial, or personal decisions without qualified professional review
- Jurisdictions and tasks outside the model's evaluated scope

## How To Use

Request an evaluation token from `labs@nonnon.ai`, then call the OpenAI-compatible endpoint directly or use the Python SDK:

```python
from nonnon import Client

client = Client(api_key="YOUR_TOKEN")
response = client.chat.completions.create(
    model="nonnon1-small-router",
    messages=[{"role": "user", "content": "Your LegalBench prompt"}],
    temperature=0,
)
```

## Training Data

NONNON-small is closed weight. Public LegalBench evaluation rows are used in the reproduction repository only for evaluation checks. Detailed training-data provenance is available to qualified evaluators under appropriate confidentiality terms.

## Evaluation

Public validation runs on 2026-05-21:

| Run | Rows | Tasks | Macro | Micro |
|---|---:|---:|---:|---:|
| One row per task | 162 | 162 | 0.9862 | 0.9862 |
| Stratified 50 per task | 8,088 | 162 | 0.9506 | 0.9507 |

Independent third-party evaluation is welcomed; the public-split results above are reproducible via the [nonnon-small-legalbench](https://github.com/NonnonLabs/nonnon-small-legalbench) repo.

## Limitations

- Not a substitute for a lawyer.
- Public LegalBench performance should not be interpreted as broad legal competence.
- Out-of-distribution prompts may produce unsupported or incomplete answers.
- Citation-heavy tasks can be sensitive to exact formatting and source availability.

## Bias And Risks

LegalBench is largely US-centric and reflects the source materials used by its task authors. NONNON-small inherits benchmark scope limitations and should be evaluated separately before use in any new jurisdiction or domain.

## License

Closed-weight model served by API. Public reproduction code is released under MIT.

## Contact

Email [labs@nonnon.ai](mailto:labs@nonnon.ai).
