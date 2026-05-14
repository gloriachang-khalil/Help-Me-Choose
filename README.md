# Help Me Choose

**Apple 生态顾问式选购推荐工具 / Apple Ecosystem Advisory Recommendation Tool**

## 语言 / Language

- [中文版本](#中文版本)
- [English Version](#english-version)

---

# 中文版本

Help Me Choose 是一款面向 Apple 线上选购场景的顾问式决策工具。它通过少量高价值问题，帮助用户从“我已经知道自己想买哪条产品线”过渡到“我可以更有把握地锁定具体 SKU”。

这个项目并不是把传统参数对比页换一种样式呈现，而是尝试用更接近购物顾问的方式，输出包含主推款、备选方案、推荐原因、配件联动与对比路径的完整决策结果。它的核心目标是降低用户的认知负荷和选择焦虑，让用户更快、更有信心地完成购买决策。

## 在线体验

- 产品原型：[help-me-choose-tau.vercel.app](https://help-me-choose-tau.vercel.app)
- 产品需求文档：[PRD文件.html](./PRD%E6%96%87%E4%BB%B6.html)
- 最新原型文件：[index.html](./index.html)

## 项目背景

Apple 官网并不缺少产品信息。真正的问题是，用户在面对复杂产品矩阵时，经常不知道如何把参数差异转化成自己的购买选择。

典型痛点包括：

- iPhone、MacBook、AirPods 的 SKU 层级复杂，用户容易在相邻型号之间犹豫。
- 参数对比页能说明“有什么不同”，但很难回答“为什么这款适合我”。
- 预算敏感型用户容易担心系统默认把自己推向更贵的方案。
- 升级用户更关心“这次换机值不值”，而不是简单地按价格区间筛选。

因此，这个项目关注的不是信息是否充足，而是用户能否获得足够的决策信心。

## 目标用户

本项目面向已经有 Apple 购买意图，但还没有确定具体型号的用户。

重点覆盖：

- 第一次进入 Apple 生态的用户
- 从旧设备升级的用户
- 对预算敏感、需要清楚取舍依据的用户
- 在相邻型号之间犹豫的用户，例如标准版、Plus、Pro，或 AirPods 4 与 AirPods Pro

## 核心体验

当前原型覆盖三个产品品类：

- iPhone
- MacBook
- AirPods

整体流程刻意保持简短：

1. 选择想购买的产品品类。
2. 回答该品类下的关键问题。
3. 获得一个主推款和一个备选方案。
4. 查看推荐理由、配件建议与主推/备选对比。
5. 继续跳转 Apple Store、展开对比、保存推荐摘要，或重新选择。

## 产品设计原则

### 少题高价值

每一道问题都必须真实影响最终推荐结果。流程避免冗长问卷，而是聚焦能够推动 SKU 收敛的关键信息。

### 心态优先于价格

推荐逻辑先识别用户的购买心态、硬需求和升级动机，再引入预算偏好。这样可以降低用户产生“系统在推贵款”的防御心理。

### 品类专属决策路径

不同品类使用不同的决策模型，而不是套用同一套问卷模板：

- iPhone 关注当前机型、换机原因与购买方式。
- MacBook 关注使用场景、便携性、性能余量与屏幕偏好。
- AirPods 关注搭配设备、使用场景、降噪需求、佩戴舒适度与音质偏好。

### 推荐结果可解释

结果页不仅展示商品，还必须解释为什么这个结果适合当前用户，以及为什么备选方案仍然值得考虑。

## 推荐逻辑

推荐引擎使用原生 JavaScript 实现，是一个基于规则和分数的轻量推荐系统。

整体逻辑分为三步：

1. 先排除明显不符合硬需求的选项。
2. 再根据品类专属因素对剩余 SKU 进行评分。
3. 最后生成主推款、备选款、推荐说明、配件建议与对比字段。

示例：

- 如果用户连续表达“需要降噪”，没有主动降噪的 AirPods 不应该仅因为价格更低而成为主推。
- 如果首次购买 iPhone 的用户想控制预算，标准版 iPhone 可以被解释为进入 Apple 生态的稳妥入口，而不是简单的“最低配”。
- 如果用户想要更大屏幕和更长续航，但又不想直接上 Pro，Plus 型号应该有自然的推荐路径。

## 结果页结构

结果页承担的是“收拢决策”，而不是继续堆叠商品信息。

主要模块包括：

- **主推款：** 基于用户回答得到的最适合 SKU。
- **备选方案：** 提供理性的降级、升级或替代路径。
- **推荐原因：** 用自然语言说明为什么这款适合用户。
- **升级洞察：** 尤其针对 iPhone 用户，解释这次升级是否有明显价值。
- **配件建议：** 将单个商品推荐延伸为更完整的购买方案。
- **主推 vs 备选对比：** 帮助用户理解两个选择之间的 trade-off。
- **保存摘要：** 让用户可以复制一段简洁的推荐结果。

## 版本演进

仓库中保留了从 V1 到 V8.2 的历史版本，用于展示产品从最小原型到当前版本的演进过程。

关键节点：

- **V1：** 完成欢迎页、问卷和结果页闭环，形成最小可运行原型。
- **V3：** 引入预算状态和购买心态，避免系统总是给出同一个“稳妥答案”。
- **V5-V6：** 将 iPhone 路径从预算筛选器重构为升级顾问逻辑。
- **V7-V8.2：** 修正 SKU 语义、历史参考价表达和中间档推荐路径。

这个项目最大的迭代价值不只是页面越来越完整，而是推荐逻辑逐渐更接近真实用户的选择方式：先修问题定义，再修规则结构，最后修商品语义和取舍表达。

## 成功指标

如果项目进入真实产品验证阶段，可以重点观察：

- 引导流程完成率
- 推荐结果点击率
- 配件联动点击率
- 主推/备选对比点击率
- 重新来过比例

这些指标可以帮助判断工具是否真的提升了决策信心、减少犹豫，并带来商业价值。

## 技术实现

这是一个静态前端原型，使用：

- HTML
- CSS
- Vanilla JavaScript
- Vercel 静态部署

项目不依赖框架，也不需要构建流程。

## 仓库结构

```text
.
├── index.html              # 最新 Help Me Choose 产品原型
├── index-v1.html           # 历史原型版本
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
└── PRD文件.html             # 展示产品思考与迭代逻辑的 PRD 文件
```

## 本地运行

因为项目是静态页面，可以直接用浏览器打开 `index.html`。

也可以启动一个简单本地服务：

```bash
python3 -m http.server 8000
```

然后打开：

```text
http://localhost:8000
```

## 项目展示的能力

这个项目是一个产品经理作品集案例，重点展示：

- 围绕真实购买决策痛点的问题定义能力
- 以用户心智为中心的决策流程设计
- SKU 级别的产品逻辑和 trade-off 思考
- 基于反馈持续迭代的能力
- 可解释推荐结果的表达能力
- 轻量前端原型实现能力

## 下一步优化

后续可以继续推进：

- 为每一步决策链路加入埋点。
- 扩大首次 Apple 用户和预算敏感用户的外部测试。
- 进一步细化 iPhone 升级树，让“当前机型 → 换机动因”的判断更真实。
- 优化 Plus 和中间档 SKU 的推荐路径。
- 增加产品图片或官方视觉占位，让结果页更接近真实电商体验。
- 将规则型推荐逻辑重构为更易维护的数据驱动结构。

## 免责声明

本项目是独立作品集原型，与 Apple 无官方关联。项目中出现的产品名称仅用于展示决策流程设计和推荐逻辑。

---

# English Version

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
