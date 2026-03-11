# EvaL Schema

JSON Schema for the Evaluation Language (EvaL) - a format for defining AI evaluation instructions and capturing structured results with proof chains.

## Overview

EvaL provides a standardized way to:

- **Define evaluation instructions** with multi-step workflows and proof requirements
- **Capture evaluation results** with structured data and evidence chains
- **Enable AI agents** to execute evaluations via MCP (Model Context Protocol)

## Schema

The schema is available at `schema.json` and defines two main document types:

- **Instruction** - Evaluation steps, proof requirements, and result schemas
- **Evaluation** - Results with status, structured data, and proof chains

## Usage

Reference the schema in your YAML/JSON documents:

```yaml
# yaml-language-server: $schema=https://raw.githubusercontent.com/evaluationlanguage/schema/v0.2.0/schema.json
title: My Evaluation Instructions
schemaVersion: "0.2.0"
steps:
  - name: Verify claim
    description: Check if the claim is supported by evidence
    proofRequirement: Quote the relevant source text
```

## Schema Features

### Result Types

Instructions steps support structured result schemas with these types: `string`, `number`, `boolean`, `enum`, `object`, `array`, `table`.

### v0.2.0 Additions

- **enumColors** - Custom hex color mapping for enum values (ResultSchema, FieldSchema, ColumnSchema)
- **multiSelect** - Multi-selection mode for enum types
- **predefinedItems** - Predefined items for checklist and scored list patterns
- **scoreMin / scoreMax** - Score range bounds for scored lists
- **proofType** - Step-level proof type constraint (`text`, `photo`, `file`, `any`)

All v0.2.0 additions are optional fields, making the schema fully backwards-compatible with v0.1.0 documents.

## Examples

See the `examples/` directory for real-world evaluation patterns:

- **Patent Claim Analysis** - EPO-style novelty assessment with X/Y categorization
- **GDP Comparison** - Economic data validation using World Bank methodology
- **SLA Compliance Audit** - Service level agreement verification with breach tracking

## Origin

Created as submission for the [EPO Codefest 2026](https://www.epo.org/).

## License

MIT License - see [LICENSE](LICENSE) for details.
