# packetstream review: what $0.10/GB actually pays, what $1/GB actually buys, and when to look at 9Proxy instead

"PacketStream review" is searched by two groups of people who want opposite things. One group has a spare desktop and wants to know whether the $0.10-per-GB rate is worth leaving an app running. The other group has a scraping job and wants to know whether a $1-per-GB residential pool with a $50 entry ticket is a smarter buy than the providers charging $3.

PacketStream serves both, which is exactly why the reviews you'll find read like they're describing two different companies. Let's separate them.

## What PacketStream actually is

PacketStream is a peer-to-peer residential proxy network. Users install a desktop client, agree to route third-party traffic through their home connection, and get paid for the bandwidth that gets used. Businesses buy access to that traffic and route their scraping, price monitoring, ad verification, or market research requests through those same home connections.

The company has been operating since around 2018 and is headquartered in Los Angeles. Its network is claimed at roughly 7 million IPs across 190 countries, which is small next to Bright Data's advertised 72 million or Oxylabs' 100 million. That's not a marketing failure so much as a structural ceiling: a P2P network can only grow as fast as it can convince real people to install the client.

The model matters for both sides of the marketplace. Because every exit node is a volunteer machine, you get IPs that look genuinely residential to detection systems. You also inherit the behaviour of those machines, including the ones running other software that pings suspicious endpoints.

## The buyer side: $1/GB, a $50 floor, and country-level targeting only

PacketStream's pricing is refreshingly blunt. Their own FAQ states it plainly: $1.00 per GB, metered, $50 minimum purchase, no subscription. Wholesale rates start at $1.00/GB with a $500 minimum.

There is no monthly commitment and no plan tiers to parse. You deposit $50, you get 50 GB, and it deducts as you go. For comparison, the same reviews that cover PacketStream put IPRoyal around $7/GB and Bright Data around $8.40/GB on the entry tiers. On raw price per gigabyte, PacketStream is hard to beat.

What that price buys has limits worth knowing before you deposit.

- **Country targeting only.** You can pick from roughly 190 countries. You cannot pick a city, which matters for retail price checks, local SERP results, and ad verification where the whole point is seeing what a specific metro sees.
- **Residential only.** No datacenter IPs at all, so there's no cheap fast lane for the easy parts of a job. No selectable mobile pool either, even though mobile devices are part of the network.
- **Protocol support is contested.** Some reviews say HTTP and HTTPS only, with no SOCKS5. Others list SOCKS5 as supported. If your stack depends on SOCKS5, verify it on your own account before you commit $50.
- **Slow peers cap throughput.** A single volunteer machine can't sustain heavy transfer. PacketStream rotates you off slow peers automatically, but for large file pulls you'll feel the ceiling.
- **No self-serve trial.** A free trial exists only by contacting sales, which is a poor fit if you just want to burn a few gigabytes on a test.

One independent test of 50 GB over nine days is worth reading in full, because it splits the results by workload rather than averaging them into a meaningless score:

| Workload | Result |
| --- | --- |
| Google SERP scraping (10,000 queries) | 84% returned full HTML; 1,360 CAPTCHAs; 240 errors |
| Retail price scraping (5,000 pages) | 96.4% clean 200 responses |
| Reddit account creation (50 attempts) | 38 alive after 24 hours |
| X account creation (50 attempts) | 22 succeeded |
| Pinterest account creation (50 attempts) | 45 succeeded |
| 50 sticky sessions held 30 minutes | Median session life 14 minutes; 28% survived the full window |

The pattern there is consistent with P2P by design. Short bursts through rotating peers work. Long sticky sessions fall apart, because the peer on the other end goes offline or gets rotated out. If your task needs a stable IP for an hour, this is the wrong tool.

## The earner side: $0.10/GB, a $5 payout, and the arithmetic

For people sharing bandwidth, the numbers are published, and they're small.

PacketStream pays $0.10 per GB of customer traffic routed through your connection, before cashout fees. Minimum cashout is $5, paid in USD via PayPal, processed within a week, with a 3% cashout fee deducted. Sharing only happens while the desktop app runs.

Do the division. At $0.10/GB, reaching the $5 payout threshold requires 50 GB of your bandwidth to actually be sold. Earning $50 requires 500 GB. That's not 500 GB of your own browsing; it's 500 GB of third-party traffic that a PacketStream customer decided to route through your specific IP.

Community trackers that log these programs put typical earnings at $0 to $4 per device per month, varying mostly by where your IP sits. A competitor's comparison page estimates $2 to $8 per month for a single always-on residential desktop, with heavier setups in supply-scarce regions reaching $20 to $40. Those are estimates, not PacketStream promises, and the company doesn't publish earnings guarantees.

User reports on Trustpilot line up with the low end. One reviewer described running the client continuously for a week and earning $0.009. Another said it took almost a year of 24/7 operation to reach $5.00. Those sit alongside positive reviews from people who got their $5 to $7 payouts within a few days of requesting them.

Both things are true at once. The payouts that get requested do get processed. The amounts are just very small, and how fast you get there depends almost entirely on demand for your location.

## Where the review picture starts to crack

Trustpilot rates PacketStream "Average" at 3.5 out of 5. The reviews are split along predictable lines: people who got paid and found the process simple, and people who hit walls.

The recurring complaints are specific enough to be useful:

- **Payout geography.** PayPal availability varies by country, and at least one reviewer in Egypt reported being allowed to join, accumulate a balance, and then get pushed to sort out a blocked PayPal transfer themselves. If PayPal is awkward where you live, treat the $5 threshold as a question mark, not a given.
- **Account suspensions.** One reviewer described running nine machines at nine locations and having the dashboard go blank after four days. Multi-device setups appear to attract scrutiny.
- **Antivirus flags.** TechRadar's review notes that Microsoft Defender blocked the installer, flagging it as software that "displays deceptive product messages." TechRadar's own read is that the flag comes from the app's behaviour of routing third-party traffic through your machine, not from anything malicious. The explanation is plausible. You still have to click through a warning to install it.
- **Login friction.** The separate "Packet Stream Dashboard" browser extension sits at 2.29/5 across 82 ratings, with a recent average of 1.90. The dominant complaint is CAPTCHA and Cloudflare verification failing at sign-in. Worth separating from the desktop client, which is what actually does the work.
- **Dashboard visibility.** A 2026 review notes the usage graph only shows the last 14 days with no way to change the range, filter by country, or break usage down by session. If you need to audit spend beyond two weeks, you can't.

None of that makes PacketStream a scam. It does mean the product is narrower than the marketing implies: it's an inexpensive source of rotating residential IPs for short-request workloads, and a very low-yield way to earn money.

## So which side of PacketStream are you on?

This is the fork the search term hides.

**If you're here as a buyer** and your workload is rotating, short-request, country-level, and above 50 GB, PacketStream's $1/GB is genuinely competitive. The floor is the problem. You can't test it with $5, and a $50 deposit on an untested pool is a real bet.

**If you're here as an earner**, be clear about the ceiling. $0.10/GB with a $5 minimum and PayPal-only settlement is a hobby-scale return. The realistic outcome is a few dollars a month for one machine.

Most people who search this phrase and then keep searching are in the first group.

## The buyer-side alternative: 9Proxy's full plan list

[9Proxy](https://bit.ly/9-Proxy) approaches the same problem from a different direction. It's a residential network of 20M+ IPs across 90+ countries, with country, state, city, ZIP, and ISP-level targeting, HTTP(S) and SOCKS5 support, and two separate billing models instead of one.

Where PacketStream charges $1/GB and nothing else, 9Proxy splits the product in two. IP-based plans give you a fixed number of residential IPs with unlimited bandwidth per IP, and unused IPs don't expire. GB-based plans give you unlimited endpoints and meter the traffic, with 180-day validity on balances (unlimited on enterprise). On June 1, 2026, 9Proxy raised IP-based and bundle prices for the first time in its history, from $0.015 to $0.018 per IP at the top of the ladder; GB-based pricing was left untouched.

Here's the current published ladder across all three product types. Click any package to see it on 9Proxy's site.

| Type | Package | Price | Effective rate | Validity / notes | Buy |
| --- | --- | --- | --- | --- | --- |
| IP-based | 100 IPs | $24 | $0.24/IP | Unlimited bandwidth per IP; unused IPs never expire | [Buy the 100-IP package](https://bit.ly/9-Proxy) |
| IP-based | 500 IPs | $72 | $0.144/IP | Same terms | [Buy 500 IPs](https://bit.ly/9-Proxy) |
| IP-based | 1,000 IPs + 500 bonus | $126 | $0.084/IP | Same terms | [Buy the 1,500-IP package](https://bit.ly/9-Proxy) |
| IP-based | 100,000 IPs | $2,300 | $0.023/IP | Same terms; reseller-scale | [Buy 100,000 IPs](https://bit.ly/9-Proxy) |
| IP-based | 500,000 IPs | $8,625 | ≈$0.017/IP | Same terms; lowest rate in the ladder | [Buy 500,000 IPs](https://bit.ly/9-Proxy) |
| GB-based | 5 GB | $15 | $3.00/GB | 180 days | [Buy the 5 GB starter pack](https://bit.ly/9-Proxy) |
| GB-based | 50 GB + 5 GB bonus | $105 | $2.10/GB | 180 days | [Buy 55 GB](https://bit.ly/9-Proxy) |
| GB-based | 100 GB | $150 | $1.50/GB | 180 days | [Buy 100 GB](https://bit.ly/9-Proxy) |
| GB-based | 200 GB | $200 | $1.00/GB | 180 days | [Buy 200 GB](https://bit.ly/9-Proxy) |
| GB-based | 1,000 GB | $800 | $0.80/GB | 180 days | [Buy 1,000 GB](https://bit.ly/9-Proxy) |
| GB-based | 2,000 GB | $1,500 | $0.75/GB | 180 days | [Buy 2,000 GB](https://bit.ly/9-Proxy) |
| GB-based | 6,000 GB | $4,200 | $0.70/GB | Unlimited validity | [Buy 6,000 GB](https://bit.ly/9-Proxy) |
| GB-based | 10,000 GB | $6,800 | $0.68/GB | Unlimited validity | [Buy 10,000 GB](https://bit.ly/9-Proxy) |
| Bundle | Starter: 100 IPs + 5 GB | $30 | Bundled | Traffic valid 180 days | [Buy the Starter bundle](https://bit.ly/9-Proxy) |
| Bundle | Popular: 1,500 IPs + 50 GB | $180 | Bundled | Traffic valid 180 days | [Buy the Popular bundle](https://bit.ly/9-Proxy) |
| Bundle | Pro: 5,000 IPs + 500 GB | $720 | Bundled | Traffic valid 180 days | [Buy the Pro bundle](https://bit.ly/9-Proxy) |

Datacenter proxies are listed as coming soon, with 50,000+ IPs planned. As of now, the residential line above is what you can actually buy.

## The comparison that matters for a PacketStream buyer

Set the two side by side and the tradeoffs are concrete rather than marketing-shaped.

|  | PacketStream | 9Proxy |
| --- | --- | --- |
| Entry cost | $50 minimum, no smaller option | $15 for 5 GB, or $24 for 100 IPs |
| Billing model | GB only | IP (unlimited bandwidth) or GB, plus bundles |
| Marginal price at volume | $1.00/GB flat | $0.68/GB at 10,000 GB; $0.017–0.023/IP at scale |
| Targeting | Country only | Country, state, city, ZIP, ISP |
| Protocols | HTTP/HTTPS (SOCKS5 disputed) | HTTP(S) and SOCKS5 |
| Pool size | ~7M IPs, 190 countries | 20M+ IPs, 90+ countries |
| Balance expiry | Not applicable (metered credits) | 180 days on GB; IPs don't expire |
| Payment methods | Card, PayPal, Google Pay, Cash App | Card, crypto (USDT, BTC, ETH, LTC, DOGE), bank cards, Alipay, Apple Pay, Google Pay |

The honest summary: PacketStream goes wider on country count and charges a flat $1/GB with no expiry games. 9Proxy goes deeper on targeting, supports SOCKS5 without ambiguity, starts at a fraction of the entry cost, and its IP-based tier removes bandwidth from the budget equation entirely.

Where PacketStream is arguably better: if you need coverage in a niche country outside 9Proxy's 90+ and the workload is light, the $50 deposit may still be the cheaper path to that specific geography. And volume pricing aside, a flat $1/GB is easy to reason about.

Independent testing on the 9Proxy side, for what it's worth, reports 293 successful passes out of 300 requests against a Cloudflare-protected e-commerce target, 5 CAPTCHAs, 2 hard blocks, and 0.63-second average response time. A second reviewer logged roughly 99.5% success at about 0.6 seconds. Published benchmarks are always a snapshot of somebody else's targets, so treat them as a starting expectation rather than a guarantee.

Two practical caveats before you buy. 9Proxy doesn't offer a self-serve free trial on the site; limited test access has been handed out through its Black Hat World thread, and availability varies. And the Trustpilot complaints that do exist cluster around refund policy rather than proxy performance, so pick your package size deliberately. Payment methods sometimes carry an extra 5% discount or 5% product bonus, which is worth checking at checkout. A limited-time 40% partner code for the 50+5 GB plan has also circulated through a third-party review site; partner codes like that expire, so test it rather than assuming it works.

👉 [Check the current 9Proxy plan prices and any live discounts here](https://bit.ly/9-Proxy)

## If you were here for the earning side, read this first

If your reason for reading a PacketStream review was "I want money for my spare bandwidth," 9Proxy is not a replacement. It doesn't buy your traffic. It sells residential proxies, and it has no Packeter-equivalent program.

What it does have is a partner route: a lifetime affiliate program with commissions up to 15%, instant payouts in crypto, and a 5% discount for the people you refer. That's a referral commission, not a bandwidth payout, and the effort involved is completely different. Selling bandwidth is passive and pays pennies. Referring customers is active and pays a percentage of what they spend.

If passive pennies are what you want, four or five other bandwidth-sharing programs exist side by side and many people just run them concurrently. If you'd rather earn on commission, the affiliate side of a proxy provider is a legitimate path, and it's the one 9Proxy actually offers.

## Verdict

PacketStream is a real service with a genuinely cheap buy side and an honestly tiny earn side, and most of the negative reviews are people who picked the wrong one of those two. Buy 50 GB or more for rotating, country-level scraping and it does the job at a price the enterprise providers can't touch. Install the client hoping for beer money and you'll be writing your own disappointed Trustpilot review in a few months.

If the piece that doesn't fit is the $50 floor, the country-only targeting, or the sticky-session drop-off, [9Proxy](https://bit.ly/9-Proxy) addresses all three directly, and its 5 GB pack costs less than a third of PacketStream's minimum deposit.

## FAQ

**Is PacketStream a scam?**
No. It pays out, and the $5 minimum with a 3% cashout fee is stated in its own FAQ. The complaints that read like scam reports are almost always about payout-country restrictions, account suspensions on multi-device setups, or earnings that took months to accumulate. Those are real problems, but they're different from theft.

**How long does it take to reach PacketStream's $5 payout?**
It depends entirely on how much third-party traffic your IP sells. At $0.10/GB you need 50 GB sold. A single always-on residential desktop typically lands somewhere between a few weeks and several months; user reports range from a few days to nearly a year. More devices in high-demand locations move the needle more than more hours.

**Does PacketStream work on phones?**
Not for earning. The client is desktop-only, with builds for Windows, macOS, and Linux. The Chrome extension is a dashboard, not an earner.

**Can I target a city on PacketStream?**
No. Country selection only. 9Proxy supports country, state, city, ZIP, and ISP targeting.

**Is 9Proxy an alternative to PacketStream's bandwidth-sharing program?**
Not directly. 9Proxy is a buy-side proxy provider with a referral commission program, not a bandwidth marketplace. It's an alternative for what most PacketStream researchers actually want: cheap residential IPs without a $50 deposit.

**Which is cheaper per gigabyte?**
At the entry tier, 9Proxy at $3.00/GB for 5 GB is three times PacketStream's $1.00/GB. Cross over around the 200 GB mark, where 9Proxy hits $1.00/GB, and it keeps falling from there, reaching $0.68/GB at 10,000 GB. Below roughly 150 GB, PacketStream's flat $1/GB is the cheaper rate if you can absorb the $50 minimum.
