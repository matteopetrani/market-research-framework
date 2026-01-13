# Synthesize Command

Aggregate research findings into actionable executive summary with viability assessment and MVP recommendations.

## Usage

`/synthesize $ARGUMENTS`

## Modes

### Default (no arguments)
Create concise executive summary with key findings and MVP recommendations.

Use the `synthesizing-research` skill to read all files in `research/` folder and create `output/executive-summary.md` with:
- Market opportunity overview
- Competitive positioning
- User validation findings
- Key differentiators
- MVP feature recommendations
- Viability assessment (go/no-go framework)
- Risk factors and mitigations
- Next steps

### `detailed`
Create extended synthesis with multiple planning documents.

In addition to executive summary, generate:
- `output/mvp-feature-spec.md` - Prioritized MVP feature requirements with rationale
- `output/content-strategy.md` - Content and editorial approach
- `output/validation-plan.md` - Experiments to test key assumptions
- `output/go-to-market.md` - Initial user acquisition strategy

## Prerequisites

Before running synthesis, ensure you have completed:
- **Minimum:** At least 2-3 `/research competitor <url>` analyses and `/research market`
- **Recommended:** `/research community` and `/research assumptions` (requires `assumptions.md` in project root)
- **Optional:** `/research hidden-competitors` for expanded competitive view

Note: If you have an `assumptions.md` file in the project root, the synthesis will incorporate assumption validation results.

## Instructions for Claude

When the user runs `/synthesize`:

1. Read `domain-config.md` from project root to understand product name, market context, and key differentiators
2. Verify that research files exist in the `research/` directory
3. Check if `assumptions.md` exists in the project root and include it in synthesis if available
4. If insufficient research data, inform the user which research areas are missing and recommend completing them first
5. Use the `synthesizing-research` skill to read and aggregate all research findings
6. Extract cross-cutting insights and identify key themes
7. Create viability assessment based on evidence from research
8. Generate actionable MVP recommendations with strategic rationale
9. For `detailed` mode, create additional planning documents
10. Provide brief summary of key findings and viability conclusion
11. Suggest next steps based on the viability assessment

Note: Synthesis will overwrite existing files in `output/` directory. Warn user if files already exist.
