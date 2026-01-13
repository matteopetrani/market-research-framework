# Market Research Framework for Product Validation

A best-in-class, domain-agnostic market research framework for validating B2C product concepts across any market.

**Originally designed for Nine Moons pregnancy app, now reusable for any product validation project.**

## What This Framework Does

This framework helps you:
- Systematically analyze competitors in your market
- Quantify market size and growth trends
- Mine user communities for pain points and demand signals
- Validate product assumptions with evidence
- Synthesize findings into actionable MVP recommendations

## Framework Structure

```
.claude/
├── README.md                              # This file
├── settings.local.json                    # Claude Code settings
├── skills/                                # Reusable research capabilities
│   ├── analyzing-competitors.md           # Analyze competitors (any market)
│   ├── discovering-hidden-competitors.md  # Find niche/adjacent competitors
│   ├── mining-community-insights.md       # Community research (Reddit, etc.)
│   ├── researching-market-opportunity.md  # Market sizing & trends
│   └── synthesizing-research.md           # Aggregate findings
└── commands/                              # Research workflows
    ├── research.md                        # /research [subcommand]
    └── synthesize.md                      # /synthesize

project root/
├── domain-config.md                       # Your market context (REQUIRED)
├── domain-config.template.md              # Template to copy
├── assumptions.md                         # Your testable hypotheses
└── assumptions.template.md                # Template to copy
```

## Configuration Files

Before starting research, you must configure two files in your project root:

### 1. domain-config.md - Market Context
Defines WHAT you're researching:
- Product name and market category
- Search keywords for discovery
- Communities to analyze (Reddit, Facebook, Discord, etc.)
- Adjacent categories to explore
- Analysis dimensions specific to your market

**Setup:** Copy `domain-config.template.md` to `domain-config.md` and customize.

### 2. assumptions.md - Testable Hypotheses
Defines WHAT you believe:
- Market assumptions (demand, size)
- Competitive assumptions (gaps, differentiation)
- User assumptions (pain points, preferences)
- Monetization assumptions (willingness to pay)
- Product assumptions (features, platforms)
- Distribution assumptions (discovery, growth)

**Setup:** Copy `assumptions.template.md` to `assumptions.md` and customize.

---

## Quick Start

### Step 0: Configure Your Domain
```bash
# 1. Copy templates
cp domain-config.template.md domain-config.md
cp assumptions.template.md assumptions.md

# 2. Edit domain-config.md with your:
#    - Product name (e.g., "FitFlow", "BudgetBuddy", "Nine Moons")
#    - Market category (e.g., "Fitness apps", "Personal finance", "Pregnancy apps")
#    - Target communities (e.g., r/fitness, r/personalfinance, r/pregnancy)
#    - Search keywords

# 3. Edit assumptions.md with your specific hypotheses
```

### Step 1: Analyze Competitors
```bash
/research competitor https://competitor1.com
/research competitor https://competitor2.com
/research competitor https://competitor3.com
# Analyze 5-10 key competitors in your market
```

### Step 2: Gather Market & User Data
```bash
/research market                # Market sizing and trends
/research community             # User insights from communities
/research hidden-competitors    # Find competitors you missed
```

### Step 3: Validate Assumptions
```bash
/research assumptions           # Test hypotheses against findings
```

### Step 4: Synthesize Findings
```bash
/synthesize                     # Executive summary
# or
/synthesize detailed            # Extended analysis with MVP specs
```

---

## Commands Reference

### `/research [subcommand]`
Execute specific research workflows.

#### `competitor <url>`
Analyze a specific competitor by URL.

**Example:**
```bash
/research competitor https://competitor-app.com
/research competitor https://apps.apple.com/app/competitor/id123456
```

Extracts features, positioning, monetization, and identifies gaps based on your domain-config.md analysis dimensions.

#### `hidden-competitors`
Discover additional competitors using search dimensions from domain-config.md. Finds niche players, international apps, and adjacent market alternatives.

#### `market`
Gather market sizing data (TAM/SAM/SOM) and trends for your market category and subcategory defined in domain-config.md.

#### `community`
Mine communities (Reddit, Facebook, Discord) specified in domain-config.md for user insights, pain points, and demand signals.

#### `assumptions`
Test hypotheses from `assumptions.md` against all research findings. Creates validation report with supporting/contradicting evidence.

**Requires:** `assumptions.md` file in project root.

---

### `/synthesize [mode]`
Aggregate findings into executive summary.

#### Default Mode
Creates `output/executive-summary.md` with:
- Market opportunity overview
- Competitive positioning
- User validation findings
- Key differentiators
- MVP recommendations
- Viability assessment
- Risk factors

#### `detailed` Mode
Creates additional planning documents:
- `output/mvp-feature-spec.md`
- `output/content-strategy.md`
- `output/validation-plan.md`
- `output/go-to-market.md`

**Prerequisites:** Complete at least 2-3 competitor analyses and market research.

---

## Skills Overview

Skills are reusable research methods that Claude loads on-demand. They read your domain-config.md to understand market context.

- **analyzing-competitors** - Single competitor analysis from URL
- **discovering-hidden-competitors** - Find niche and adjacent competitors
- **mining-community-insights** - Extract insights from online communities
- **researching-market-opportunity** - Calculate market size (TAM/SAM/SOM)
- **synthesizing-research** - Aggregate into actionable recommendations

Skills automatically adapt to your market based on domain-config.md.

---

## Research Questions to Answer

1. **Market Viability** - Is your market growing? What's the addressable niche?
2. **Competitive Gap** - What's missing from existing solutions?
3. **User Demand** - Does your target audience form a cohesive, underserved segment?
4. **Differentiation** - What makes your product unique?
5. **Monetization** - What pricing models work in this market?
6. **MVP Scope** - What's the minimum feature set to validate the concept?

---

## Output Structure

### Research Outputs (`research/` folder)
- `competitive-landscape.md` - Competitor analyses (one section per competitor)
- `market-opportunity.md` - Market sizing, trends, TAM/SAM/SOM
- `community-insights.md` - User research from communities
- `assumptions-validation.md` - Hypothesis testing with evidence

### Synthesis Outputs (`output/` folder)
- `executive-summary.md` - Viability assessment and MVP recommendations
- `mvp-feature-spec.md` (detailed mode)
- `content-strategy.md` (detailed mode)
- `validation-plan.md` (detailed mode)
- `go-to-market.md` (detailed mode)

---

## Example Configurations

### Example 1: Nine Moons (Pregnancy Apps)

**domain-config.md:**
```markdown
- Product Name: Nine Moons
- Market Category: Pregnancy apps
- Market Subcategory: Wellness & spirituality
- Target Audience: Pregnant people interested in holistic experiences
- Search Keywords: pregnancy app, holistic pregnancy, wellness pregnancy
- Reddit: r/pregnancy, r/BabyBumps, r/Spirituality
- Facebook: Pregnancy groups, spiritual communities
- Adjacent Categories: Meditation apps, wellness apps, women's health
- Analysis Dimensions: Spiritual/religious content coverage, personalization
```

**Starting competitors:**
- https://expectful.com
- https://belly.babyalbum.com
- https://stardust.app

---

### Example 2: FitFlow (Fitness Apps)

**domain-config.md:**
```markdown
- Product Name: FitFlow
- Market Category: Fitness apps
- Market Subcategory: AI-powered strength training
- Target Audience: Beginners (18-35) interested in home workouts
- Search Keywords: fitness app, strength training, AI coach, home workout
- Reddit: r/fitness, r/bodyweightfitness, r/homegym
- Facebook: Fitness challenge groups, home workout communities
- Adjacent Categories: Nutrition apps, yoga apps, running apps
- Analysis Dimensions: AI/ML personalization, exercise library depth
```

**Workflow:**
```bash
/research competitor https://apps.apple.com/app/fitbod/id1234567
/research market
/research community
/synthesize
```

---

### Example 3: BudgetBuddy (Personal Finance)

**domain-config.md:**
```markdown
- Product Name: BudgetBuddy
- Market Category: Personal finance apps
- Market Subcategory: Budgeting for millennials
- Target Audience: Millennials (25-40) seeking simple budgeting
- Search Keywords: budgeting app, expense tracking, personal finance
- Reddit: r/personalfinance, r/Fire, r/Frugal
- Facebook: Personal finance groups, millennial money communities
- Adjacent Categories: Investment apps, savings apps, banking apps
- Analysis Dimensions: Automation features, visual dashboards, gamification
```

---

## Customizing for Your Market

1. **Copy templates:**
   - `domain-config.template.md` → `domain-config.md`
   - `assumptions.template.md` → `assumptions.md`

2. **Define your domain** in domain-config.md:
   - Product name and market category
   - Communities where your users congregate
   - Keywords users search for
   - Adjacent categories that compete for attention
   - Key analysis dimensions for your market

3. **Define your assumptions** in assumptions.md:
   - What do you believe about your market?
   - What needs validation?
   - What could make or break your product?

4. **Run research commands** - they'll automatically use your domain context

5. **Synthesize findings** into executive summary and MVP plan

---

## Methodology

### Competitive Analysis
- Analyze competitors individually by URL
- Extract features, positioning, monetization
- Identify gaps based on your domain-specific analysis dimensions
- Build comparison across all analyzed competitors

### Market Research
- TAM: Total market for your category
- SAM: Serviceable market for your subcategory/niche
- SOM: Realistic addressable market (year 1-2)
- Trend analysis and growth projections

### Community Research
- Analyze communities from domain-config.md
- Extract pain points, feature requests, sentiment
- Identify user personas and demand signals
- Validate product-market fit indicators

### Assumptions Validation
- Read hypotheses from assumptions.md
- Cross-reference with research findings
- Document supporting/contradicting evidence
- Recommend additional research for untested assumptions

### Synthesis
- Cross-cutting insights across all research
- Viability assessment with evidence
- MVP recommendations with strategic rationale
- Risk identification and mitigation

---

## Workflow Best Practices

### Iterative Research
- Analyze competitors one at a time as you discover them
- Update assumptions.md as understanding evolves
- Re-run `/research assumptions` after new data
- Use `/research hidden-competitors` to expand view

### Quality Standards
- Always cite sources
- Include counter-evidence, not just confirmation
- Focus on actionable insights
- Document gaps and limitations

### Decision Making
- Review research outputs before synthesis
- Base viability on evidence, not intuition
- Identify missing research before final synthesis
- Use synthesis for go/no-go decisions

---

## Next Steps After Research

1. Review `output/executive-summary.md` for viability assessment
2. Make go/no-go decision based on evidence
3. Define MVP scope using feature recommendations
4. Plan content/feature strategy
5. Design validation experiments for untested assumptions
6. Identify beta users for initial testing
7. Begin MVP development or pivot based on findings

---

## Getting Help

- **Commands:** See [commands/](commands/) folder for detailed usage
- **Skills:** See [skills/](skills/) folder for capability definitions
- **Best Practices:**
  - [Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices)
  - [Agent Skills Documentation](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)
  - [Slash Commands Guide](https://code.claude.com/docs/en/slash-commands)

---

**Ready to start?**

1. Copy `domain-config.template.md` to `domain-config.md` and customize
2. Copy `assumptions.template.md` to `assumptions.md` and customize
3. Run `/research competitor <url>` for your first competitor
