# Dingo — Interactive MVP Design Prototype

**Invest your time. Build real ideas.**

Arabic-first, responsive, interactive design prototype for the Dingo time-investment marketplace. The prototype is a front-end design exploration, **not a deployed multiuser SaaS**.

## Quick start · طريقة التشغيل

**Recommended:** unzip the folder, then from inside `dingo-mvp` run:

```bash
python -m http.server 8000
```

Open `http://localhost:8000/` in a modern web browser.

You can also open `index.html` directly in a browser, but using a local server is more reliable for browser storage and assets.

**Login note:** The login, sign-up, and reset flows are an interactive front-end **simulation**, not real authentication. Registration saves only the demo profile (name, email, role); passwords are not stored. A password entered on the login screen is not checked against a server. Never use real passwords in this prototype. A real release requires a proper authentication provider, server-side account checks, secure sessions, email verification, abuse prevention, and a functioning password recovery flow.

**Note:** Internet access is optional. Google Fonts loads when network is available; system fonts are used when offline.

## Screens / الشاشات

| URL hash | Design screen | Interaction |
|---|---|---|
| `#/home` | Marketing landing page | Explore ideas, publish an idea, switch Arabic ↔ English, Log in / Sign up links |
| `#/login` | Login | Email/password validation, show/hide password, demo login, remember-me UI |
| `#/register` | Registration | Name/email/password confirmation, password-strength indicator, choose idea owner / time investor / both |
| `#/forgot-password` | Password reset preview | Email validation and explicit no-send simulation |
| `#/members` | Member directory | Browse sample profiles, search by name/skills, review availability and work examples |
| `#/profile/mostafa` | Contributor profile | Skills, portfolio, self-reported experience, availability, demo feedback and logged contributions |
| `#/profile/me` | My profile | Edit headline, about, skills, time availability and optional professional links (local demo only) |
| `#/discover` | Ideas Repository | Filter by category/reward, search, sort, explore cards |
| `#/idea/ai-stock` | Idea details | View POC, discuss in public thread, submit private time offer |
| `#/idea/team-flow` | My idea details | Review roles and private incoming offers |
| `#/publish` | 4-step idea publishing | Enter brief → requirements → reward models → confirm rights; creates a demo idea |
| `#/offers` | Idea Owner Dashboard | Open contributor profile from an offer, review samples / time history, negotiate draft, accept / decline offers |
| `#/workspace` | POC workspace | Move task statuses; submit time-logged deliverables; view ledger |
| `#/emails` | Email preview center | Switch between 4 email designs; download HTML email template |

All edits in this design prototype are saved **only in your browser's localStorage**, not to any server. Clearing browser storage or switching devices will lose your changes.

## Concept and safeguards

- Owner remains the original idea submitter; contributors **do not automatically receive** ownership or future financial rights.
- Reward models are flexible **per idea**: community/portfolio, contingent revenue share, potential future equity, and deferred payment.
- Every accepted collaboration should have a separately reviewed agreement defining IP assignment/licensing, deliverables, duties, milestones, payment conditions, and disputes.
- Offers are private by design; discussion threads are public. Offer-specific summaries appear on a contributor profile only when opened from the owner’s offer inbox in this local demo. In production this requires server-enforced access checks.
- Profile experience, work samples, availability and feedback are **illustrative, self-reported or demo data**. The MVP does not verify identity, skill credentials, claimed hours or reviews. There is no real reputation scoring or background check.
- Hours **pledged**, hours **submitted**, and hours **accepted** have different meanings.
- This prototype's idea timestamps are **local browser timestamps and are editable**. They are **not certified timestamps**, patents, government IP filings, or independent proof of exclusive ownership. Production requires server-side immutable audit trail, trusted timestamps where appropriate, content hashing, identity checks, and legal review.
- Notification previews **do not send emails**. The platform **does not actually authenticate** people or sign contracts in this version.

## Delivered assets

```text
index.html                Browser entry point
auth.js                   Bilingual login / registration / reset interactions
auth.css                  Responsive auth layouts, brand side panels, forms
profiles.js               Member directory, dynamic member profiles, demo profile edit
profiles.css              Responsive profile and directory design
app.js                    Demo data, state, routing, translations, interactions
styles.css                Responsive UI and design system
assets/
  dingo-mark.svg/png      Icon-only original brand mark
  dingo-logo.svg/png      Original main wordmark
  dingo-logo-white.svg/png  White wordmark for dark backgrounds
emails/
  offer.html              New Time Investment Offer email
  comment.html            New public discussion comment email
  accepted.html           Time Offer Accepted email
  deliverable.html        Deliverable Submitted email
screenshots/
  brand-identity.png      Color palette and wordmark guide
  email-templates-overview.jpg
  email-*.png             Individual email sample renders
  dingo-product-concept.png  Generated creative product-vision collage (concept only)
  login-desktop.png          Login page desktop screenshot
  register-desktop.png       Registration page desktop screenshot
  login-mobile.png           Login page mobile screenshot
  register-mobile.png        Registration page mobile screenshot
  member-profile-desktop.png  Full contributor profile
  member-profile-offer-review.png Profile linked to pending offer
  member-profile-mobile.png   Responsive profile on a phone
  members-directory.png       Searchable directory of member profiles
DESIGN_NOTES.md           UI structure and implementation handoff
```

## Email dynamic variables

Standalone HTML email files use placeholders like `{{recipient_name}}`, `{{idea_title}}`, `{{contributor_name}}`, `{{contributor_profile_url}}`, `{{offered_hours}}`, `{{reward_model}}`, `{{deliverables}}`, `{{action_url}}`, and `{{notification_preferences_url}}`.

Before production, interpolate with escaped/validated strings and verified HTTPS action links, and send using a transactional email service. Do not ship prototype sender addresses or example template data as real.

## Production next steps

1. Implement authentication, profiles, permissions/RLS and file storage.
2. Replace localStorage with a database, server-side audit log and tamper-evident revision history.
3. Implement private contribution offers, notification jobs, and email delivery.
4. Create jurisdiction-reviewed agreement templates and legally valid approval flows for IP, rewards, and work product.
5. Add moderated reports/disputes and contributor reputation based on verified deliverables.
6. Connect real task status, POC proof, analytics, and abuse prevention.

**Brand note:** The logo is an original prototype design, not a trademark clearance or assertion that the name “Dingo” is available for commercial registration.
# Dingo
