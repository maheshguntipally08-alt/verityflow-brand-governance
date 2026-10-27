# VerityFlow — Evidence-first brand governance

**Tagline:** Trust every publish. Prove every claim.

VerityFlow is a judge-ready, browser-based prototype that helps a creator check promotional copy against a small, approved source library before handing it to a human reviewer. The demo is seeded with fictional Northstar Energy brand data. It is designed to make evidence boundaries visible rather than pretend to prove universal truth.

## Open the prototype

- Open `index.html` in a modern browser. No package installation or API key is required.
- The prototype stores demo changes in browser `localStorage`.
- Use **Reset demo** on the Overview page to return to the seeded dataset.
- Recommended walkthrough: Overview → Review studio → Apply suggested fixes → Send to human review → switch to Reviewer view → Review queue → approve or request changes → Audit trail.

## Implemented in this build

1. Responsive dashboard and navigation across Overview, Review Studio, Source Library, Review Queue, and Audit Trail.
2. Draft editor with word/character counts, sample draft loader, and `.txt` / `.md` import.
3. Deterministic checks for unsupported numeric claims, absolute promises, unsupported rankings/comparisons, and unsubstantiated outcome language.
4. Explainable finding cards with snippets, risk level, rule/source evidence, and suggested minimal edits.
5. Claim Passport status labels: Supported, Contradicted, or No approved source found, based on the local sample library and deterministic rules.
6. Source library with owner, approved date, expiry/review date, source ID, scope notes, and ability to add a source record locally.
7. Submit-for-review queue with submitted content snapshots and reviewer actions: approve or request changes with a reason.
8. Version-aware approval behavior: changing text after approval resets the active draft to Draft; an approval is associated with the submitted version.
9. Local audit trail and JSON export for review reports / audit events.
10. Accessible semantic labels, keyboard focus states, responsive layout, reduced-motion support, and clear prototype limitations.

## Technology and implementation details

- **UI:** semantic HTML5, CSS3, vanilla JavaScript (single-file static application).
- **State:** browser `localStorage`; no server database in this prototype.
- **Review engine:** deterministic browser-side JavaScript rules plus a synthetic approved-source ledger. This is deliberately transparent and repeatable.
- **File import:** browser `FileReader` for plain text and Markdown files.
- **Exports:** browser Blob download to JSON.
- **Hosting:** static-site compatible; can be published through GitHub Pages, Netlify, or any static web host.
- **Privacy:** no external AI call, analytics, or API keys are required. Do not enter confidential customer/company material.

## Important boundary: what is not implemented

This build is a functional MVP/demo, not an enterprise release. It does **not** currently include a Gemini/LLM API connection, server-side FastAPI service, PostgreSQL/Supabase storage, real authentication or permission enforcement, OCR/image ingestion, DOCX/PDF parsing, logo/colour comparison, automated accessibility measurements, or a production-grade immutable audit trail. The role switch is a demo interaction and is not security. Source matching is limited to the sample evidence and deterministic checks; the product is not a universal fact checker, legal-compliance certification, or automatic publisher.

## Publish as a public site

1. Create a GitHub repository named `verityflow-brand-governance`.
2. Upload the contents of this folder to the repository root (including `.github/workflows/pages.yml`).
3. In GitHub, open **Settings → Pages** and choose **GitHub Actions** as the build/deployment source if it is not already selected.
4. Push to the default branch. The included workflow deploys the static site. Copy the resulting GitHub Pages URL into the event form after confirming the page opens in a logged-out/private browser.
5. For a public source-code repository link, use the repository URL after you create it. This package is source-ready but has not been pushed to a public GitHub account from this environment.

## Suggested judge walkthrough (3–4 minutes)

1. **Problem (20 sec):** a draft can be polished but still contain unsupported, overconfident claims.
2. **Run review (40 sec):** open the Review Studio and point out the mismatched “40% lower energy bills” claim and the approved pilot source.
3. **Evidence boundary (40 sec):** show Claim Passport statuses and why the source does not prove guaranteed bill savings.
4. **Correct without rewriting everything (35 sec):** apply a suggested fix, re-run checks, and explain the creator stays in control.
5. **Human governance (45 sec):** submit the exact draft version, switch to Reviewer view, request changes or approve, and show the Audit Trail.
6. **Limitations (20 sec):** clearly state this build uses a deterministic local engine and synthetic facts; live AI, real auth, and image/OCR ingestion are later work.

## Three major Round 3 improvements

1. **Evidence-grounded claim extraction:** introduce a provider adapter and constrained structured output, retrieve only from the approved library, and validate every claim-to-source mapping; missing support must fail to “No approved source found.”
2. **Version-aware reviewer controls and persistence:** move roles, immutable content versions, source metadata, decisions, and audit events to a server-backed store with authenticated role enforcement and tests for approval invalidation.
3. **Visual + accessibility checks and measured benchmark:** add a supported image/OCR path, basic approved-logo/colour and alt-text checks, then run a seeded benchmark and moderated usability walkthroughs. Publish actual measured results and known failure cases; do not present targets as results.

## Source of scope

The prototype follows the original VerityFlow plan's key mechanisms: Claim Passport, explain-and-preserve edits, and human-controlled version-aware review. It intentionally narrows the planned Next.js/FastAPI/DB/AI stack into a static build to deliver a complete, inspectable end-to-end flow without requiring secrets or external services. The change and limitations are documented rather than represented as finished integrations.

## Files

- `index.html` — runnable prototype.
- `README.md` — this guide.
- `SUBMISSION_NOTES.md` — concise details for the event submission form.
- `TEST_REPORT.md` and `test_results.txt` — browser acceptance checks and output.
- `assets/demo-overview.png` and `assets/demo-review-studio.png` — UI screenshots.
- `docs/VerityFlow_Updated_Project_Submission.pdf` — the updated submission report.
- `.github/workflows/pages.yml` — GitHub Pages deployment workflow.
