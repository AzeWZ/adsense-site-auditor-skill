# AdSense Site Auditor Skill

Codex skill for auditing whether a website is ready to apply for Google AdSense.

The skill converts Google AdSense Help, AdSense Program policies, Google Publisher Policies, and Google Publisher Restrictions into an exhaustive website audit checklist.

## What It Checks

- AdSense eligibility and account readiness
- Site ownership and verification readiness
- Original content, low-value content, copied content, and ad/content ratio
- Navigation, UX, deceptive buttons, redirects, and popup behavior
- Crawler access, robots.txt, WAF, login walls, DNS, redirects, and POST-only pages
- AdSense Program policies
- Google Publisher Policies
- Google Publisher Restrictions
- Privacy policy, cookies, PII, EU consent, COPPA, and personalized ads restrictions

The current checklist contains 73 requirement IDs. Every audit must mark each ID as `Pass`, `Fail`, `Unknown`, or `N/A`.

## Explicit Invocation

Preferred:

```text
@adsense-site-auditor
```

Fallback for Codex surfaces that use dollar-style skill invocation:

```text
$adsense-site-auditor
```

## Minimal Prompt

```text
@adsense-site-auditor Audit https://example.com for Google AdSense application readiness. You must cover every ADS-* requirement ID and output a complete Pass/Fail/Unknown/N/A table.
```

## Chinese Prompt

```text
@adsense-site-auditor 审计 https://example.com 是否符合 AdSense 申请要求。必须逐项覆盖所有 ADS-* 检查项，并输出完整 Pass/Fail/Unknown/N/A 表。
```

## Install

Copy the skill folder into your Codex skills directory:

```bash
cp -R adsense-site-auditor ~/.codex/skills/
```

Or unpack the zip package:

```bash
unzip dist/adsense-site-auditor-skill-2026-06-16.zip -d ~/.codex/skills/
```

## Files

- `adsense-site-auditor/SKILL.md` - skill entry point and audit workflow
- `adsense-site-auditor/references/adsense-requirements.md` - exhaustive AdSense checklist
- `adsense-site-auditor/references/usage-prompts.md` - ready-to-copy prompts
- `adsense-site-auditor/agents/openai.yaml` - UI metadata
- `dist/adsense-site-auditor-skill-2026-06-16.zip` - packaged skill

## Important

This skill does not guarantee Google AdSense approval. Before a serious audit, refresh the official Google documentation because AdSense policies can change. If official Google documentation conflicts with this skill, the official documentation wins.


Full Website Audit
@adsense-site-auditor 请完整审计这个网站是否适合申请 Google AdSense：

URL: https://example.com
阶段：申请前

要求：
1. 必须逐项检查所有 ADS-* 要求 ID。
2. 每一项都必须标记 Pass / Fail / Unknown / N/A。
3. 不允许只给摘要，不允许省略看起来不相关的项目。
4. 输出 Blocker / High / Medium 风险，并给每项的证据和修复建议。
5. 最后做 Completeness Check，确认报告覆盖了全部要求 ID。
Live URL Only
仓库地址
@adsense-site-auditor 只基于线上可访问页面审计这个站是否能申请 AdSense：

URL: https://example.com

请抓取首页、robots.txt、sitemap、隐私政策、About/Contact、分类页和代表性内容页。
如果某项必须依赖 AdSense 后台、服务器配置或站长确认，请标为 Unknown，并说明需要什么证据。
Repo Plus Live Site Audit
@adsense-site-auditor 结合本地代码仓库和线上站点，审计 AdSense 申请准备情况：

线上 URL: https://example.com
本地仓库: /absolute/path/to/repo
阶段：申请前

请同时检查：
- 渲染后的页面和抓取可访问性
- 模板/路由/内容来源
- robots.txt、sitemap、canonical、隐私政策
- 是否存在低价值、复制、聚合、广告/联盟内容过多的问题
- 是否满足全部 ADS-* 检查项
Post-Rejection Diagnosis
@adsense-site-auditor 这个站 AdSense 申请被拒了，请按官方要求做拒审原因诊断：

URL: https://example.com
拒审信息：粘贴 AdSense 后台显示的原文

请把拒审信息映射到 ADS-* 要求 ID，逐项检查所有要求，并给出优先级修复清单。
Post-Fix Verification
@adsense-site-auditor 我已经按上次建议修复了网站，请复审是否可以重新提交 AdSense：

URL: https://example.com
已修复内容：
- ...
- ...

请重新逐项检查全部 ADS-* 要求 ID，不要只检查已修复项。输出 Ready / Ready after fixes / Not ready。
Task List Output
@adsense-site-auditor 请把这个网站的 AdSense 申请问题转成可执行修复任务：

URL: https://example.com

输出格式：
1. Blocker 任务
2. High 任务
3. Medium 任务
4. 每个任务包含：涉及 ADS-* ID、文件/页面、修复动作、验收标准
5. 最后附完整逐项检查表
Minimal Prompt
@adsense-site-auditor 审计 https://example.com 是否符合 AdSense 申请要求。必须逐项覆盖所有 ADS-* 检查项，并输出完整 Pass/Fail/Unknown/N/A 表。
