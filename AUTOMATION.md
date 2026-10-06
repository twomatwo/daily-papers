# Daily guide generation protocol

This repository is the presentation layer for the Notion **Daily Paper Recommendations** workflow.

## Source of truth

1. Read the canonical Notion page **每日论文推荐规则** before every run.
2. Notion owns paper metadata, recommendation state, reading state, and user feedback.
3. GitHub owns the source for interactive deep-reading guides.
4. A generated guide never implies the user has read the paper.

## When to generate

Create or update exactly one guide for each paper selected as a daily deep read.

- A paper that was previously briefed may receive its first guide when it is promoted to a deep read.
- Re-running the same daily task must update the same file, not create a duplicate.
- Reuse a prior guide for the same research work when appropriate; do not fork preprint and journal versions into separate guides without a real reason.

Path:

`src/pages/papers/YYYY-MM-DD/<stable-slug>.mdx`

Assets, when needed:

`public/papers/YYYY-MM-DD/<stable-slug>/`

## Required guide structure

A guide should be optimized for learning, not for reproducing the paper.

1. 30-second takeaway.
2. 5 min / 20 min / deep-dive reading paths.
3. Big picture and a compact mechanism/concept flow.
4. Authors' reported results, AI interpretation, and caveats kept separate.
5. Key figures:
   - preserve an original figure only when reuse rights have been verified;
   - otherwise link to the original figure and explain what to look for;
   - create a clearly labeled explanatory diagram when it improves understanding.
6. Core mechanism/theory with equations where useful.
7. Historical Reading Chain, normally 2–4 items with one clear first read.
8. Reading checklist.
9. Source and attribution section.
10. Optional interactive element only when it materially clarifies a parameter, phase, mechanism, or conceptual progression.

## Figure and media policy

This repository is public. Do not automatically upload publisher figures, PDF screenshots, videos, or third-party media without verifying reuse terms.

- **Open license permitting reproduction:** an unmodified paper figure may be stored or embedded with author/source/license attribution.
- **No-derivatives license:** reproduce only an unmodified original when the license permits this site's use. Never crop, annotate, recolor, combine, or otherwise create a derivative.
- **Unclear or restrictive rights:** do not copy the image. Link to the original figure and create a separate explanatory diagram from verified factual concepts.
- **Generated explanatory media:** label it explicitly as an explanatory reconstruction, not as a paper figure. Never recreate quantitative data points or curves from memory.

Prefer a few meaningful figures and interactions over decorative media.

## Quality rules

- Distinguish paper claims from analysis.
- State the actual reading scope: full text, selected sections, or abstract only.
- Do not invent inaccessible methods, figure details, numbers, limitations, or supplementary results.
- Link historical papers to canonical/original sources where possible.
- Conceptual interactives must be labeled conceptual unless backed by verified numerical data.

## Commit and verification

1. Inspect `main` and the existing stable slug before writing.
2. Update/create the guide and any permitted local assets.
3. Do not rewrite framework files in an ordinary daily run.
4. Commit to `main`.
5. The GitHub Actions `build` workflow must pass before webpage generation is considered successful.
6. After a successful commit/build, write the GitHub source URL and guide path back to the Notion paper record.
7. Only write a public live guide URL after a deployment base URL has actually been configured.
8. If webpage generation or build fails, keep the paper recommendation intact and report the webpage failure explicitly.

## Deployment

The site builds statically with:

`npm run build` → `dist/`

Cloudflare is not configured yet. A future deployment may use Cloudflare Pages or Workers without changing the content-generation contract.
