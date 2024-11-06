# Risk
## Or . . . No, Not the Board Game (Which Is Also the Subtitle for Monopoly - tbd)

## Contents


## On Capitalism

Contrary to many opinions, capitalism does not run on greed. Greed may be a motivation to be involved, but no, capitalism runs on risk.

If you can manage your risks better than your competitors, you have a distinct advantage. And managing risks does not mean mitigating all risks to be "safe." That is called fear. Introducing fear into an org, managing by fear, and being managed by fear all happen in companies. And it makes them waste extra cycles on their fears instead of addressing the ever-changing market.

> Fear is the mind killer. - P. Atreides

### On Fire

I usually explain risk management as akin to (or part of) fire.

> Fire bad. - Frankenstein's monster

Many people seek only to mitigate risk. Fire is also what drives steam engines. Risk management can be carefully engineered to harness risk.

Like fire, risk makes people get out of its way. If you can accept that risk and others can't, then you don't need to flinch. So if there's a position that's risky but valuable, you have the advantage if you can deal with that risk.

How? Often that means being stingy with risk-taking in other places. It can also mean being strong enough to weather short-term problems.

But what about steam engines? Those would be well-crafted orgs and algos that can repeat their risk strategies successfully.

### Why Talk Capitalism?

Where do you work? Even if it's a non-profit, does it have an accountant? Does it compete in the marketplace? That's why.

Aside: I, personally, am an anti-capitalist, and risk management applies to non-capitalist systems, too, though they may not be so driven by profit and risk.

## Software Testing

Software testing is often seen as primarily risk mitigation. This casts us testers as even more of a [Druckerian cost center](https://www.investopedia.com/terms/c/cost-center.asp) than we are otherwise (I keep finding ways to be a profit center and being shut down by CXOs!).

### Shipping Less Often Because of Risk Just Adds More Risk

A lovely test-related example of risk thinking gone wrong is the periodic release. Yes, we still have to do those with mobile (because of app store rules about dynamic coding/updates), but for most other things, we could do continuous deployment.

The risk of something being a problem in a release is not just the sum of the risks of each commit, but also at least multiplied by each other commit in the release. The more changes, the more likely they interfere with one another in some way not tested for at first. So a two-week release cycle with lots of commits stacked up presents considerable risk, thus often demands a long test period. Which makes the release cycle longer. Which means more risk. Yuck!

But risk is good, right, Drew? Well . . . unless the surprise release of some flood of goodness from that kind of release cycle makes enough business sense to overwhelm the risk . . . no.

Instead, we can do continuous deployment, where any code change is tested as completely as it needs to be immediately before code review, and assuming someone says "ok," it ships. That's a way to minimize the risk of any one deploy. When it's just one commit (tested with the current prod version of everything else, as needed), the multiplying effect doesn't really happen.

> Stupid claim needing citation. Do not trust until citation given!
>Instead of risk being n * n, it's (1 + 1) * n (risk of the change plus risk of interaction with status quo times the number of changes).


### Larger Teams == More Predictable

In large, established companies, large, predicably scheduled teams are the norm.

One way to get ahead is by using a much smaller (.1x? .01x?) team to design and code up the same solution. This works. This is, over long time-frames, faster. But it's less predictable. It's higher risk.




## Software Security

Often security is seen as mitigating risks to the status quo. Not often enough is it what allows us to take more risks because they're made safe enough (like encryption in the face of the [crypto wars](https://en.wikipedia.org/wiki/Crypto_Wars)).

also, often security is treated as a solved problem by the rest of the org because some security owner is running scanners and playing whack-a-mole - doesn't seem right


## How Can We Change?

When asked to mitigate risks we can ask for assessments of how risk is being used. If it's not being used, feel free to make suggestions.
