# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a domain-agnostic market research framework for validating B2C product concepts. Built with Claude Code using Agent Skills and Slash Commands, it enables systematic validation of product ideas across any market through competitive analysis, market sizing, community research, and assumption testing.

## Key Architecture

### Configuration-Driven Design

The framework separates domain-specific context from reusable research methods:

- **`domain-config.md`** (required): Defines the market context - product name, target communities (Reddit/Facebook/Discord), search keywords, adjacent categories, and analysis dimensions specific to the market being researched.

- **`assumptions.md`** (required): Contains testable hypotheses about the market, competitive gaps, user needs, monetization, product features, and distribution strategies.

- **`.claude/skills/`**: Five reusable research capabilities that automatically adapt to any market by reading domain-config.md:
  - `analyzing-competitors.md`: Deep analysis of individual competitors from URLs
  - `discovering-hidden-competitors.md`: Finds niche/adjacent competitors using domain search dimensions
  - `mining-community-insights.md`: Extracts insights from configured communities
  - `researching-market-opportunity.md`: Calculates TAM/SAM/SOM for the market
  - `synthesizing-research.md`: Aggregates findings into executive summary

- **`.claude/commands/`**: Slash command workflows that orchestrate skills:
  - `research.md`: `/research [subcommand]` for executing targeted research
  - `synthesize.md`: `/synthesize [mode]` for creating synthesis outputs

### Output Structure

Research outputs are generated in gitignored directories:

- **`research/`**: Raw research findings
  - `competitive-landscape.md`: Competitor analyses (one section per competitor)
  - `market-opportunity.md`: Market sizing and trends
  - `community-insights.md`: User research from communities
  - `assumptions-validation.md`: Hypothesis testing results

- **`output/`**: Synthesis documents
  - `executive-summary.md`: Viability assessment and MVP recommendations
  - Additional detailed specs when using `/synthesize detailed`

## Common Workflows

### Initial Setup (for new domains)
```bash
# Copy templates and customize for the target market
cp domain-config.template.md domain-config.md
cp assumptions.template.md assumptions.md

# Edit both files with market-specific information
```

### Research Execution
```bash
# Analyze known competitors (run for each competitor)
/research competitor https://competitor-url.com

# Discover additional competitors
/research hidden-competitors

# Gather market data
/research market

# Mine user communities
/research community

# Validate assumptions against findings
/research assumptions

# Create executive summary
/synthesize

# Or create detailed specs
/synthesize detailed
```

## Important Implementation Notes

### Skills Must Read domain-config.md First

All research skills MUST begin by reading and parsing `domain-config.md` from the project root. This file contains:
- Product name and market category/subcategory
- Target communities to analyze
- Search keywords for discovery
- Adjacent categories
- Analysis dimensions for competitive evaluation

Skills should extract this context and use it to adapt their research methodology to the specific market.

### Research Outputs Are Append-Only

When adding findings to research files:
- ALWAYS append new sections, never overwrite existing content
- Each competitor analysis gets its own section in `competitive-landscape.md`
- Use clear section headers with competitor names/dates
- Cite all sources

### Assumptions Validation Requires Prior Research

The `/research assumptions` command requires that other research has already been completed. It cross-references hypotheses from `assumptions.md` against existing findings in `research/` folder.

### Synthesis Requires Minimum Research Depth

The `/synthesize` command requires at least:
- 2-3 competitor analyses in `research/competitive-landscape.md`
- Market opportunity data in `research/market-opportunity.md`
- Community insights (preferred but not strictly required)

## Configuration Files

### domain-config.md Structure
```markdown
## Project Identity
- Product Name: [Name]
- Market Category: [Primary category]
- Market Subcategory: [Niche/focus area]
- Target Audience: [Description]

## Search Keywords
[List of primary search terms]

## Key Communities
[Reddit subreddits, Facebook groups, Discord servers, forums]

## Adjacent Categories
[Related markets that compete for attention]

## Competitor Discovery Dimensions
[Search angles for finding competitors]

## Analysis Dimensions
[Key aspects to evaluate in competitors]
```

### assumptions.md Structure

Organized by category:
- Market Assumptions (demand, size)
- Competitive Assumptions (gaps, differentiation)
- User Assumptions (pain points, preferences)
- Monetization Assumptions (pricing, willingness to pay)
- Product Assumptions (features, platforms)
- Distribution Assumptions (discovery, growth)

Each assumption includes:
- Statement of belief
- Why it matters
- Validation criteria

## Working Example

The repository includes a complete working example for "Nine Moons," a pregnancy app focused on wellness/spirituality. This serves as a reference implementation showing:
- How to configure domain-config.md for a specific market
- How to structure assumptions for hypothesis testing
- The type of insights each skill should generate

## Key Design Principles

1. **Domain-Agnostic**: Skills use domain-config.md to adapt to any market without code changes
2. **Evidence-Based**: All claims must cite sources; include counter-evidence
3. **Iterative**: Research can be run incrementally as competitors are discovered
4. **Reusable**: The same framework validates pregnancy apps, fitness apps, finance apps, etc.
5. **Actionable**: Output should lead to clear go/no-go decisions and MVP scoping

## WebSearch Permission

This framework heavily relies on WebSearch for gathering competitive intelligence, market data, and community insights. The `.claude/settings.local.json` file includes WebSearch in allowed permissions.
