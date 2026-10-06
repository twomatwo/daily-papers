# Daily Papers

Interactive reading guides for the daily paper recommendation workflow.

## Architecture

- **Notion**: paper metadata, discovery / brief / deep-read state, user feedback.
- **GitHub (this repo)**: source of truth for interactive reading guides.
- **Astro + MDX**: static paper pages with reusable components.
- **Cloudflare**: optional deployment target later.

## Daily workflow

1. Run the existing daily paper discovery process.
2. Select exactly two deep reads according to the canonical Notion rules.
3. For each deep read:
   - verify enough of the paper body and supplement;
   - collect key figures that are necessary for understanding;
   - create explanatory diagrams when helpful and label them as AI-generated;
   - generate one MDX file under:
     `src/pages/papers/YYYY-MM-DD/<slug>.mdx`;
   - store binary assets under:
     `public/papers/YYYY-MM-DD/<slug>/`.
4. Build must pass.
5. Commit to `main`.
6. Write the final guide URL back to the corresponding Notion paper record.
7. The chat morning brief stays short and links to both guides.

## Content contract

Every deep-read page should include:

- 30-second takeaway
- 5 min / 20 min / deep-dive reading paths
- big-picture explanation
- 2–4 key figures when useful
- mechanism / theory with equations
- authors' claims separated from AI interpretation
- caveats
- Historical Reading Chain
- reading checklist
- source / figure attribution

Do not fabricate inaccessible figure details. If a figure cannot be legally or technically copied, use an attributed link or an AI-generated explanatory reconstruction instead.

## Local development

```bash
npm install
npm run dev
```

Build:

```bash
npm run build
```

## Cloudflare later

For Cloudflare Pages / Workers static deployment:

- Build command: `npm run build`
- Output directory: `dist`

A custom domain such as `papers.example.com` can be attached later without changing the content workflow.
