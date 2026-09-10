# Official Adaption source routing

Use this reference for implementation, debugging, documentation contribution, or workflows spanning multiple Adaption areas. Do not load it for a narrow factual answer.

## Source hierarchy

1. Use `docs.adaptionlabs.ai` guides for the intended workflow and conceptual behavior.
2. Use the generated API reference under `docs.adaptionlabs.ai/api` for exact REST schemas, current limits, response fields, and Python SDK signatures.
3. Use `github.com/adaptionlabs/adaption-api-docs` for documentation-source questions, raw MDX, navigation, validation, and the committed OpenAPI inputs.

The documentation site is built from the repository with Astro, Starlight, and Stainless. Authored guides live in `src/content/docs/`. The API reference is generated at build time from `spec/openapi.json` and `spec/openapi.stainless.yml`; those spec files are synchronized from the API source and should not be edited by hand in the docs repository. For a reference defect, identify the endpoint and report the mismatch instead of patching the generated spec.

## Adaptive Data invariants

- The SDK reads `ADAPTION_API_KEY` automatically when constructing `Adaption()`.
- `datasets.create` can import provider data or initiate a local upload. A local upload is not complete until the bytes are PUT to the presigned URL and the upload is confirmed with size and SHA-256.
- Ingestion is asynchronous. Wait until status indicates imported rows are available, and surface `error_data` if it fails.
- `processing_mode="adapt"` is the normal Adaptive Data path. Use `processing_mode="raw"` only for already training-ready tabular prompt/completion data that intentionally skips adaptation.
- Map source columns to the semantic roles expected by the run. Request an estimate with the exact configuration before submitting the paid run.
- `datasets.download(...)` returns response content, not a link. Use `.write_to_file(...)`, `.read()`, `.text()`, or the streaming response as appropriate to the current SDK version.
- Parquet download output is a gzipped tar archive of shards; name and extract it accordingly.

## AutoScientist invariants

- Prefer a dataset that has completed Adaptive Data. A raw dataset is an explicit alternative, not the default recommendation.
- Use a model ID returned by `autoscientist.list_models()` when the user requires a specific supported model. Otherwise allow platform selection.
- Omit `column_mapping` when platform inference is appropriate. If provided, map columns in the processed dataset schema, not blindly from the original uploaded headers.
- Use an idempotency key when a create request could be retried.
- Wait for `succeeded`, `failed`, or `cancelled`; inspect the error on non-success and inspect `best_win_rate` on success.
- Download only when `download_available` is true. The archive contains the best iteration checkpoint, which may not be the final iteration.

## Implementation checks

- Confirm the installed `adaption` package version before copying an example whose response shape or helper method is version-dependent.
- Prefer the SDK's typed methods and streaming helpers over reimplementing REST plumbing. Use direct HTTP only when requested or when the SDK does not expose the needed current endpoint.
- For large jobs, use bounded waits or durable job tracking rather than an infinite local loop.
- Separate code failures from ingestion, authentication, quota, credit, model-support, and remote-job failures in the explanation.

## Documentation repository map

- `src/content/docs/`: authored guides and tutorials
- `astro.config.ts`: redirects, navigation, and site integration
- `spec/openapi.json`: generated public OpenAPI document
- `spec/openapi.stainless.yml`: generated API-reference configuration
- `scripts/check_snippets.py`: Python example validation
- `CONTRIBUTING.md`: authoring and pull-request checks

When editing docs, change the canonical current page rather than adding a compatibility page for an obsolete path. Run the repository's documented validation and build commands, and verify the rendered page when layout or navigation changes.
