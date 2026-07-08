<wizard-report>
# PostHog post-wizard report

The wizard has completed a full PostHog integration for Bishoy Maher's Astro static portfolio site. A new `src/components/posthog.astro` component was created using the PostHog web snippet with `is:inline` to prevent Astro from processing it, and it reads credentials from environment variables. The component is included in `src/layouts/Layout.astro`, which wraps every page, so PostHog initialises on every visit automatically.

Seven custom events are captured across four files, covering the portfolio's key conversion actions (booking a discovery call, sending an email) and engagement signals (viewing project case studies, clicking social links).

| Event name | Description | File |
|---|---|---|
| `discovery_call_clicked` | User clicked a "Book a discovery call" CTA | `src/pages/index.astro` |
| `email_cta_clicked` | User clicked a "Send me an email" CTA | `src/pages/index.astro` |
| `project_section_viewed` | User scrolled a project case study into view (TfC, Dexi, Toptal) | `src/pages/index.astro` |
| `discovery_call_clicked` | User clicked "Book a discovery call" on the about page | `src/pages/about.astro` |
| `view_work_clicked` | User clicked "View work" on the about page | `src/pages/about.astro` |
| `banner_cta_clicked` | User clicked "Get in touch" in the top availability banner | `src/layouts/Layout.astro` |
| `social_link_clicked` | User clicked a footer social link (email, LinkedIn, Dribbble, Medium) | `src/components/Footer.astro` |

## Next steps

We've built some insights and a dashboard for you to keep an eye on user behaviour, based on the events just instrumented:

- [Analytics basics (wizard) — Dashboard](https://eu.posthog.com/project/219044/dashboard/803179)
- [Discovery call clicks](https://eu.posthog.com/project/219044/insights/JhppSASf)
- [Email CTA clicks](https://eu.posthog.com/project/219044/insights/rnJAbDjn)
- [Project section views by project](https://eu.posthog.com/project/219044/insights/YrjuS98f)
- [Conversion funnel: Project view → Discovery call](https://eu.posthog.com/project/219044/insights/MnUUOFQu)
- [Social link clicks by platform](https://eu.posthog.com/project/219044/insights/gnmq9DoX)

## Verify before merging

- [ ] Run a full production build (`npm run build`) and fix any lint or type errors introduced by the generated code.
- [ ] Run the test suite — call sites that were rewritten or instrumented may need updated mocks or fixtures.
- [ ] Add `PUBLIC_POSTHOG_PROJECT_TOKEN` and `PUBLIC_POSTHOG_HOST` to `.env.example` and any bootstrap scripts so collaborators know what to set.
- [ ] Wire source-map upload (`posthog-cli sourcemap` or your bundler's upload step) into CI so production stack traces de-minify.

### Agent skill

We've left an agent skill folder in your project at `.claude/skills/integration-astro-static/`. You can use this context for further agent development when using Claude Code. This will help ensure the model provides the most up-to-date approaches for integrating PostHog.

</wizard-report>
