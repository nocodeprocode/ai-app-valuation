# Codebase Valuation Prompt (AI Era, Zero Revenue)

Paste everything below into an agent that has read access to the repo.

---

You are valuing this codebase as a sellable asset. It has zero revenue. Produce a price that survives contact with a buyer who has a frontier coding agent and can simply regenerate anything obvious.

## Rule zero

**Effort is not value.** Hours spent, tokens burned, commits made, and lines written are inputs the seller chose to spend. A buyer pays for the cheapest path to the same outcome, and that path is almost never "redo what the seller did." Never let build cost set the price. If your final number is mostly someone's hourly rate multiplied by hours, you have valued a timesheet, not an asset.

Related bans:
- No flattery. If it is a template with the colors changed, the first line says so.
- Do not trust the README, my description, or my effort estimate. Read the code, run the build, count what actually ships.
- Every assumption carries a number. "Reasonable market interest" is banned.
- Absence of evidence is evidence of absence. The burden of proof is on any premium.

## Part 1: The three gates

Run all three before any arithmetic. Answer each with evidence from the repo or the surrounding business.

**Gate 1: The one-sitting test.**
Write the complete spec a buyer would hand their own agent instead of paying you. Write it in full, as a paragraph, not as a summary. Then judge: does a frontier agent produce functional parity from that paragraph in one working session?

If yes, the code has no independent value. It is regenerable. Say so plainly.

**Gate 2: The demand test.**
Has anyone who is not the author used this? Count real users, real sessions, real rows written by someone else. Then name the incumbents and their prices. If the category's anchor price is $0 because free tools already do this, note it.

If nobody outside the author has used it and free substitutes exist, demand is zero. Zero demand is not a discount, it is a multiplier of zero.

**Gate 3: The taste test.**
Look at the actual interface, the copy, the naming, the information design. Does it look like default AI output: generic gradient hero, stock card grid, lorem-grade microcopy, unmodified component library defaults? Judge it against what a buyer would ship, not against an empty repo.

Generic design is not neutral. It is work the buyer must throw away and redo, and it caps the price at "boilerplate" because it signals no product judgment was applied.

**Gate outcome.** If Gate 1 says regenerable AND Gate 2 says no demand, stop. The asset is worth $0 to a few hundred dollars regardless of what it cost to build. Skip Parts 2 through 4, output the verdict, the honest paragraph, and the leverage moves. Do not run the math anyway to be nice. Running the math on a commodity is how you get a four figure number for a template.

## Part 2: Substitute cost, not replication cost

Only for assets that survived the gates.

The floor is what the buyer's cheapest alternative costs today. Compute all three and take the **lowest**:

1. **Regenerate.** Tokens to produce parity from the Gate 1 spec, at one-sitting scale, not at the seller's iteration count. State the model and current per-million pricing, or state the placeholder you used.
2. **Substitute.** Cost of the nearest existing product, open source project, or template that covers the same job. If a free one exists, this is $0.
3. **Commission.** What a competent contractor charges to build it to spec today, using agents.

Substitute cost `S` = the lowest of those three.

Do not add a seller margin. Margin is earned by demand, and demand is scored below.

## Part 3: Score, then multiply

Score each dimension. Note that two of them go negative.

**A. Non-obviousness (0 to 5).** Would a frontier model, given a good spec, reach this architecture and these solutions unaided? 5 means the repo solves problems the model does not know exist: undocumented platform behavior, reverse engineered protocols, edge cases only production reveals, domain rules absent from any public corpus. Fix commits for well-documented third party onboarding friction score 0. They are a build log, not accumulated wisdom.

**B. Clone resistance (0 to 5).** How long for a funded competitor with agents to reach parity, and what is still missing at the end? 5 means the missing pieces are structural: proprietary data, accumulated corrections, network effects, a licensing position, a certification, an exclusive integration.

**C. Execution and operability (-3 to +5).** Does it survive real use by someone other than the author? Positive for tests over the money paths, observability, idempotency, migrations, repeatable deploys, security posture. **Negative** for liabilities the buyer inherits: proprietary vendor proxies they must rip out before first run, zero tests on payment or auth paths, silent error swallowing, secrets in the repo, unowned domains.

**D. Product judgment and taste (-2 to +5).** Design quality, information architecture, copy, the specific decisions that show someone understood the user. Negative if the interface must be discarded. This dimension has grown in weight, not shrunk: when generation is cheap, taste is one of the few remaining things a model does not supply for free.

**E. Demand (0 to 5).** Evidence, not belief. Paying users, retained users, waitlist, LOIs, pilots, inbound. The author does not count as a user.

**F. Transferable assets beyond code (0 to 5).** Only what actually transfers: production data, evals, an owned domain and its SEO position, users and their content, integration approvals, store listings and review history, compliance artifacts, trademarks, published packages with install counts. Subdomains on someone else's platform transfer nothing.

**The math.**

```
Base       = S + (S × premium multiplier from A + B + D)
Demand     = E scaled 0 to 1.0
Value      = Base × Demand − Remediation
```

- Demand of 0 gives a value of 0. That is correct and intended. Nobody pays regeneration cost for something nobody wants.
- Exception: if B (clone resistance) is 4 or 5, set a Demand floor of 0.1. Genuinely hard-to-build things carry option value even before anyone wants them. Nothing else earns this exception.
- Remediation is a real dollar figure: hours to strip vendor lock-in, redesign a generic interface, and cover untested money paths, at a contractor rate. It is subtracted last and may push the total below zero. An asset can be worth less than nothing.

## Part 4: Decay and comps

- Estimate what share of scores A, B, and D a model 12 months out would produce unaided. Discount the premium portion, never the substitute cost, by that share.
- State the half-life plainly: "the defensible part is worth half as much in N months unless X happens."
- Cross-check against how these actually clear. Zero-user code assets on marketplaces sell in the hundreds to low thousands regardless of build cost. Products with revenue clear on a multiple of that revenue. If your number exceeds roughly $50k, name the specific acquirer and the specific thing they cannot generate. If you cannot name one, cut the number.

## Output

No preamble. Exactly this:

1. **One line verdict.** What this honestly is.
2. **Gate results.** Pass or fail on each of the three, with the full Gate 1 spec paragraph written out. If gates 1 and 2 both failed, the price is the gate outcome and sections 3 and 4 are one line each.
3. **Price.** Walk-away, realistic clearing range, and a ceiling that names its condition. Show the arithmetic including the remediation subtraction.
4. **What is actually being sold.** Rank components by share of value. If the code is not first, say what is. If nothing is worth anything, say that.
5. **Buyer list.** In order of fit, with the pitch each responds to. "Nobody" is a valid first entry.
6. **Leverage moves.** Three to five, each with effort and dollar impact, split into two columns: moves that raise the price, and moves that only raise the build cost. Only the first column matters. Explicitly flag any move that adds features, since more regenerable surface area is usually worth nothing.
7. **The honest paragraph.** What a skeptical buyer says to knock the price down, and whether they are right.
