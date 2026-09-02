## Nonprofit and user group
**Nonprofit:** SFI Foundation  
**User group:** motorsports manufacturers, race teams, inspectors, and buyers who need to find safety specs and verify certified parts.

## Big Issue
SFI Foundation web modernization — ML-powered spec search, QR-based manufacturer verification, and a mobile-first UI redesign for motorsports safety certification.

Reference: old site version https://pages.opencodingsociety.com/capstone/greppers/

## Problem statement
Users need a fast and reliable way to search SFI safety specifications and verify manufacturer certifications on mobile devices because the current experience is hard to navigate, slow to search, and not optimized for modern verification workflows.

## Success statement
We know this works when users can find the correct spec in seconds, scan a QR code to verify manufacturer certification in real time, and complete key tasks easily from a phone without support help.

## Out of scope
This project will not include rewriting SFI certification standards, changing compliance policy, or replacing internal certification decision systems.

## Team approval
- [x] Ishan Jha (Scrummer)
- [x] Vayun Shekar (Technologist 1) 
- [x] Ishan Khandelwal (Technologist 2)

# Sub Issue: Build the SFI Foundation Frontend (Full Site Implementation)

**Parent Issue:** SFI Foundation Web Modernization — ML-powered spec search, QR-based manufacturer verification, and a mobile-first UI redesign
**Owner:** Ishan Jha
**Role on team:** Scrummer / Lead Builder for this Sub Issue
**Related Sub Issues:** Sub Issue — Testing & QA (owner: TBD), Sub Issue — Deployment (owner: TBD)

---

## Summary

Design and build the complete SFI Foundation frontend application: a mobile-first web app that lets motorsports manufacturers, race teams, inspectors, and buyers search SFI safety specifications and verify certified parts via QR code. This Sub Issue covers the full construction of the site — architecture, UI, and all three core features — up through a stable, feature-complete build deployed to a staging environment. Testing/QA and production deployment are handled by separate Sub Issues and are explicitly out of scope here.

## Deliverable

A single, feature-complete frontend codebase (merged to `main`) implementing:

1. ML-powered spec search
2. QR-based manufacturer/part verification
3. Mobile-first UI redesign across all core pages

...running successfully on a staging environment, with no known build-breaking defects, ready to be handed off for formal testing.

## Background / Context

The current site (reference: https://pages.opencodingsociety.com/capstone/greppers/) is hard to navigate, slow to search, and not optimized for mobile verification workflows. This Sub Issue is the primary build effort that turns the parent issue's success statement into working software:

> Users can find the correct spec in seconds, scan a QR code to verify manufacturer certification in real time, and complete key tasks easily from a phone without support help.

This Sub Issue is intentionally broad in scope but singular in ownership: Ishan Jha owns the end-to-end build so there is one clear point of accountability for "is the site built," separate from "is the site tested" and "is the site live."

---

## Functional Requirements

### 1. Spec Search (ML-powered)

- Ingest and normalize the SFI spec dataset (spec number, title, category, description, associated certified parts/manufacturers) from the reference site or best-available source.
- Build a search interface with a prominent search bar as the primary landing interaction.
- Support natural-language / semantic queries (e.g., "helmet certification for oval track racing") in addition to exact spec-number lookup, using an embeddings-based or hosted semantic search approach.
- Return ranked, relevant results with a graceful fallback to keyword search if the ML service is unavailable or slow.
- Provide a spec detail page showing full spec metadata and any linked certified manufacturers/parts.
- Support filtering/browsing by category as a secondary discovery path for users who don't have a specific query.

### 2. QR-Based Manufacturer Verification

- Implement in-browser QR code scanning using the device camera, with proper permission handling and a clear fallback (e.g., manual code entry) if camera access is denied or unavailable.
- Define and implement the QR payload format (manufacturer ID + part/certification ID).
- On scan, query certification data and display a clear real-time result: **Certified**, **Expired**, or **Not Found / Unverified**.
- Handle all error states explicitly (camera permission denied, malformed QR, no network, no match) with plain-language messaging — no raw errors or blank screens.
- Build/seed a certification data source (manufacturer, part, status, issue date, expiration) sufficient to demonstrate all three verification outcomes.

### 3. Mobile-First UI Redesign

- Design and build all core flows mobile-first (search, verify, browse), then progressively enhance for tablet/desktop.
- Establish a shared design system: color palette, typography, spacing scale, and reusable components (nav, cards, buttons, inputs, modals) consistent with SFI branding.
- Ensure touch-friendly tap targets, readable type at common mobile widths (360px–430px), and no horizontal scrolling.
- Build primary navigation connecting Search, Verify, and Browse as first-class, equally accessible entry points from the home screen.
- Run a baseline accessibility pass: sufficient color contrast, alt text on images/icons, visible focus states, semantic HTML structure.

---

## Technical Requirements

- Frontend framework, hosting, and search/embedding provider to be selected and documented by the owner in an ADR (architecture decision record) committed to the repo before implementation begins.
- Codebase must build cleanly via CI on every push to `main`.
- All environment-specific config (API keys, endpoints) must be handled via environment variables — no secrets committed to the repo.
- Code must be organized to allow the Testing Sub Issue to run automated and manual test passes without needing architecture changes (e.g., testable component boundaries, seed/mock data paths clearly separated from production data paths).
- A staging environment must be reachable via a public or shareable URL for handoff to Testing and Deployment Sub Issues.

---

## Task Breakdown

- [ ] Write and commit architecture decision record (framework, hosting, search approach)
- [ ] Scaffold project (repo, linting, formatting, CI build check)
- [ ] Build shared design system and base layout components
- [ ] Ingest/normalize spec dataset
- [ ] Build baseline keyword search (search bar, results list, spec detail page)
- [ ] Integrate ML/semantic search layer with fallback to keyword search
- [ ] Add category filtering/browse view
- [ ] Define QR payload format and seed manufacturer/certification test data
- [ ] Build QR scan flow (camera access, permissions, error states)
- [ ] Build certification lookup and result screen (Certified / Expired / Not Found)
- [ ] Build mobile-first home page and primary navigation
- [ ] Implement responsive behavior across mobile, tablet, desktop breakpoints
- [ ] Run and resolve baseline accessibility pass
- [ ] Deploy feature-complete build to staging environment
- [ ] Document known limitations/edge cases for the Testing Sub Issue

---

## Dependencies & Handoffs

- **Blocks:** Sub Issue — Testing & QA cannot begin full test execution until this Sub Issue reaches a feature-complete staging build.
- **Blocks:** Sub Issue — Deployment cannot promote to production until Testing & QA signs off on this build.
- **Depends on:** None (this is the foundational build Sub Issue).

## Out of Scope

- Formal test planning, test case execution, and bug triage (owned by the Testing & QA Sub Issue).
- Production deployment, release process, monitoring, and rollback procedures (owned by the Deployment Sub Issue).
- Rewriting SFI certification standards, changing compliance policy, or replacing internal certification decision systems (out of scope for the entire parent issue).

---

## Done Condition

This Sub Issue is complete when:

1. All three core features (ML spec search, QR verification, mobile-first UI) are implemented and functioning end-to-end.
2. The application builds successfully via CI with no errors on `main`.
3. The build is deployed and reachable on a staging environment.
4. A user can, on a real mobile device, search for a spec and find a correct result, scan a QR code and receive a real-time certification result, and navigate all core flows without encountering unhandled errors.
5. The architecture decision record and any known limitations are documented in the repo for handoff to the Testing & QA Sub Issue.

## Definition of Done Checklist

- [ ] All functional requirements above implemented
- [ ] All tasks in Task Breakdown completed
- [ ] CI passing on `main`
- [ ] Staging URL live and shared with team
- [ ] Handoff notes written for Testing & QA Sub Issue