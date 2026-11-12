# Private SEO & Content Operations Platform — Product Plan v1.0

**Planning baseline | 12 November 2026**  
**Working title:** Private SEO Workspace (product name not finalized)

> **Product direction locked:** Build a private, multi-website SEO workspace for 2–5 WordPress websites. Focus the first release on keyword research, content planning, AI-assisted article drafting, approval-controlled WordPress publishing, internal-link suggestions and Google Search Console performance. GEO, local SEO, backlink intelligence and social distribution are later phases.

This document is product planning only. It intentionally excludes database design, schemas, API contracts, source code, detailed system architecture and implementation instructions.

## 1. Executive summary

The project is a private SEO content operations platform inspired by the practical parts of Distribb. It is intended for personal SEO projects and Tech Webers client websites. The first release should make one workflow dependable:

**Research a keyword → plan the topic → draft a useful article → review it → publish it to WordPress → monitor its search performance.**

The platform will support 2–5 websites in one private dashboard. Each site retains its own business context, competitors, content calendar, WordPress connection and Search Console property. The initial product is not a public SaaS offering: no public signup, subscription billing or white-label portal.

## 2. Product definition

### What we are building

A single dashboard for managing SEO content work across a small group of WordPress websites. It combines lightweight keyword intelligence, a content calendar, AI-assisted article drafting, approval-controlled publishing, internal-link recommendations and Search Console reporting.

### What we are not building

- Not a public SaaS competitor to Distribb or a pixel-for-pixel copy of its interface, branding or proprietary workflows.
- Not a full enterprise SEO suite with every technical audit, rank-tracking and backlink metric.
- Not an autonomous publishing bot. Generated content and material page updates require human approval.
- Not a backlink exchange marketplace or automated link-exchange system.
- Not a multi-CMS publishing hub in the first release. WordPress is the only supported CMS.
- Not a social scheduler, paid advertising platform or full CRM.

## 3. Goals, users and operating assumptions

### Goals

1. Manage 2–5 websites from one private dashboard without mixing site data or credentials.
2. Make keyword research and topic planning repeatable.
3. Generate better first drafts using each website’s services, audience, locations, writing preferences and existing content.
4. Keep a clear human approval step before content is sent to WordPress.
5. Use Search Console data to understand which content earns impressions and clicks.
6. Reduce repetitive work while preserving editorial judgment.

### Intended users

- **Owner / administrator:** adds websites, connects services, controls settings, monitors usage and reviews work.
- **SEO/content operator:** researches keywords, plans articles, edits drafts, approves content and reviews performance.
- **Future reviewer (optional):** reviews assigned content without managing integrations or website settings.

### Locked assumptions

| Area | Planning assumption |
|---|---|
| Websites | 2–5 at launch |
| Markets | Primarily English-language sites targeting the United States; country and language configurable per site |
| CMS | WordPress only |
| Initial content volume | Approximately 4–6 articles per site per month; adjust after quality and review testing |
| Automation | Research and drafting can run automatically; human decision required before publication or major changes |
| Access | Private owner-led workspace; staff access can be added later |

## 4. Initial product: V1 features

### 4.1 Multi-website workspace

One private dashboard with a website switcher and separate work areas for each site. Each website has its own profile, keyword list, content calendar, articles, WordPress connection and Search Console connection.

### 4.2 Website and business profile

Capture the website URL, business name, niche, services, service areas, target audience, target country/language, key selling points, competitors, preferred tone, prohibited wording and content instructions. Use this as reusable context for research and writing.

### 4.3 Lightweight website discovery

Read the sitemap and discover important published pages. Identify URLs, titles, meta descriptions, H1s and basic indexability signals. This supports content context and internal-link suggestions; it is not a comprehensive technical crawler.

### 4.4 Keyword research

Use **DataForSEO** as the initial SEO data provider. Research seed keywords and related ideas. Display available search volume, keyword difficulty, CPC where available, intent classification and relevant SERP observations. Allow the operator to filter, shortlist and approve target keywords.

### 4.5 Topic clustering and duplicate-topic checks

Group similar keyword ideas into topics and compare proposed topics with existing pages and planned articles. Flag likely overlap for human review; do not automatically discard topics based only on a model score.

### 4.6 Content calendar

Plan articles by website, target keyword, title, content type, target date and status. Support manual topic creation, rescheduling, topic approval and visibility into overdue or blocked work.

### 4.7 AI article briefs and drafts

Create a structured brief before drafting. Generate an outline, article draft, SEO title, meta description, suggested slug, FAQs where useful, relevant CTAs and internal-link opportunities. Writing must use the site profile and approved research context.

### 4.8 Editorial editor and approval

Provide an editable review experience with revision history, checklist and reviewer notes. Support approve, reject, request changes and return to draft. Article generation finishing must never trigger publication by itself.

### 4.9 WordPress publishing

Connect each site using a dedicated WordPress user with a revocable **Application Password**. Transfer article content and basic metadata, and record the resulting URL and post reference. Default publishing mode is WordPress Draft. After approval, the operator can publish or schedule.

### 4.10 Internal-link suggestions

Use discovered pages to suggest a small number of contextually relevant internal links and anchor text. The reviewer can accept, edit or ignore each suggestion. Do not automatically insert unrelated links.

### 4.11 Google Search Console performance

Connect the verified Search Console property for each site. Show clicks, impressions, CTR and average position, with basic query/page views and date comparisons. Allow users to inspect performance of published articles.

### 4.12 Activity and usage view

Show recent jobs, article status, publishing outcomes, integration health and approximate usage for paid services. Provide clear errors when research, generation or publishing fails.

## 5. Core user workflows

### Add a website
1. Create a website entry and complete its business profile.
2. Confirm market, language, services, locations and competitors.
3. Connect WordPress with a dedicated restricted user and Application Password.
4. Connect the correct Google Search Console property.
5. Import the sitemap and discover existing pages.
6. Review discovered pages and identify priority service/location pages where useful.

### Research and plan content
1. Enter a seed topic, service, location or competitor domain.
2. Retrieve keyword ideas and available search metrics from the SEO data provider.
3. Review intent and group related keyword ideas into topics.
4. Check for overlap with existing pages and planned articles.
5. Select topics, assign dates and add them to the content calendar.

### Generate, review and publish
1. Open a planned calendar item and review its brief.
2. Generate an outline and article draft using the website profile.
3. Review facts, service accuracy, local references, originality, tone, search intent and internal links.
4. Edit or request changes; save meaningful revisions.
5. Approve and choose WordPress Draft, Publish now or Schedule.
6. Verify the WordPress result and record its URL and publication date.

### Review performance
1. Select a website and reporting period.
2. Review clicks, impressions, CTR, average position, top queries and top pages.
3. Inspect published articles after sufficient time for search data to accumulate.
4. Record pages needing a refresh or further investigation.
5. Use observations to inform the next content calendar.

## 6. Recommended tools and services

| Area | Recommended choice | Reason |
|---|---|---|
| Application | Next.js + TypeScript | One maintainable web application for the private dashboard and workflows |
| UI | Tailwind CSS + shadcn/ui | Consistent, efficient dashboard components |
| Authentication | BetterAuth | Private owner access now; staff access later if needed |
| Background workflows | Trigger.dev | Long-running research, generation, scheduled syncs and retries |
| SEO data | DataForSEO | One initial source for keyword ideas, volume/difficulty and SERP research |
| AI writing | OpenAI API | One primary provider for briefs, outlines and drafts |
| Search performance | Google Search Console API | First-party clicks, impressions, CTR, position, queries and pages |
| Publishing | WordPress REST API + Application Passwords | Native WordPress connection; dedicated restricted user |
| Media storage | Cloudflare R2 | Separate storage for article images and generated media |
| Hosting | Vercel | Straightforward hosting for a Next.js application |
| Error monitoring | Sentry | Visibility into failed jobs and application errors |
| Notifications | Resend (optional) | Review-ready and publishing-failure alerts |

**Keep the MVP simple:** do not begin with several LLM vendors, several SEO data vendors, multiple CMS connectors or an integration marketplace. Prove the workflow with one provider per category first.

### WordPress connection decision

Use the WordPress REST API with a dedicated user and revocable Application Password by default. Do not store a site administrator’s normal password. Build a small companion plugin only if native REST API support cannot reliably handle a required task, SEO metadata, custom fields or media workflow.

### SEO data provider decision

Use DataForSEO first. Keep the product experience independent of the provider, but do not pay for a second provider during MVP unless a specific data gap blocks the workflow.

### AI provider decision

Use OpenAI first. Control quality through reusable site instructions, structured briefs, research context and human editing. Consider Claude for editorial review only after testing proves a clear benefit.

## 7. Automation and editorial control

| Activity | V1 policy |
|---|---|
| Keyword research | Can run automatically after operator starts a task |
| Topic clustering | Suggested automatically; operator approves topics |
| Content calendar | System can suggest dates; operator confirms plan |
| Article generation | Automatic draft generation from an approved brief |
| Internal links | Suggestions only; reviewer accepts or edits |
| Article editing | Human-controlled; no silent replacement of approved content |
| WordPress publishing | Explicit approval required; default destination is WordPress Draft |
| Existing page optimization | Recommendations only; no live-page overwrite without review |
| Reports | Can be prepared automatically; operator checks interpretation before client delivery |

### Recommended content statuses

Planned → Brief ready → Generating → Needs review → Changes requested → Approved → Scheduled → Published. Use Blocked/Failed when a person or integration needs to resolve an issue.

## 8. Upcoming features and roadmap

### V1.1 — Content improvement and basic SEO health

- GSC opportunity queue: pages with declining clicks, high impressions/low CTR or queries near page one.
- Content refresh workflow with before/after comparison and approval before WordPress updates.
- Light technical checks: broken internal links, missing titles/descriptions, missing H1, sitemap visibility and obvious indexability flags.
- Monthly summary of organic clicks, impressions, published content and notable movements.

### V2 — GEO and local presence

- AI visibility tracking across selected AI answer providers; record prompt, provider, date, region, mentions, competitors and cited URLs. Treat results as directional, not as a perfect reproduction of consumer AI search.
- Google Business Profile connection, subject to API access and client authorization.
- Review reply assistant with approval before posting.
- Google Business Profile post drafting and scheduling after review.
- GA4 reporting for sessions and selected conversions.

### V3 — Backlink intelligence and outreach

- Competitor backlink discovery and referring-domain research.
- Backlink monitoring and lost-link detection.
- Outreach prospecting for relevant resource pages, roundups and editorial opportunities.
- Outreach CRM for contacts, draft pitches, approvals and follow-ups.
- Manual, editorially directed placement workflow. No automated reciprocal-link exchange marketplace.

### V4 — Content distribution and agent access

- Turn approved articles into social captions, carousel outlines and short-video scripts.
- Generate reusable carousel graphics and simple template-driven videos after human review.
- Evaluate social publishing APIs and permissions before offering automatic posting.
- MCP/AI agent access under the same site permissions and approval rules.
- Optional team/reviewer access if needed.

## 9. Explicitly out of scope

| Excluded from initial project | Why deferred |
|---|---|
| Backlink exchange marketplace / credit network | Requires a real publisher network, quality controls and operations; automated link exchange creates search-policy risk. |
| Automated link insertion or guaranteed link acquisition | Editorial relevance and quality cannot be safely guaranteed through automation. |
| Automatic live-page overwrites | Conflicts with review-first operation. |
| Shopify, Webflow, Wix, Ghost and other CMSs | WordPress only for launch. |
| Full social scheduler | Not needed to prove SEO content workflow; platform permissions add scope. |
| Video production engine | Adds media rendering and quality-control work. |
| White-label client portal and subscription billing | Private-use project, not public SaaS. |
| Full CRM / email marketing automation | Separate product category. |
| Paid ads management | Outside product focus. |

## 10. Success measures

- **Workflow completion:** Can an operator move from keyword idea to approved WordPress draft without copying content across tools?
- **Review acceptance:** What share of drafts pass with light edits rather than needing a full rewrite?
- **Time saved:** How long do research, briefing and first-draft creation take versus the current process?
- **Content quality:** Are articles accurate, useful, distinct and aligned with the business?
- **Publishing reliability:** Does approved content reach the correct site with correct title, content, URL and metadata?
- **Search performance visibility:** Can the operator monitor clicks, impressions, CTR and position for each website?
- **Cost per article:** Can the platform estimate provider spend for research, generation and media tasks?

Do not promise rankings, leads or revenue. Measure operating efficiency first and evaluate SEO outcomes over time with Search Console and, later, GA4 conversion data.

## 11. Dependencies and risks

| Risk | Planning response |
|---|---|
| Search Console access | Ensure the correct verified property is available to the authorized account. |
| WordPress compatibility | Test actual site versions, hosting and SEO plugins before finalizing metadata behavior. |
| AI factual errors | Require human review; flag claims about licensing, guarantees, pricing, health/legal topics and service availability. |
| Keyword metrics are estimates | Display source and retrieval date; do not treat metrics as exact truth. |
| Search data delay | Explain that Search Console is not real-time. |
| Provider cost variability | Set usage limits and monitor cost per website/article/job. |
| GEO uncertainty | When introduced, record model/provider, prompt, date and region; compare like with like. |
| GBP permissions | Do not commit GBP features to V1; confirm Google API eligibility and client authorization first. |
| Search-policy risk | Avoid manipulative exchanges, scaled low-value pages and unreviewed publishing. |

## 12. V1 release gates

- At least two WordPress websites can be configured independently and switched between safely.
- Each website has a reusable business profile and imported existing URLs.
- The operator can research keywords and approve topics into a calendar.
- The operator can generate an article brief and editable draft grounded in site context.
- A reviewer can request changes, approve or reject drafts and see status clearly.
- Approved content can be sent to the correct WordPress site as a draft or published/scheduled through an explicit action.
- Internal-link suggestions are relevant, editable and never inserted without review.
- Search Console metrics are visible for the correct property.
- Failed jobs are visible and retrying does not create duplicate WordPress posts.
- Approximate provider usage can be inspected by website.

## 13. Recommended planning sequence

1. Approve the V1 included and excluded feature lists.
2. Choose two pilot websites with working WordPress and Search Console access.
3. Confirm service accounts and billing limits for DataForSEO, OpenAI, Google Search Console and hosting.
4. Test one real keyword-to-article workflow on each pilot website; evaluate draft quality, review time and WordPress transfer.
5. Test Application Password connection and metadata/media needs on the real sites; decide whether a companion plugin is necessary.
6. Freeze V1 acceptance criteria. Do not add GEO, GBP, backlinks or social features during the first delivery without an explicit scope change.

## 14. Locked product decisions

| Decision | Locked position |
|---|---|
| Product type | Private internal platform, not public SaaS |
| Inspiration | Distribb’s practical SEO content operations model; no copying proprietary code, branding or protected assets |
| Primary job | Keyword-to-content-to-WordPress workflow with Search Console feedback |
| Initial websites | 2–5 |
| CMS | WordPress only |
| Automation | Research and drafting can be automated; publishing and content changes require review |
| Primary SEO data | DataForSEO |
| Primary content AI | OpenAI API initially |
| Search performance | Google Search Console |
| Local SEO / GBP | Upcoming, not V1 |
| GEO tracking | Upcoming, not V1 |
| Backlink exchange | Not planned |
| Social distribution | Upcoming, not V1 |

## 15. Reference sources

Product scope informed by public sources available on 12 November 2026. Public product pages are references, not evidence of Distribb’s undisclosed internal implementation.

1. [Distribb — Features overview](https://distribb.io/features) — product feature groups.
2. [Distribb — Main product site](https://distribb.io/) — content workflow, site connections and review-before-publish description.
3. [Distribb — API documentation](https://distribb.io/api-docs) — public REST API and MCP descriptions.
4. [Distribb — Developer page](https://distribb.io/developers) — API, MCP and agent access.
5. [Google Search Console API](https://developers.google.com/webmaster-tools/v1/searchanalytics/query) — Search Analytics documentation.
6. [Google Business Profile APIs](https://developers.google.com/my-business) — official starting point for future GBP work.
7. [WordPress REST API authentication](https://developer.wordpress.org/rest-api/using-the-rest-api/authentication/) — official authentication guidance, including Application Passwords.
8. [DataForSEO pricing](https://dataforseo.com/pricing) — official pricing; recheck before implementation.

---

**Document boundary:** This is the product and scope baseline. Database schemas, data models, API route specifications, detailed architecture diagrams, code, implementation tasks and deployment instructions are deliberately excluded. Prepare those only after the product scope is accepted.
