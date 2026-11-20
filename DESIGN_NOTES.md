# Dingo — Visual Design & Product Handoff

## Brand strategy

**Positioning:** A time-investment platform for creators whose ideas cannot move forward because funding is missing. Skilled contributors can invest their time and deliverables instead of money.

**Tagline:** “Invest your time. Build real ideas.”

**Tone:** optimistic, practical, human-first, transparent about rights and contributions.

### Palette

| Token | Hex | Role |
|---|---|---|
| Midnight Plum | `#251746` | Primary text, dark hero backgrounds |
| Electric Violet | `#6E43D5` | Primary buttons, links, navigation accents |
| Dingo Orange | `#FF963B` | Energy, time investment, brand highlight |
| Lilac Mist | `#F3EDFF` | Surfaces, light accents |
| Verified Green | `#168E67` | Verified work / accepted states |
| Canvas | `#F8F7FC` | App background |
| Border | `#EAE6F2` | Dividers and component borders |

Arabic-first typography: IBM Plex Sans Arabic with Tahoma fallback. English: Manrope with Arial fallback. Fonts are loaded from Google Fonts optionally; no font file redistribution.

Brand mark: rounded wild-dog-inspired head in plum and orange, with a minimal bright face. SVG is editable. The wordmark is also supplied as SVG + PNG.

## Information architecture

- Home / public landing
- Ideas Repository (filters and search)
- **Members directory** (search by name and skills, preview availability)
- **Individual member profile** (skills, availability/week, self-reported experience, portfolio cards, demo feedback, accepted demo deliverables and safe public contact links); personal profile editing
- **Pre-acceptance due diligence flow**: Offer inbox → contributor profile with private offer summary → work samples / ledger / feedback → review acceptance
- Idea detail: Overview / Requirements / Public Discussion / Private Offers
- Publish idea: brief / hours / flexible rewards / ownership acknowledgment
- Idea Owner Dashboard: offers, decision states, personal projects
- Project Workspace: Kanban, time ledger, milestones
- Email templates: 4 notification situations

## Core roles

**Idea Owner:** writes the brief, defines POC, offers reward models, approves participation, tracks deliverables and preserves rights through explicit agreements.

**Time Investor:** discovers a compatible POC, proposes a role, time commitment, delivery period, compensation preferences and deliverables, then tracks accepted work.

**Future platform operations:** protect users from abuse, authenticate actors, preserve audit evidence and handle reports; the platform should not claim to be an investment broker or an IP registration authority.

## Privacy and state rules

`offers.status` = pending | accepted | declined. Negotiation drafts are stored separately in this prototype. In production, revision history and explicit bilateral approvals are required; accepting an offer in-app must not independently grant equity or issue financial instruments.

`time_entries.status` = review | approved. This prototype does not implement disputes or approval workflow automation; it displays the statuses and allows a mock submission. In production, contributors should link deliverables and owners should have role-based review permissions.

**Ownership:** idea metadata and recorded submissions do not imply that copyright protects a bare abstract idea. Work-for-hire / assignment / licensing of code, designs, trademarks, and data must be written and jurisdiction-specific. Pre-existing materials of contributors need exceptions and licensing terms.

**Time ledger:** proposed/accepted/actual hours do not represent interchangeable financial units. Rewards must be independently determined by agreement and should not be auto-calculated by raw hour count.

## Suggested backend for implementation

Next.js + TypeScript, Supabase/Postgres + RLS, server-side event/audit log, Resend (transactional email), job queue for notifications, object storage, secure file authorization and moderation dashboard.

Suggested tables: users, profiles, skills, ideas, idea_revisions, idea_visibility, needs, offer_revisions, agreements, comments, comment_replies, members, projects, tasks, milestones, deliverables, time_entries, notifications, audits, reports, disputes.

Need to specify legal jurisdiction and obtain counsel prior to designing revenue share, deferred compensation or equity grants; these can create employment, tax or securities/regulatory obligations depending on the exact arrangement and country.

## UX implementation details

- Full Arabic RTL and English LTR switch; navigation automatically mirrors.
- All demo routes are hash-based and can be loaded directly.
- Interactive components persist via localStorage.
- Screens are responsive down to mobile widths with a mobile navigation drawer.
- Email HTML uses table structure, inline styles and descriptive action buttons.
- Status tags distinguish offered hours from recorded and approved work.
- Demo data is clearly illustrative; production emails and audit timestamps are not active.


## New authentication screens (prototype)

- Routes: `#/login`, `#/register`, `#/forgot-password`
- Arabic RTL / English LTR interface; responsive desktop two-panel brand story and mobile stacked forms.
- Role choices on sign-up: idea owner, time investor, or both.
- Password show/hide, minimum-length/number checks, confirmation, strength UI, inline errors, demo sign-in, and demo account indicator in app navigation.
- Browsing and editing the prototype remain accessible in preview mode; the prototype is intentionally not protected by a backend.
- Local demo profiles contain only name, email, and selected role. **No passwords are saved or verified, no credentials are authenticated, and no recovery emails are actually sent.**
- Production integration: replace the entire mock session layer with a real auth provider (e.g., Supabase Auth); verify email, enforce sessions and role-based RLS at the database/API layer, implement password reset via trusted provider URLs, terms/versioning, rate limits, and legal policies.

## Contributor profile / trust UX

Profile records are **sample-only** in this prototype. There is no actual identity verification, credential validation, external portfolio verification, or authentic reviews. Trust signals are explicitly labelled “demo,” “not independently verified,” or “self-reported.” The summary of an incoming offer is viewable from the owner inbox profile-link in the demo, but production must enforce owner-only authorization at the API and database layers.

Member data includes headline, biography, location/time zone, weekly availability, skills, preferred compensation, optional links, indicative experience, portfolio, sample feedback, platform-seeded deliverables and idea history. The signed-in demo member can edit their basic professional details in localStorage. Private email addresses, full contracts, and unrelated offers are not exposed in public profiles.

A trusted production reputation model should calculate on-time delivery from accepted milestones and authenticated project records only; do not treat logged hours as a guarantee of competence, employment or investment performance.
