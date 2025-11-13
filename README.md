# Civic Interconnect P-Tag Schemas

This repository provides JSON Schemas for machine-readable provenance tags ("PTags") used across Civic Interconnect.

-   `ptag.core.schema.json` - minimal, PROV-aligned schema for software, tools, and specs
-   `ptag.civic-data.schema.json` - adds civic-data attributes for datasets and apps
-   `ptag.privacy.schema.json` - see <https://github.com/civic-interconnect/civic-transparency-ptag-spec> for earlier draft

## Unversioned URIs

-   <https://raw.githubusercontent.com/civic-interconnect/civic-ptag-core-schema/main/schema/ptag.core.schema.json>
-   <https://raw.githubusercontent.com/civic-interconnect/civic-ptag-core-schema/main/schema/ptag.civic-data.schema.json>
-   <https://raw.githubusercontent.com/civic-interconnect/civic-ptag-core-schema/main/schema/ptag.privacy.schema.json>

## Versioning

-   publish component tag like `ptag-core@1.0.0`
-   publish component tag like `ptag-civic-data@1.0.0`

Reference them from repos via:

-   `https://raw.githubusercontent.com/civic-interconnect/civic-ptag-core-schema/ptag-core@1.0.0/schema/ptag.core.schema.json`
-   `https://raw.githubusercontent.com/civic-interconnect/civic-ptag-core-schema/ptag-civic-data@1.0.0/schema/ptag.civic-data.schema.json`

## Local Validation

Required: Node.js (v24).

Open Git Bash / bash / zsh terminal:

```shell
npx ajv-cli validate --spec=draft2020 -s schema/ptag.core.schema.json  -d examples/core-lib_ptag.json

npx ajv-cli validate --spec=draft2020 -r schema/ptag.core.schema.json -s schema/ptag.civic-data.schema.json -d examples/civic-data_dataset_ptag.json

npx ajv-cli validate --spec=draft2020 --strict=false -s schema/ptag.privacy.schema.json -d examples/privacy_ptag.json
```

## Reuse of Core Schema

Currently, only the `civic-data` profile formally extends the core schema via `$ref`.

The `ptag.privacy.schema.json` profile is intentionally independent.
While `ptag.core` and `ptag.civic-data` describe full PROV-structured provenance graphs, the privacy profile defines a small, flat set of bucketed, non-PII attributes intended for per-post tagging.
Requiring it to extend the core schema would force all privacy tags into full PROV graph structures (prefix, entity, activity, wasGeneratedBy, etc.), making them heavier and harder to adopt in platform-level pipelines.
Keeping the privacy profile standalone provides:

-   a simple, embeddable JSON object for social-post metadata
-   no required PROV boilerplate
