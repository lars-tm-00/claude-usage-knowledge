# Go High Level + ChatGPT Ads

A practical guide to running ChatGPT Ads campaigns for an offer built on Go High Level
(GHL) — campaign setup, conversion tracking, landing pages, and the product-side prep that
has to happen before you spend a single euro.

## 1. Before you launch: keep the offer simple

The single biggest mistake in this whole workflow is packing too much into the product
you're advertising. Cold traffic from an ad has zero context — one clear feature/outcome
converts far better than a bundle of ten things you personally find cool. Pick ONE thing
(e.g. a Voice AI website widget, an AI-generated website) and sell that.

If you're building a SaaS-style tiered offer on top of GHL to sell via ads:

- Use the SaaS Configurator (GHL Pro plan, $497/mo, needed for full automation of
  reselling) to build 2-3 pricing tiers in one Category (each tier must have at least the
  same features as the one below it, never fewer).
- Skip the free-trial tier if your offer already has a free interactive demo elsewhere
  (e.g. a live widget the visitor can test on the landing page) — you want the fastest
  possible path to a paid conversion given ad spend is already committed.
- Structure minute/usage-based tiers (for voice/AI features) with healthy margin — e.g. if
  a minute costs you ~10 cents, price the entry tier so 100 minutes nets a comfortable
  margin, and price the top "unlimited" tier deliberately high mainly to nudge people
  toward the middle tier.
- Cross-check your configuration against ChatGPT (it can hold context on your whole GHL
  setup across a conversation) as a sanity-check partner before committing.

## 2. Set up conversion tracking BEFORE building the campaign

You need this if you want to optimize for Conversions rather than Clicks.

1. In ChatGPT Ads Manager → **Conversions einrichten**, create a data source and get a
   Pixel ID + site-wide installation snippet.
2. Install the snippet **site-wide** (in the `<head>`, every page) — you can literally
   prompt an AI page builder to do this: _"Füge folgenden OpenAI Ads Pixel seitweit auf
   [site] in den Headbereich ein, sodass er auf jeder Seite gelesen wird. Direkt umsetzen
   und bestätigen."_ Then publish.
3. **Compliance**: if you add this tracking pixel, it must be disclosed in your cookie
   banner.
4. Create a **second, separate Conversion Event** specifically for the purchase/signup
   action (e.g. "Abonnement erstellt" for a subscription product) — this gets its own
   pixel snippet, installed ONLY on the confirmation/thank-you page (e.g. `/danke`), not
   site-wide.
5. **Test it**: in Ads Manager, open the event stream ("Ereignisstream anzeigen"), click
   "Abfrage starten", visit your own thank-you page in a new tab, then check back — you
   should see a successful event logged (JSON payload). Pause the query when done.

## 3. Campaign setup

- **Objective**: Reichweite (Reach) spreads broadly and isn't targeted enough for a sales
  goal. Klicks (Clicks) is the default safe choice, especially if you're an affiliate and
  legally can't redirect straight to a checkout page. Conversions requires the pixel setup
  above and a page you fully control as the destination.
- **Targeting**: can be very granular — down to individual cities/postal codes (unlike
  Meta, which shows more broadly even in small areas). Check whether your offer would even
  realistically show for a narrowly-targeted small location before relying on it.
- **Custom audiences are not yet supported for EEA/Switzerland** campaigns (no personalized
  ads there yet) — data is still collected for future use, just not actionable yet.
- **Platform**: choose iOS app / Android app / Web based on where your actual audience is
  — don't default to "all three" without thinking about it.
- **A/B testing across platforms**: create separate campaigns, each scoped to ONE platform
  only, rather than mixing platforms in one campaign, if you want to compare which
  platform actually performs for you.
- **Budget**: no end date if it's working — let it run and scale if good, leave as-is if
  mediocre. The platform can spend up to 2× your daily budget on a strong day, but total
  7-day spend is capped at 7× the daily budget (it self-balances across the week).
- **Auto-translation** ("Textanpassung"): turn this OFF unless you actually want your ad
  shown (auto-translated) to people who don't speak your ad's language.
- **Bidding**: choose "Ergebnisse maximieren" (maximize results / auto-bid) for a new,
  untested campaign, or set a manual max-CPC. If going manual, consider starting HIGHER
  than the platform's suggested range (e.g. suggested 2-3€ → set 4€) — a higher ceiling
  buys better visibility early on and the platform rarely spends the full max anyway; it
  optimizes down when it can, and early competition is lower than it'll become later.
- **Kontexthinweise** (context hints, optional field): fill this in explicitly, especially
  if your landing page is thin on text — describe your actual target audience (e.g.
  "decision-makers/Geschäftsführer", not employees who can't decide) so the platform
  doesn't have to guess purely from page content.
- **Tracking URL parameters**: have ChatGPT or Claude generate the query-parameter
  template with the platform's dynamic placeholders (e.g. `{ad_id}`, `{campaign_id}`) —
  natively supported, and an LLM does this more reliably than doing it by hand.

## 4. Landing page — don't link directly to the offer

If you're an affiliate (or otherwise can't send cold traffic straight to a checkout), build
your OWN intermediate landing page in GHL rather than linking out:

- Use GHL's AI Studio / Funnel AI to generate a first draft fast — a detailed prompt (goal
  of the page, affiliate disclosure near CTA buttons, a trust/social-proof bar) produces a
  meaningfully better result than a generic prompt. Full AI generation of a page costs
  roughly €0.70 in tokens; a first-time free allowance often applies.
  Funnel AI specifically: Seiten → Funnels → Neuer Funnel → Funnel AI → pick company/niche,
  goal (leads / appointments / present work / sell products), and tone — generates a full
  page with scroll animations and a coherent color scheme in under a minute (~99 cents
  after any free-generation allowance runs out — cheap relative to building from scratch).
- **Visual edits are free** (no token cost) — only full AI (re-)generation costs tokens.
  Swap images/text via the visual editor once the AI draft is close.
- Always click **veröffentlichen/aktualisieren** (publish) and check the live preview
  before setting the page as your ad's destination URL — a page isn't live until published.

## 5. Ad creation

- Title has a hard character limit (~50 chars) and may truncate on some placements — front-
  load the essential benefit.
- Write the headline around the visitor's actual benefit (e.g. "Deine Website beantwortet
  Fragen selbst — rund um die Uhr", not a feature name).
- Create at least 2 ad variations to test framing rather than accepting only the
  platform's auto-suggested ad.
- Upload a company logo at the account level (flagged as an error/missing field if absent).
- Currently card payment only for billing.

## 6. After launch

- Expect a review/approval delay before ads actually start serving.
- Expect a further delay before impressions appear at all — it can take ~2 hours, then
  jump from 0 to thousands of impressions once it starts.
- Create multiple ad variations relatively soon after launch (not just 1-2) so the system
  has different conversational contexts to match against — the platform itself recommends
  this.
- **Scaling once profitable**: either broaden the SAME niche to other ad platforms
  (Meta/Facebook/Instagram), or replicate the same narrow-niche playbook for OTHER niches
  (same product, different vertical landing pages, e.g. `/dachdecker`, `/immobilienmakler`)
  — narrow niches face less ad competition than going broad.
- Consider setting up a "Managed Agent" (an AI agent with API access to your Ads account)
  to review performance nightly and produce a morning report with suggested changes —
  configured via API connection in GHL, no coding required.
