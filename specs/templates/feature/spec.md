---
status: draft
created: {{YYYY-MM-DD}}
updated: {{YYYY-MM-DD}}
# requires:
#   - {{spec-folder-name}}
---

# {{Feature Name}}

## User Story

> As a {{persona}}, I want to {{action}}, so that {{benefit}}.

_1–3 sentences. Non-technical. Immediately understandable by a non-developer._

## Acceptance Criteria

- [ ] **Given** {{precondition}}, **When** {{action}}, **Then** {{expected outcome}}
- [ ] **Given** {{precondition}}, **When** {{action}}, **Then** {{expected outcome}}

## Personas

- **{{Persona}}** — {{brief description of their role in this feature}}

## UI / Visual Design

_Optional. Omit for non-UI features (CLI tools, background services, APIs). Replace with a "Behaviour" section if more appropriate._

_Describe screens, flows, and interactions. Include mockup references or design links if available._

### {{Screen Name}}

- {{UI element or behavior}}
- {{UI element or behavior}}

### Error States

- {{Error condition}}: "{{Error message shown to user}}"

## Interfaces & Contracts

_Define the interfaces or data contracts this feature introduces or depends on. Format depends on your project: REST endpoints, GraphQL queries, CLI commands, message schemas, function signatures, etc._

### `{{METHOD}} /{{path}}`

**Request:**
```json
{
  "field": "type"
}
```

**Response (200):**
```json
{
  "field": "type"
}
```

**Error ({{status}}):** {{description}}

## Constraints & Edge Cases

- {{Edge case or constraint}}
