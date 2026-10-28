# Mobile Release Radar — week of 2026-10-18 → 2026-10-25

**Run date:** Sunday, 25 October 2026 (UTC)
**Horizon:** deadlines through 2027-01-23 (90 days)
**Items found:** 8 (iOS 3 / Android 4 / Both 1) · **High impact:** 4

> Scope note: nothing brand-new was *announced* by Google Play inside this 7-day window — the newest Play policy announcement is still 2026-07-15. The action pressure this week is on the Apple guidelines revision (published 16 Oct, nine days ago, no transition period) and on a Play deadline that is **7 days out**.

---

## 1. Act this week

### 1. Play target API 36 — extension cutoff hits 1 Nov 2026 (7 days)
- **What:** Since 2026-08-31, new apps and all app updates must target **Android 16 (API 36)**; existing apps must target **API 35** to stay available to new users on newer Android versions. Developers who needed more time could request an extension — **the extension only runs to 2026-11-01**.
- **Source:** https://support.google.com/googleplay/android-developer/answer/11926878
- **Deadline:** 2026-11-01 · **days_remaining:** 7 · **platform:** Android · **impact:** High · **effort:** Low if already on API 36/35; Medium–High if still below
- **Next action:** open Play Console → Policy status. If any app is flagged for target-API non-compliance and the extension is not already approved, you have one week. Anything you ship from 1 Nov onward must be built against API 36 for new apps/updates.

### 2. App Review Guideline 1.2 — UGC moderation now explicitly covers nonconsensual intimate imagery, incl. AI-generated
- **What:** Apps hosting user-generated content must "proactively prevent and remove" NCII, including imagery generated with AI tools, and must keep report/block flows working. Failing adequate safeguards, or not remediating after notice, is framed as a Developer Code of Conduct violation and grounds for removal.
- **Source:** https://developer.apple.com/news/?id=vvzx6cul · https://developer.apple.com/app-store/review/guidelines/
- **Deadline:** effective on publication (2026-10-16), no transition period · **platform:** iOS · **impact:** High · **effort:** Medium
- **Next action:** audit every image-bearing UGC surface (uploads, generated previews, share sheets). If you have any AI image generation or editing feature, confirm the abuse path is blocked *and* documented in Notes for Review.

### 3. App Review Guideline 2.5.19 — hidden / post-approval "bait-and-switch" features
- **What:** New standalone guideline: shipping a clean binary and enabling features after approval (e.g. via remote flag) is a removal + Developer Program termination risk. License to ship less in the binary and more behind flags just got narrower.
- **Source:** https://developer.apple.com/news/?id=vvzx6cul
- **Deadline:** effective 2026-10-16 · **platform:** iOS · **impact:** High · **effort:** Low–Medium
- **Next action:** list every remotely-gated feature that materially changes app behaviour; anything that could read as "not in the version submitted" should either ship in the binary or be described specifically in Notes for Review (2.3.1(a) already required specificity — this makes the consequence explicit).

### 4. New Guideline 2.3.14 — creative assets
- **What:** Brand-new guideline covering creative assets (screenshots, previews, marketing imagery). New rule with no stated transition period.
- **Source:** https://developer.apple.com/news?id=92th7e5i
- **Deadline:** effective 2026-10-16 · **platform:** iOS · **impact:** Medium · **effort:** Low
- **Next action:** read 2.3.14 in full and diff it against your current App Store screenshots/preview frames before the next submission. This is the one change whose scope is least documented in Apple's own summary — treat it as a checklist item, not a known safe.

### 5. Play foreground services — geofencing no longer an approved use case
- **What:** Geofencing is being removed as an approved foreground-services use case; move to the Geofence API.
- **Source:** https://support.google.com/googleplay/android-developer/table/12921780
- **Deadline:** 2027-01-27 · **days_remaining:** 94 · **platform:** Android · **impact:** High · **effort:** Medium
- **Next action:** grep the manifest for `FOREGROUND_SERVICE` + `ACCESS_BACKGROUND_LOCATION` usage tied to geofence entry/exit. This is the item in the January cluster most likely to require an actual refactor.

---

## 2. On the horizon

| Date | Days left | Platform | Requirement |
|---|---|---|---|
| 2026-11-01 | 7 | Android | End of the target-API-36 extension window (https://support.google.com/googleplay/android-developer/answer/11926878) |
| 2027-01-27 | 94 | Android | Contacts Permissions policy — broad contacts access requires the Android Contact Picker (https://support.google.com/googleplay/android-developer/answer/16909972) |
| 2027-01-27 | 94 | Android | Location Permissions update — location button becomes the recommended minimum scope for precise location (https://support.google.com/googleplay/android-developer/answer/13986130) |
| 2027-01-27 | 94 | Android | SMS/Call Log policy — account verification via phone call no longer a permitted `READ_CALL_LOG` use case; use Digital Credentials API or SMS Retriever (https://support.google.com/googleplay/android-developer/answer/13986130) |
| 2027-01-27 | 94 | Android | Geofencing removed as an approved foreground-services use case (see item 5) |

**Already in force (no longer "upcoming" — verify once, then it drops off this table):**
- iOS/iPadOS apps uploaded to App Store Connect must target **iOS 13+** (since 2026-09-09).
- Apps must be built with **Xcode 26+** using an SDK for iOS 26 / iPadOS 26 / tvOS 26 / visionOS 26 / watchOS 26 (since 2026-04-28). **Xcode 27.1 (Swift 6.4) shipped 2026-10-15 and App Store Connect accepts its builds** — upgrade is available, not yet mandated.
- Play package-name registration for Android developer verification: required from 2026-09-30 in Brazil, Indonesia, Singapore and Thailand; global rollout 2027. 99% of Play apps were auto-registered — confirm yours on the Play Console Home page.
- Apple age-rating questions, Apple privacy manifest, Play Data safety — see checklist below.

---

## 3. Checklist status

No app inventory or console access was available for this run, so status is reported as *requires check* rather than guessed.

| # | Standing item | Requirement in force | Status |
|---|---|---|---|
| 1 | Play target API level | New apps + updates: API 36 from 2026-08-31; existing apps: API 35 to stay discoverable | **Requires check** — Play Console → Policy status |
| 2 | Apple privacy manifest | `PrivacyInfo.xcprivacy` with required-reason API declarations for listed SDKs | **Requires check** — verify file ships in every target |
| 3 | Play Data safety form | Must accurately declare all data access/collection/sharing; privacy policy must be live, public, non-PDF, non-geofenced | **Requires check** — App content → Data safety |
| 4 | Age ratings | Apple's new rating system auto-applied since 2026-01-31; new questionnaires must be answered or submissions are interrupted | **Requires check** — App Information per app |
| 5 | Billing compliance | Play Billing for digital goods; App Store external-purchase link entitlements vary by region (3.1.1(a) was reworded 2026-10-16) | **Requires check** — region-by-region |
| 6 | Account deletion | In-app deletion path required, not just a support email | **Requires check** |

---

## 4. Watched, no action

- **Section 5 wording hardened** (2026-10-16): apps facilitating human trafficking or child exploitation are removed from the App Store *and* blocked from alternative distribution. No engineering work unless you host such content — then it is a removal, not a remediation.
- **Xcode 27.1 / Swift 6.4** released 2026-10-15: adds SDKs for iOS 27.1 et al., Swift 6.4's only listed feature is a Previews canvas override for alternate displays (relevant if you target iPhone Duo). Known issue: Mac Catalyst projects targeting iOS 27.1 need an explicit Mac Catalyst 27.0 deployment target.
- **App Store Connect API 4.5.1** (2026-10-06) and a TestFlight update (2026-10-14) — automation tooling only.
- **Android developer verification** global rollout remains scheduled for 2027; no new date announced this week.

---

## Sources (primary only)

- https://developer.apple.com/news/?id=vvzx6cul — Apple, 2026-10-16 guideline changes (1.2, 2.5.19, §5)
- https://developer.apple.com/news?id=92th7e5i — Apple, 2026-10-16 full changelog incl. 2.3.14
- https://developer.apple.com/news/upcoming-requirements/ — Apple standing requirements
- https://support.google.com/googleplay/android-developer/table/12921780 — Play policy deadlines
- https://support.google.com/googleplay/android-developer/answer/11926878 — Play target API levels
- https://developer.android.com/distribute/play-policies — Play/Android deadline timeline
- https://developer.android.com/developer-verification — Android developer verification

*Third-party coverage (TechCrunch 2026-10-19, AppleInsider 2026-10-17) was used only to locate the Apple announcement; no claim in this brief rests on it.*
