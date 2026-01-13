# Market Research Framework

A best-in-class, domain-agnostic market research framework for validating B2C product concepts across any market.

Built with [Claude Code](https://code.claude.com) using Agent Skills and Slash Commands.

## What This Framework Does

This framework helps you systematically:
- 🔍 Analyze competitors in any market
- 📊 Quantify market size and growth trends (TAM/SAM/SOM)
- 👥 Mine user communities for pain points and demand signals
- ✅ Validate product assumptions with evidence
- 📝 Synthesize findings into actionable MVP recommendations

## Quick Start

### 1. Install Prerequisites
- [Claude Code](https://code.claude.com) (requires Claude Pro, Team, or Enterprise)

### 2. Configure Your Domain
```bash
# Copy templates and customize
cp domain-config.template.md domain-config.md
cp assumptions.template.md assumptions.md

# Edit domain-config.md with your:
# - Product name and market category
# - Target communities (Reddit, Facebook, Discord)
# - Search keywords
# - Adjacent categories
```

### 3. Run Research
```bash
# Analyze competitors
/research competitor https://competitor1.com
/research competitor https://competitor2.com

# Gather market and user data
/research market
/research community
/research hidden-competitors

# Validate assumptions
/research assumptions

# Synthesize findings
/synthesize
```

## Features

### Domain-Agnostic Design
Works for any B2C product validation:
- **Pregnancy apps** (original use case: Nine Moons)
- **Fitness apps** (example: FitFlow)
- **Personal finance** (example: BudgetBuddy)
- **Or any other market** - just configure domain-config.md

### Configuration-Driven
All domain-specific information lives in two config files:
- **`domain-config.md`** - Market context (product, communities, keywords)
- **`assumptions.md`** - Testable hypotheses about your market

### Reusable Research Methods
5 specialized skills that adapt to your market:
- `analyzing-competitors` - Deep competitor analysis from URLs
- `discovering-hidden-competitors` - Find niche and adjacent competitors
- `mining-community-insights` - Extract insights from online communities
- `researching-market-opportunity` - Calculate TAM/SAM/SOM
- `synthesizing-research` - Aggregate findings into executive summary

### Slash Commands
Simple workflows via Claude Code commands:
- `/research competitor <url>` - Analyze specific competitor
- `/research market` - Gather market sizing data
- `/research community` - Mine user communities
- `/research assumptions` - Validate hypotheses
- `/synthesize` - Create executive summary

## Example Use Cases

### Nine Moons (Pregnancy App)
Validating a pregnancy app with spiritual/wellness content.

**Domain Config:**
- Market: Pregnancy apps → Wellness & spirituality
- Communities: r/pregnancy, r/BabyBumps, r/Spirituality
- Keywords: holistic pregnancy, spiritual pregnancy
- Analysis Dimensions: Spiritual content coverage, personalization

### FitFlow (Fitness App)
Validating an AI-powered strength training app.

**Domain Config:**
- Market: Fitness apps → AI-powered strength training
- Communities: r/fitness, r/bodyweightfitness, r/homegym
- Keywords: fitness app, strength training, AI coach
- Analysis Dimensions: AI/ML personalization, exercise library

### BudgetBuddy (Personal Finance)
Validating a budgeting app for millennials.

**Domain Config:**
- Market: Personal finance apps → Budgeting for millennials
- Communities: r/personalfinance, r/Fire, r/Frugal
- Keywords: budgeting app, expense tracking
- Analysis Dimensions: Automation features, visual dashboards

## Documentation

Complete documentation available in `.claude/README.md`:
- Detailed setup instructions
- Command reference
- Skills overview
- Methodology
- Best practices

## Output Structure

The framework generates organized research outputs:

```
research/
├── competitive-landscape.md    # Competitor analyses
├── market-opportunity.md        # Market sizing (TAM/SAM/SOM)
├── community-insights.md        # User research
└── assumptions-validation.md    # Hypothesis testing

output/
├── executive-summary.md         # Viability assessment
├── mvp-feature-spec.md          # MVP recommendations
├── content-strategy.md          # Content approach
└── validation-plan.md           # Next steps
```

## Technology

Built with:
- [Claude Code](https://code.claude.com) - AI-powered CLI
- [Agent Skills](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) - Reusable capabilities
- [Slash Commands](https://code.claude.com/docs/en/slash-commands) - Custom workflows

## Origin Story

Originally designed to validate [Nine Moons](domain-config.md), a pregnancy app with spiritual/religious content. Refactored to be domain-agnostic and reusable across any B2C product validation.

## License

MIT License - feel free to use for any product validation project.

## Contributing

Contributions welcome! Areas for improvement:
- Additional example configurations
- Enhanced analysis dimensions for specific markets
- Integration with other research tools
- Documentation improvements

## Author

Created with Claude Code by Matteo Petrani

---

**Ready to validate your product idea?**

1. Clone this repo
2. Copy config templates
3. Customize for your market
4. Run `/research` commands
5. Get data-driven validation

Good luck building! 🚀
