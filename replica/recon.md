# Recon map: Tinder (iOS)

Scope: the core dating loop: sign up, profile, swipe deck, match, chat, safety
tools, and the paid tiers and consumables that gate it. Group Hangouts and the
Apple TV and visionOS apps are listed but come later.
For: not stated yet. Assumed: a product to sell. Confirm before `/replica-entrepreneur`.
Date: 2026-11-18

**Evidence note.** Read on 2026-11-18: the US and FR App Store listings and
Tinder's public safety pages. The help center (help.tinder.com) sits behind a
Cloudflare bot challenge, and the skill rules forbid getting around that, so it
was not read. The homepage needs JavaScript, so it gave nothing. Anything
marked **medium** or **guess** below was not seen in those pages. It describes
how the app is widely known to work, and needs confirming against the help
center in a normal browser or against your own account.

## Sources

| # | source | URL | notes |
| --- | --- | --- | --- |
| 1 | app store listing (US) | https://apps.apple.com/us/app/tinder-dating-app-chat-date/id547702041 | pitch, IAP list in USD, privacy labels, version history, reviews. Read. |
| 2 | app store listing (FR) | https://apps.apple.com/fr/app/tinder-appli-de-rencontre/id547702041 | IAP list in EUR. Platinum appears here and not in the US top-10 IAP list. Read. |
| 3 | safety tips | https://policies.tinder.com/safety/intl/en | reporting reasons, meeting-safety guidance. Read. |
| 4 | safety features | https://policies.tinder.com/community-resources/safety-features | Safety Center, unmatch, block, block contacts, photo verification, verified-only chat, message nudges, contact-exchange alert, traveler alert. Read. |
| 5 | help center | https://www.help.tinder.com/hc/en-us | **blocked** (Cloudflare challenge). Read it yourself in a browser. It is the best feature list. |
| 6 | marketing site | https://tinder.com | JavaScript only, no content without a browser. |
| 7 | App Store screenshots 1–6 | https://is1-ssl.mzstatic.com/image/thumb/PurpleSource221/v4/0c/49/cd/0c49cdf7-a4f8-3f89-defb-89684545719d/Screen_01_ASENUS.png/600x1300bb.jpg (same pattern for Screen_02…06, listed in the appendix) | **not downloaded**: the image host is blocked from this session. Save them into `replica/screens/` by hand. Reference only, never shipped. |
| 8 | your own account | — | not used. Click through it on your phone to fill in the states marked "?" below. |

Key facts from the listing (source 1 unless noted):

- 4.2★ from 1.8M ratings, Editors' Choice, #9 in Lifestyle, 18+ with age assurance, 478.5 MB, iOS 16+, 55 languages.
- Pitch bullets: explore profiles, match nearby or worldwide, answer prompts, add photos and interests, **Double Date** (bring a friend), **let a friend know when you're meeting someone**, chat with safety tools.
- Latest "major update": **Group Hangouts**: bring friends, pick an activity, meet other groups.
- Tiers: Tinder Plus, Gold and Platinum, as auto-renewing Apple subscriptions. Free tier: "send Likes, match, and chat".
- IAP (US): Plus $9.99; Gold $13.99 / $14.99 / $18.99 / $24.99; 1 Boost $3.99 / $6.99 / $7.99; 3 Super Likes $9.99; 5 Super Likes $4.99. The listing gives no durations or pack sizes beyond these labels.
- IAP (FR, source 2): Plus €8.99; Gold €13.99 / €16.49 / €27.49; Platinum €16.99 / €32.99; 1 Boost €7.99 / €9.99.
- Version notes, weekly releases (17.39–17.44): "find and connect with people who want what you want—whether it's a spark, a story, or something long-term". That points to relationship-intent matching.
- Privacy labels: precise and coarse location, contacts (used for Block Contacts), photos and videos, sensitive info, purchases, phone number, email. Identifiers are used for tracking.

## Core loop

Swipe through a deck of nearby profiles. A mutual Like makes a match, and a match unlocks chat. Users pay to be seen more (Boost, Super Like) and to see who already liked them (Likes You).

## Screens

| ID | screen | route / how to reach | purpose | key components | states seen | confidence |
| --- | --- | --- | --- | --- | --- | --- |
| S01 | Welcome / sign in | first launch | create an account or log in | logo, auth buttons (phone, Apple, Google), terms links | default, error, banned? | medium |
| S02 | Onboarding steps | after first sign in | name, birthday (18+ gate), gender, who to show, relationship intent, photos, interests, location permission | step header and progress, inputs, chips, photo grid, permission prompt | each step: empty, invalid, valid; under-18 block | medium (intent: high, from version notes) |
| S03 | Discovery deck | home tab | rate profiles one by one | swipe card stack, Nope / Super Like / Like / Boost / Rewind buttons, verified badge, distance | filled, loading, out of profiles, out of likes, Boost active | high (card and Like from listing), medium (button row) |
| S04 | Profile detail | tap a card, or open from a match | the full profile | photo carousel, bio, prompt answers, interests, intent, verified badge, report entry | own vs other, verified vs not | high |
| S05 | It's a match | mutual Like | celebrate, then start chatting | modal over the deck, both photos, quick message box, keep swiping | — | medium |
| S06 | Matches & messages | chat tab | new matches strip and conversation list | horizontal avatar row, conversation rows with unread state | empty, filled, unmatched removed | high |
| S07 | Chat thread | tap a conversation | messaging | bubbles, composer, GIF/media?, safety shield, overflow menu (unmatch, report), "Are you sure?" nudge, contact-exchange alert | empty (new match), filled, flagged message, verified-only lock | high (safety parts from source 4) |
| S08 | Likes You | tab or badge | grid of people who already liked you | grid, blurred for free users, upsell CTA, filters | locked (free), unlocked (Gold+) | medium (a reviewer's complaint about "paying to see who's swiped on me", source 1) |
| S09 | Explore / modes | tab | Double Date, Group Hangouts, other modes | mode tiles, friend invite | — | medium (modes named in source 1) |
| S10 | Edit profile | profile tab | photos, bio, prompts, interests, intent | reorderable photo grid, text areas, prompt picker, interest chips, preview toggle | incomplete, complete | high |
| S11 | Photo verification | profile, or verified-only chat gate | video selfie compared to profile photos | camera, instructions, progress, result | pending, verified, failed | high (source 4) |
| S12 | Discovery settings | settings | distance, age range, who to show, global/location, filters (interests) | sliders, toggles, chips | free vs paid filters? | medium |
| S13 | Account settings | profile → settings | account, notifications, Block Contacts, privacy, delete account | list rows, toggles, contacts picker | — | high (Block Contacts), medium (rest) |
| S14 | Plan paywall | tap a locked feature or upgrade | choose Plus / Gold / Platinum and a length | plan cards, feature comparison, Apple purchase sheet, restore | each locked-feature entry point | high (tiers from source 1) |
| S15 | Consumables store | Boost or Super Like button with zero balance | buy Boosts and Super Likes | pack options, Apple purchase sheet | zero balance, purchase success | high |
| S16 | Safety Center | shield icon, all over the app | guides, tools, resources | article list, tool shortcuts | — | high (source 4) |
| S17 | Report / block / unmatch | profile or chat overflow menu | report a user with a reason, unmatch, block | reason list (money requests, underage, harassment, in-person behaviour, fake profile, spam), free text, confirm | from deck, from chat, after unmatch | high (sources 3, 4) |
| S18 | Share date plans | chat or Safety Center | tell a friend who, where and when | match picker, place, time, contact picker, share sheet | — | high (named in source 1), medium (fields) |
| S19 | Traveler alert | opening the app in a flagged country | warn LGBTQ+ users, offer to hide the profile | full-screen notice, hide-profile toggle | — | high (source 4) |

## Flows

```
F01 New user creates a profile
    S01 -> S02 (name, birthday, gender, show me, intent, photos, interests, location) -> S03
    happy path clicks: ~14 (measure in your own account)
    edge: under 18, location denied, too few photos, phone code fails, existing account

F02 Swipe and match (the core loop)
    S03 -> (S04) -> Like -> S05 -> S07
    happy path clicks: 1 swipe per profile, 2 taps from match to first message
    edge: deck runs out, like limit reached (upsell), match while offline (push), Rewind after a Nope (paid)

F03 Chat with a match
    S06 -> S07 -> send
    edge: "Are you sure?" nudge before sending, receiver flags the message, contact info detected (alert),
          match only takes messages from verified users (verify gate, S11), other side unmatches mid-chat

F04 See who liked you (upgrade)
    S08 (blurred) -> S14 -> Apple sheet -> S08 unlocked
    edge: purchase cancelled, restore purchases, subscription lapses

F05 Boost or Super Like
    S03 -> Boost / Super Like -> (S15 when balance is 0) -> active
    edge: Boost timer while backgrounded, Super Like received (highlighted card)

F06 Get photo verified
    S10 -> S11 -> video selfie -> verified badge
    edge: face does not match the photos, poor lighting, re-verify after photo changes (reviewer: re-verify after location changes)

F07 Unmatch, block, report
    S07 or S04 -> overflow -> S17 -> reason -> done
    edge: report after unmatching (allowed, source 4), Block Contacts from S13

F08 Change discovery settings
    S13 -> S12 -> deck refreshes

F09 Share date plans with a friend
    S07 or S16 -> S18 -> pick match, place, time, contact -> share

F10 Double Date
    S09 -> invite a friend -> pair profile -> swipe on pairs -> group chat
    edge: friend has no account (invite link), friend leaves the pair
```

## Components

| component | variants | states | used on |
| --- | --- | --- | --- |
| Swipe card | profile, pair (Double Date), ad? | idle, dragging (Like/Nope stamp), flying out, Super Liked, Boosted | S03 |
| Action button row | nope, rewind, super like, like, boost | default, pressed, disabled (no balance), locked (paid) | S03 |
| Photo carousel | card, full profile | segment indicator, tap left/right, loading | S03, S04 |
| Verified badge | small, large | — | S03, S04, S06, S07 |
| Chip | interest, intent, filter | unselected, selected, disabled | S02, S04, S10, S12 |
| Photo grid | edit (reorderable), onboarding | empty slot, uploading, filled, error | S02, S10 |
| Prompt answer card | text | empty, filled | S04, S10 |
| Match modal | — | entering, idle | S05 |
| Avatar row | new matches, likes | unread dot, Super Like ring | S06 |
| Conversation row | — | unread, read, typing? | S06 |
| Message bubble | sent, received, system | sending, sent, flagged | S07 |
| Safety nudge | "Are you sure?", "Does this bother you?", contact-exchange alert | shown, dismissed | S07 |
| Range slider | distance, age | — | S12 |
| Paywall plan card | Plus, Gold, Platinum | selected, best value, current plan | S14 |
| Blur-lock overlay | grid tile | locked, unlocked | S08 |
| Bottom tab bar | 4–5 tabs | active, badge | all |
| Bottom sheet / action sheet | report reasons, overflow | — | S07, S17 |
| Toast | success, error | — | all |

## Inferred data model

```
User          id, phone, email, birthdate, created_at, status (active | hidden | banned | deleted),
              last_active_at, location (point, coarse), country
              evidence: S01, S02, privacy labels (source 1)        confidence: high

Profile       user_id, name, gender, show_me (genders), intent (enum), bio, job?, school?,
              distance_max_km, age_min, age_max, global_mode (bool), verified (bool), hidden (bool)
              evidence: S02, S10, S12, version notes                confidence: medium

Photo         id, user_id, url, position, moderation_status         confidence: high
PromptAnswer  id, user_id, prompt_id, text, position                confidence: high (listing "answer prompts")
Interest      id, label; UserInterest (user_id, interest_id)        confidence: high

Swipe         id, from_user, to_user, kind (like | nope | super_like), created_at, undone (bool)
              unique (from_user, to_user)                           confidence: high
Match         id, user_a, user_b, created_at, unmatched_by?, unmatched_at?
              evidence: S05, S06, unmatch (source 4)                confidence: high
Message       id, match_id, sender_id, body, created_at, flagged_by_sender_nudge (bool),
              reported (bool), read_at                               confidence: high

Block         blocker_id, blocked_user_id | contact_hash, created_at
              evidence: Block Profile and Block Contacts (source 4)  confidence: high
Report        id, reporter_id, reported_id, reason, message_id?, details, status   confidence: high
Verification  user_id, video_ref, status (pending | passed | failed), checked_at   confidence: high

Subscription  user_id, tier (plus | gold | platinum), product_id, period, expires_at,
              store (apple | google), original_transaction_id      confidence: high
Wallet        user_id, super_likes, boosts                           confidence: medium
Boost         id, user_id, started_at, ends_at                       confidence: medium
DatePlanShare id, user_id, match_id, place, at, shared_with (contact)   confidence: guess (fields)
DoubleDatePair id, user_a, user_b, status                            confidence: guess
```

Relationships: a User has one Profile and many Photos, PromptAnswers and Interests. A pair of Users has at most one Swipe each way. Two Likes make one Match. A Match has many Messages. A User has many Blocks and Reports, one Verification, at most one active Subscription and one Wallet.

## Feature matrix

See `features.csv`. Must: 17, should: 14, could: 9, skip: 5.

## Out of scope (cannot or should not be cloned)

- **The network.** Tinder's users and their profiles. Your clone starts with zero, and cold start in one city is the real problem.
- **Ranking data.** Years of swipe history behind their recommendations. You rebuild a simple ranker, not theirs.
- **The brand.** Name, flame logo, the swipe-stamp artwork, copy, the "It's a Match" wording and look. `/replica-brand` replaces all of it.
- **Apple TV and visionOS apps.** Not part of the core loop.
- **Their moderation models.** The "Are you sure?" and contact-detection features can be rebuilt, but with your own rules or a vendor's model.

## Size

Screens 19, flows 10, entities 16. Hard parts:

1. **Discovery ranking with geo queries**: a fast deck that excludes everyone already swiped, blocked or hidden, inside distance, age and intent filters, at scale (PostGIS plus a precomputed queue).
2. **Trust and safety**: age assurance, photo verification (liveness and face match through a vendor), message nudges, report handling, and a moderation queue for photos. App Store review will check this for an 18+ dating app with user content.
3. **Realtime chat plus Apple subscriptions**: push, read state, unmatch tearing down threads, and server-side receipt validation for 3 tiers and consumables.

Size: **L** (a quarter) for the full scope above. The core loop alone (S01–S07, S10, S17, one paid tier) is **M** (a few weeks). Cold start is a business problem, not a build size.

## Appendix: screenshot URLs (source 7)

Append `/600x1300bb.jpg` to each to download.

- Screen_01: https://is1-ssl.mzstatic.com/image/thumb/PurpleSource221/v4/0c/49/cd/0c49cdf7-a4f8-3f89-defb-89684545719d/Screen_01_ASENUS.png
- Screen_02: https://is1-ssl.mzstatic.com/image/thumb/PurpleSource211/v4/57/7a/da/577adaef-4d2c-b0c3-db5f-0ef9304a22ed/Screen_02_ASENUK.png
- Screen_03: https://is1-ssl.mzstatic.com/image/thumb/PurpleSource211/v4/96/4b/6c/964b6c83-da87-8dd2-6837-581675412250/Screen_03_ASENUK.png
- Screen_04: https://is1-ssl.mzstatic.com/image/thumb/PurpleSource211/v4/ac/13/88/ac138824-b526-48d1-acdc-a844850147b8/Screen_04_ASENUK.png
- Screen_05: https://is1-ssl.mzstatic.com/image/thumb/PurpleSource211/v4/29/5c/b3/295cb369-8dcc-8cbc-b0ee-edf2573a74e2/Screen_05_ASENUS.png
- Screen_06: https://is1-ssl.mzstatic.com/image/thumb/PurpleSource221/v4/99/c6/2e/99c62ea1-8af4-d188-57c8-e5e7436fab31/Screen_06_ASENUS.png
