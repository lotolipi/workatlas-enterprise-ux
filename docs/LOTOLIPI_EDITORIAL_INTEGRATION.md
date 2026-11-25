# Lotolipi integration handoff

Target: lotolipi/product-design-portfolio, app/work/workatlas/page.tsx (inspected blob 677d7fcc0e87f8db1712e1066320d67b0dcfced2).

The current route already renders ExperienceChallenge and DataExperience. Preserve both and the existing HTML case study. Add the evidence section immediately after DataExperience, before case-study-reading. Copy docs/workatlas-editorial.svg into public/projects/workatlas/editorial-evidence.svg in the portfolio repository.

Suggested JSX (inside the existing fragment):

```tsx
<section className="lvis-data" aria-labelledby="workatlas-evidence-title">
  <p className="lvis-kicker">Design evidence / Manual prototype checks</p>
  <h2 id="workatlas-evidence-title">One system. Clear ownership.</h2>
  <p>15 recorded initial checks: 14 reported passes and one initial failure. Follow-up retests are excluded. These are not usability or business impact metrics.</p>
  <figure style={{margin:0}}>
    <a href="/projects/workatlas/editorial-evidence.svg">
      <img src="/projects/workatlas/editorial-evidence.svg" width={1200} height={1600} loading="lazy" style={{width:"100%",height:"auto",display:"block",borderRadius:16}} alt="Shared task architecture, blocker workflow, ownership correction and manual checks. Sprint 02: 3 passes; Sprint 03: 5 passes; Sprint 04: 4 passes and 1 initial failure; Sprint 05: 2 reported passes." />
    </a>
    <figcaption>Open the full-size infographic. Independent prototype, synthetic scenarios.</figcaption>
  </figure>
  <p><a href="https://github.com/lotolipi/workatlas-enterprise-ux/blob/main/docs/VISUAL_EVIDENCE.md">Explore the detailed evidence and limitations</a></p>
</section>
```

QA gate before release: run repository build and type check; inspect at 375, 768 and 1440 px; check image loading, keyboard focus, zoom, contrast, existing challenge and data controls, and case-study navigation. Confirm no horizontal overflow. No new prototype tests or rendered browser checks are claimed by this handoff.

Deployment restriction: do not push to the Vercel-connected portfolio repository until preview deployment behavior is confirmed or authorized. This handoff is documentation only.
