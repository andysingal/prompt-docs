```
"<Task>
Act as a full-stack AI marketing strategist for a startup preparing to launch a new product or service. You will handle market research, positioning, messaging, content creation, email copywriting, and SEO ideation.
</Task>

<Inputs>
<product>{Describe your product or service here}</product>
<target_audience>{Who is the product for? (demographics, psychographics, industry, etc.)}</target_audience>
<goal>{e.g. “generate leads,” “build awareness,” “launch product,” etc.}</goal>
<tone>{e.g. “casual and fun,” “bold and punchy,” “professional and clear”}</tone>
</Inputs>

<Instructions>
Given the product, target audience, and goal:

1. **Customer Insight & Research**
   - Generate an Ideal Customer Profile (ICP)
   - Identify key pain points, goals, and decision drivers
   - Suggest 3 positioning angles to resonate with this audience

2. **Messaging & Conversion Copy**
   - Write a hook-driven landing page (headline, subheadline, CTA section)
   - Provide 3 viral headline variations
   - Create a messaging matrix: [Pain Point → Promise → Proof → CTA]

3. **Content Creation**
   - Generate a 7-day content plan (Twitter + LinkedIn)
   - Include daily post titles, themes, and tone suggestions
   - Add 1 short-form video concept if relevant

4. **Email Marketing**
   - Write 3 cold email variations:
     - Value-first pitch
     - Problem-agitate-solution
     - Case-study / social proof style

5. **SEO Strategy**
   - Suggest 1 SEO topic cluster aligned with the product
   - Provide 5 blog post titles that target mid-to-high intent keywords
   - Recommend a pillar + supporting post structure

6. **Output Format**
   - Use clear section headers (e.g. “ICP”, “Landing Page Copy”, “SEO Titles”)
   - Use markdown formatting for readability
   - Do **not** explain your reasoning — just give the final, polished outputs

This should be delivered as a comprehensive marketing kit, ready to deploy.
</Instructions>
```
<img width="523" height="705" alt="Screenshot 2026-02-24 at 4 18 28 PM" src="https://github.com/user-attachments/assets/4f3f1ed9-d62d-4b51-9ae7-8f80640230f4" />

***** [Expose Your Design System to LLMs](https://hardik.substack.com/p/expose-your-design-system-to-llms)

An audit script that catches what the LLM gets wrong. Solves the drift problem. It scans CSS files and flags every raw value with the correct token to use instead. If the LLM writes color: #2563EB, the script says “use var(--color-link).” Runs in CI. Zero violations required.

```md
Audit this project and make the design system LLM-readable.

Step 1: Audit
Scan every CSS/SCSS file. List every hardcoded visual value:
hex colors, rgb/rgba colors, pixel spacing, raw font sizes,
font weights, border radii, z-index values, box shadows,
and transition durations. Group them by category. Count totals.
Report which files have the most hardcoded values.

Step 2: Token layer
Create a tokens.css file with three layers:
- Layer 1: upstream design system tokens (use existing ones
  if the project already uses a design system, otherwise
  derive sensible primitives from the audit)
- Layer 2: project aliases that reference Layer 1 with
  fallbacks, e.g. --color-text: var(--ds-text, #292A2E)
- Layer 3 is the components themselves — they only ever
  reference Layer 2 aliases, never raw values

Include tokens for: colors (text, background, link, border,
interactive states), spacing (at least 8 steps), typography
(font families, sizes, weights, line heights), border radius,
elevation/shadow, z-index, and motion/transitions.

Step 3: Spec files
Create a specs/ directory. Write structured markdown specs:
- specs/foundations/ — color.md, spacing.md, typography.md,
  radius.md, elevation.md, motion.md
- specs/tokens/ — token-reference.md (master map of every
  CSS variable, its value, and when to use it)
- specs/components/ — one file per major component in the
  project. Each spec follows this template:
  1. Metadata (name, category, status)
  2. Overview (when to use, when not to use)
  3. Anatomy (parts of the component)
  4. Tokens used (which CSS variables it references)
  5. Props/API (if applicable)
  6. States (default, hover, active, focus, disabled, error)
  7. Code example
  8. Cross-references (related components)

Only spec components that actually exist in this project.

Step 4: Audit script
Create scripts/token-audit.js (or .sh) that:
- Scans all CSS files for hardcoded values
- Suggests the correct token for each violation
- Prints file, line number, violation, and suggestion
- Returns exit code 1 if any errors found (CI-ready)
- Distinguishes errors (hardcoded colors, spacing) from
  warnings (raw durations, uncommon values)

Step 5: Replace hardcoded values
Go through every CSS file and replace hardcoded values with
the tokens from Step 2. Every color:, background:, padding:,
margin:, gap:, border-radius:, font-size:, font-weight:,
box-shadow:, z-index:, and transition: should reference a
var(--token). No raw values should remain.

Step 6: Project instructions
Add a section to the project’s AI instruction file (CLAUDE.md,
.cursorrules, or equivalent) that says:
“Before writing or modifying any UI code, read the relevant
spec file in specs/. Use only tokens from tokens.css. Run the
token audit script before committing. Zero errors required.”

Run the audit script at the end and confirm zero violations.
```



