# Help Me Choose

**Apple Ecosystem Advisory Recommendation Tool**

Help Me Choose is a guided product decision tool for Apple online shopping scenarios. It helps users move from "I know which product line I want" to "I can confidently choose a specific SKU" through a short, high-value questionnaire.

Unlike a traditional spec comparison page, the project behaves more like a lightweight shopping advisor. It returns a primary recommendation, an alternative option, a clear "why", accessory suggestions, and a comparison path so users can understand the trade-off behind the answer.

## Live Demo

- Product prototype: [help-me-choose-tau.vercel.app](https://help-me-choose-tau.vercel.app)
- Product requirement document: [PRD文件.html](./PRD%E6%96%87%E4%BB%B6.html)
- Latest prototype file: [index.html](./index.html)

## Product Problem

Apple's online store already provides rich product information, but users still face a decision gap:

- The product matrix is complex, especially across iPhone, MacBook, and AirPods.
- Spec tables explain differences, but rarely answer: "Why is this model right for me?"
- Budget-sensitive users may feel that recommendation systems are pushing them toward more expensive products.
- Upgrade users care less about generic price tiers and more about whether the next purchase is actually worth it.

The core product challenge is not information availability. It is decision confidence.

## Target Users

The project focuses on users who already have Apple purchase intent but are unsure which exact model fits their needs.

Primary user groups:

- First-time Apple ecosystem entrants
- Users upgrading from older Apple devices
- Budget-conscious shoppers who need a clear trade-off
- Users choosing between nearby SKUs, such as standard vs. Plus vs. Pro, or AirPods 4 vs. AirPods Pro

## Core Experience

The current prototype covers three product categories:

- iPhone
- MacBook
- AirPods

The flow is intentionally short:

1. Choose a product category.
2. Answer category-specific questions.
3. Receive a primary recommendation and an alternative.
4. Review the recommendation rationale, accessories, and comparison table.
5. Continue to Apple Store, compare options, save the recommendation, or restart.

## Product Principles

### High-ROI Questions

Every question is designed to affect the final recommendation. The flow avoids long surveys and focuses on inputs that materially change the SKU decision.

### Mindset Before Price

The recommendation logic first identifies user intent, hard needs, and upgrade motivation before introducing budget preference. This reduces the feeling of being "sold to".

### Category-Specific Decision Paths

Each category uses a different decision model:

- iPhone focuses on current device, upgrade reason, and purchase mindset.
- MacBook focuses on work scenario, portability, performance, and screen preference.
- AirPods focuses on device pairing, use scenario, noise cancellation, comfort, and sound needs.

### Explainable Output

The result page does not only show a product. It explains why the product fits the user's situation and why the alternative may still be worth considering.

## Recommendation Logic

The recommendation engine is implemented as a rule-based scoring system in vanilla JavaScript.

It follows three broad steps:

1. Exclude options that clearly violate hard requirements.
2. Score remaining products based on category-specific decision factors.
3. Generate a primary recommendation, an alternative, explanation copy, accessories, and comparison fields.

Examples:

- If a user repeatedly expresses a need for noise cancellation, AirPods without ANC should not win purely because they are cheaper.
- If a first-time iPhone buyer wants to enter the ecosystem with controlled budget, a standard iPhone can be framed as a stable entry point rather than "just the cheapest option".
- If a user wants a larger screen and longer battery life but does not want to jump to Pro, a Plus model should have a natural recommendation path.

## Result Page Structure

The result page is designed to close the decision loop:

- **Primary recommendation:** the best-fit SKU for the user's answers.
- **Alternative option:** a rational fallback or upgrade path.
- **Why explanation:** plain-language reasoning behind the recommendation.
- **Upgrade insight:** especially for iPhone users, explains whether the upgrade is meaningful.
- **Accessory suggestions:** turns a single-product recommendation into a more complete purchase solution.
- **Comparison table:** helps users understand the trade-off between the primary and alternative option.
- **Save summary:** lets users copy a concise recommendation summary.

## Version Evolution

The repository keeps historical prototype files from V1 to V8.2 to show how the product evolved.

Key iteration milestones:

- **V1:** Built the minimum runnable prototype with welcome page, questionnaire, and result page.
- **V3:** Added budget state and purchase mindset to avoid defaulting to one "safe" answer.
- **V5-V6:** Reworked the iPhone path from a budget selector into an upgrade advisor.
- **V7-V8.2:** Refined SKU semantics, historical reference pricing, and middle-tier recommendation paths.

The main learning from the iteration was that the hardest part was not UI polish. It was making the decision logic feel like it understood the user's trade-off.

## Success Metrics

If this were moved beyond prototype stage, the key metrics would be:

- Guided flow completion rate
- Recommendation click-through rate
- Accessory attach rate
- Compare click-through rate
- Restart rate

These metrics would help evaluate whether the tool improves confidence, reduces hesitation, and supports commercial outcomes.

## Technical Implementation

This is a static front-end prototype built with:

- HTML
- CSS
- Vanilla JavaScript
- Vercel static deployment

No framework or build step is required.

## Repository Structure

```text
.
├── index.html              # Latest Help Me Choose prototype
├── index-v1.html           # Historical prototype versions
├── index-v2.html
├── index-v3.html
├── index-v4.html
├── index-v4-claude.html
├── index-v5.html
├── index-v6.html
├── index-v7.html
├── index-v8.html
├── index-v8.1.html
├── index-v8.2.html
└── PRD文件.html             # Portfolio PRD for product thinking and iteration rationale
```

## Run Locally

Because the project is static, you can open `index.html` directly in a browser.

Or run a simple local server:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

## What This Project Demonstrates

This project was built as a product management portfolio case. It demonstrates:

- Problem definition around a real online purchase decision gap
- User-centered decision flow design
- SKU-level product logic and trade-off thinking
- Iterative improvement based on feedback
- Recommendation explainability
- Lightweight front-end prototyping

## Next Steps

Planned improvements:

- Add analytics events for each decision step.
- Expand external testing with first-time Apple buyers and budget-sensitive users.
- Refine iPhone upgrade logic with more granular current-device conditions.
- Improve Plus and mid-tier SKU paths.
- Add visual product cards or official product imagery placeholders.
- Convert the rule-based recommendation logic into a more maintainable data-driven structure.

## Disclaimer

This is an independent portfolio prototype and is not affiliated with Apple. Product names and references are used only to demonstrate decision-flow and recommendation design.
