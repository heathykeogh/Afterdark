# AfterDark — Project TODO

## Design system & shell
- [x] Dark neon glassmorphism theme tokens in `client/src/index.css` (deep purple/black gradients, neon pink/magenta accents)
- [x] Google Fonts wired in `client/index.html` (display + body font)
- [x] Reusable `GlassCard` component with frosted surface + neon border
- [x] Reusable `NeonButton` (solid/outline/ghost tones, accent + pulse) and `TierBadge` components
- [x] Fluid page transition wrapper (framer-motion) between routes
- [x] Pulse animation on active card
- [x] Particle/burst effect component fired on scoring milestones
- [x] Mobile-first bottom tab navigation + desktop layout

## Data model
- [x] `players` table (couple profile: name, avatar, lifetime points, wins, losses)
- [x] `cards` table (custom + default overrides: text, tier, baseValue, durationSec, tags, mediaUrl)
- [x] `decks` table (name, description, thumbnailUrl, isDefaultEnabled)
- [x] `sessions` table (mode, tier range, status, scores, winner)
- [x] `sessionEvents` table (card played, points awarded, multipliers applied, chain depth)
- [x] `rewards` table (label, threshold type, threshold value, tier, grantedBy)
- [x] `unlockedRewards` table (player, reward, unlockedAt, redeemedAt)
- [x] `generatedWildCards` table (LLM wild card cache: prompt, effect, magnitude)
- [x] Migration generated with drizzle-kit and applied via SQL

## Scoring engine
- [x] Tier base values: Romantic, Flirty, Steamy, Wild/Extreme (exact labels)
- [x] Duration multiplier curve based on card duration
- [x] Risk-boost chain multiplier that compounds on consecutive completions
- [x] Pure scoring module in `shared/` with unit tests
- [x] Real-time per-session score tracking persisted to DB
- [x] Wild effect modifiers folded into the same calculation
- [x] Bail penalty derived from the card's own value
- [x] Per-card score breakdown surfaced in the UI

## Game modes
- [x] Session setup screen: mode select, players, tier range (starts at Romantic/level 1), point ceiling, wild card frequency
- [x] Mode A — Dual Selection: two-player drafting, per-tier loadouts, queue reorder up/down, point ceiling lock, alternating turns, live progress
- [x] Mode B — Would You Rather: alternating escalating Option A vs Option B, chooser/judge resolution
- [x] Mode C — Roulette Wheel: SVG wheel, spin physics with easing, dare + mystery penalty slices, instant task assignment
- [x] Turn resolution UI: complete / chicken-out / partner-veto with score effects
- [x] Card timer for timed cards
- [x] Match completion screen with winner resolution

## Wild Card Engine
- [x] Automatic injection based on turn thresholds + random probability (no manual drafting)
- [x] Effect types: point steal, double-or-nothing, tier escalation, forced swap, immunity
- [x] LLM generation of contextual wild card prompts (tier + mode + recent history aware)
- [x] Safe fallback to static wild deck when LLM unavailable
- [x] Generated card cache with prewarm + manual generation from Setup

## Deck Studio
- [x] Create / edit / duplicate / delete custom cards
- [x] Full parameter control: text, tier, base points, time limit, tags, media
- [x] Deck management with enable/disable toggles for default vs custom decks
- [x] JSON export of a deck
- [x] JSON import with validation and error reporting
- [x] Card background media upload (S3) mapped to specific cards
- [x] Keyword/tag/card-key media mapping so themed cards share a visual context
- [x] Live value preview from the scoring engine inside the editor

## Progression
- [x] Persistent leaderboard: match winners, lifetime points, win/loss record
- [x] Player profile stats page (cards completed, chickened out, longest chain, wilds survived, best session)
- [x] Match history list
- [x] Rewards system: point thresholds + milestone wins unlock reward tiers
- [x] Partner-granted privileges (custom rewards created by the couple, granted in-session)
- [x] Reward redemption tracking
- [x] Unlock celebration animation

## Quality
- [x] Vitest coverage for scoring engine, wild card engine, deck content and media matching (49 tests)
- [x] TypeScript clean (`pnpm check`)
- [x] Responsive verification at 390px and 1280px
- [x] Consent/safeword and age gate notice
- [x] Checkpoint saved

## Follow-ups
- [x] "Pass the phone" handoff screen between turns that hides the previous card's outcome until the next player confirms
- [x] Duel drafting is sequential and private when handoff is on — only the current drafter's board renders, the partner's queue is never displayed
- [x] Handoff can be toggled off in Setup for couples playing side by side (and dismissed inline from the curtain)
- [x] Match log hidden behind the curtain so the last outcome cannot be read through it
- [x] `passTheDevice` column migrated; router input contract and column definition (type, not-null, default) covered by tests

## Redesign — BDSM/sensual identity
- [x] Typography replaced: Bodoni Moda display, Cormorant Garamond italic for prompts, Jost for UI chrome
- [x] Colour system reworked around latex black, oxblood, crimson lacquer and candlelit gold
- [x] Material textures added: latex sheen on glass, leather grain panels, stitched edges, ornamental rules
- [x] New motion: heartbeat pulse and candle flicker alongside the neon pulse
- [x] Nav redesigned: wax-seal mark, "after hours" wordmark, drawn-underline desktop links, 56px tactile bottom tabs
- [x] Buttons rebuilt: lacquer/outline/ghost tones, accent overrides, heartbeat pulse on primary CTAs
- [x] Tier badges reworked into hardware collar tags with glyphs and intensity pips, plus a TierPlate variant with taglines
- [x] GlassCard extended with leather material, stitched edging and accent-driven glow
- [x] Card face redesigned: dealt-card motion, corner glyphs, ruled ornament, prompt set large in the italic serif, payout as the hero number
- [x] Card background textures retuned into four families (hardware/toys/warmth/voice) on latex-black bases
- [x] Score HUD sharpened: turn filament on the active side, larger totals, hot/cold chain readout
- [x] Draft board restyled: wax-seal sealed state, glyph slats in the queue, tier spines on pool rows, 32px controls
- [x] Handoff curtain restyled with a blindfold band motif in the new palette
- [x] Landing page restyled: candlelit blooms, italic serif lede, the ladder shown as four leather tier plates, ornamental rules
- [x] Setup / Studio / Ranks / Rewards headings normalised to the shared label-caps + display serif treatment (13 legacy recipes replaced)
- [x] Rewards ladder verified rendering (earlier blank panel was the loading skeleton); added a proper empty state and restyled reward cards
- [x] Velvet card-table felt texture applied behind every internal page via PageShell
- [x] Page headings restyled with label-caps eyebrows, larger display serif and an ornamental rule
- [x] Studio empty state rebuilt as a fanned deck of card backs on a stitched leather panel
- [x] Roulette wheel retuned: lacquered rim gradient, metal hub with seated screw, new slice palette
- [x] Studio card tiles restyled with tier accents, display serif titles and italic prompts
- [x] Design token tests added (9 assertions) covering tier labels, colours, taglines, glyphs, mode taglines and card textures
- [x] 404 page restyled off the light template default into the app's own dark register

## Per-tier round counts (tier plan)

- [x] Shared tier-plan model: rounds per tier, escalation order, and the current-tier resolver (`shared/tierPlan.ts`)
- [x] Tests for the tier plan: 23 assertions covering escalation order, exhaustion, skipped tiers, caps and empty-plan fallback
- [x] Persist the tier plan on the session (`tierPlan` + `resolvedRounds` columns, migration 0003 applied)
- [x] WYR and Roulette draws come from the tier the plan currently points at; wild cards are written at the reached tier
- [x] Duel drafting helpers written and unit-tested: `draftAllowance` / `draftRemaining` / `isLoadoutComplete`
- [x] Helper-level tests for plan-driven tier selection per mode (17 assertions)
- [x] Drafting helpers wired into DraftBoard: per-tier quota chips, capped picks with an explanatory toast, and sealing gated on a complete loadout
- [x] `lockLoadout` rejects a queue that does not match the plan and sorts it softest-first server-side
- [x] Wild card interrupts do not consume a planned round; regular cards consume one on complete, bail or veto
- [x] Setup UI: per-tier round steppers with presets, live round total, "opens here" marker and a segmented arc preview
- [x] WYR / Roulette always open at the lowest planned tier and only escalate upward
- [x] Duel: locked queues are sorted softest-first server-side (player ordering preserved within a tier), with 6 ordering tests
- [x] In-match progress readout: header shows current tier and round N of M, plus a segmented arc bar and a "next tier" cue
- [x] Duel drafting respects the tier plan's card counts per tier (UI quotas + server validation)
- [x] Match ends when the tier plan is exhausted, in addition to the point ceiling (`endReason` distinguishes the two)
- [x] Handoff curtain shows the incoming player their tier and round number, which is public information
- [x] Result screen notes when a match ended by playing out every planned round
- [x] Session-level tests for round consumption and end conditions (12 assertions); 143 tests passing overall
- [x] Sessions created before this feature have a null plan and keep playing on tier range alone

## Installable on phones (Android APK + PWA)

- [x] App icon set generated (192, 512, maskable 192/512, Apple touch, favicon) in the oxblood identity
- [x] Web app manifest with standalone display, portrait orientation, theme colours, icons and Play/Studio shortcuts
- [x] Service worker caching the app shell; never caches /api so scores are always live
- [x] iOS meta tags for standalone display, black-translucent status bar and home-screen title
- [x] Install page at /install: APK download plus browser install on Android, Share-sheet steps on iOS
- [x] Install entry point in the top nav and account menu, which disappears once installed
- [x] Tests covering manifest installability, service worker safety rules and download config (15 assertions)
- [x] Verified the manifest and PWA meta tags are served correctly on the live domain
- [x] Signed Android APK built with Bubblewrap (Trusted Web Activity), 2.9 MB, for sideloading
- [x] Digital Asset Links served at /.well-known/assetlinks.json so the APK opens without browser chrome
- [x] APK hosted at /download/afterdark.apk with the /install page giving step-by-step guidance
- [x] Tests covering asset links shape and the APK download redirect (5 assertions)
- [x] Live verified: assetlinks.json served on the deployed domain with the correct fingerprint
- [x] Live verified: /download/afterdark.apk returns the real 2.9 MB APK (checksum matches the build)
- [x] Live verified: APK signature matches the fingerprint published in assetlinks.json
- [x] Live verified: service worker and manifest both served on the deployed domain
- [x] In-game action rail rebuilt: full-width 56px primary with live point preview, quieter 48px bail/veto pair
- [x] Would You Rather choices enlarged to 104px targets with oversized A/B watermarks

## Duel flow audit
- [x] Loadout lock advances correctly from player A to player B (`nextDrafter`)
- [x] Curtain now fires on the drafting→active transition as well as side changes, and correctly does NOT fire on a `swap` wild where the same player keeps acting
- [x] Drafted queue is consumed strictly in order via the shared `nextQueueKey` helper (used by the server draw path, the client's remaining-count readout, and the tests)
- [x] Duel draws are queue-only — no silent fallback to random cards or the partner's queue
- [x] Exhausted loadout surfaces a clear "score the match / back to setup" escape hatch instead of an error toast
- [x] Locked queue is never rendered to the partner while handoff is on (with handoff off, both boards show by design — the couple has opted into shared-screen play)
- [x] Tests covering the duel draft/lock/handoff state machine (19 assertions)
- [x] Each side's remaining card count shown during play
