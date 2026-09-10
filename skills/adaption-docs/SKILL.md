---
name: "adaption-docs"
description: "Use for current, source-grounded guidance about Adaption, Adaptive Data, AutoScientist, the Adaption Python SDK and REST API, or the adaption-api-docs repository. Do not use for generic data preparation or model-training questions that do not involve Adaption."
---

# Adaption Docs

Provide current, cited Adaption product, SDK, API, and documentation-repository guidance. Read zero or one bundled reference.

**First substantive action:** Use the agent's available web or HTTP retrieval capability to open the official source selected by the route below. If no exact page is known, search the user's exact topic in the official Adaption documentation, then open the matching page. Use the fetched page, not a search snippet. For exact request fields, response fields, accepted values, limits, or SDK signatures, open the corresponding current API reference page. Complete this source lookup before inspecting local code or answering from memory. If official sources cannot be fetched, state that current behavior could not be verified.

For a straightforward factual or citation-only request, follow the source order and do not read a bundled reference. For implementation, debugging, documentation contribution, or a workflow that spans more than one Adaption area, read [official source routing](references/official-docs.md).

## Choose one primary route

Use the first matching route. Open only the pages needed to answer the request.

- **Supplied official documentation URL:** Open it directly, then follow relevant links if more evidence is needed.
- **Documentation source or contribution:** Use the official [adaption-api-docs repository](https://github.com/adaptionlabs/adaption-api-docs), then inspect only the relevant authored MDX, OpenAPI, configuration, or validation file.
- **Exact API or Python SDK behavior:** Go directly to the relevant endpoint in the generated [API and SDK reference](https://docs.adaptionlabs.ai/api). Prefer the Python variant for Python questions and the HTTP variant for REST questions. No quickstart is required.
- **Adaptive Data workflow:** Start with the [Adaptive Data quickstart](https://docs.adaptionlabs.ai/adaptive-data-quickstart), then open the specific guide or endpoint involved.
- **AutoScientist workflow:** Start with the [AutoScientist quickstart](https://docs.adaptionlabs.ai/autoscientist-quickstart), then open the specific guide or endpoint involved.

## Source and execution boundaries

- Use only `docs.adaptionlabs.ai`, `adaptionlabs.ai`, and `github.com/adaptionlabs/adaption-api-docs` for claims about Adaption. Link each material claim to the page that directly supports it.
- Prefer the current generated API reference for exact schemas and limits. If sources disagree, including within the reference, check the relevant endpoint schema and the installed SDK version and types before choosing behavior. State the discrepancy and the evidence for the choice. If it remains unresolved, say so and do not present dependent code as verified.
- Preserve the user's requested product, model, data path, training type, and processing mode. Do not silently substitute a different workflow.
- Never print, commit, or embed an API key. Prefer `ADAPTION_API_KEY`; use a secret manager for deployed systems.
- Before running Adaptive Data, request an estimate with the intended configuration. Do not start a credit-consuming adaptation or AutoScientist run unless the user authorized that external action.
- Treat dataset ingestion, adaptation, evaluation, and AutoScientist training as asynchronous. Check terminal failure states and avoid unbounded polling.
- Stream large dataset exports and model checkpoints. Do not assume a download response is a URL or that a Parquet export is a single `.parquet` file.
- Say "Adaption Docs" or "official Adaption documentation" in user-facing answers. Keep examples and citations concise.
