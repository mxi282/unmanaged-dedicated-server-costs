# unmanaged dedicated server hosting: what you still have to run yourself, what the monthly bill really adds up to, and when one 56-core box in Hong Kong beats a stack of VPS

If you're searching for unmanaged dedicated server hosting, you've probably already accepted that you'll be the one installing the OS, tuning the database and getting paged at 3am. The question that actually matters is narrower: where exactly does the host's responsibility stop, and what does the bill look like once setup fees, extra IPs and traffic overage are added in?

Short answer: the provider keeps the physical layer — hardware, power, network, DDoS scrubbing, instant provisioning. Everything above the operating system is yours. And on price, the headline monthly figure rarely tells the whole story.

One option worth putting on the table early is GoMami Networks, a Hong Kong-focused provider whose Forge line is the only true bare-metal product it sells. Two plans, one CPU, one location — which makes the decision refreshingly short.

> **Quick pick:** GoMami Forge Mini — AMD EPYC 7663 (56C/112T), 128 GB RAM, 960 GB NVMe, 10 TB traffic on a 2 Gbps port, **$399/month plus a one-off $68 setup fee**. That's $4,856 for the first year. It fits workloads with a mostly mainland-China or East Asian audience that need the whole box rather than a slice of one.
> 👉 [Check the Forge Mini configuration and current price](https://bit.ly/Gomami)

## Where the line sits in unmanaged dedicated hosting

The host handles the physical machine, the data centre, power and cooling, network uplinks, and the DDoS scrubbing layer. You get root on the operating system and everything above it.

That means you choose the distribution, partition the disks, set firewall rules, install a control panel or skip it, manage users, patch the kernel, and decide how the service scales. Providers in this segment tend to be blunt about it: OVHcloud's own product copy warns readers who lack the right level of expertise to look elsewhere.

One nuance is worth stating plainly, because it trips people up: unmanaged doesn't mean the provider is hands-off. GoMami still runs fully automated setup, activates the server immediately after payment, and lets you reinstall the OS from the control panel whenever you like. What you're not buying is somebody to debug your MySQL config.

Windows licensing falls on your side of the line too. GoMami's documentation doesn't bundle it, so you either bring your own key or raise a ticket to confirm what's available before you commit.

## GoMami Forge: full plan list and specs

GoMami's homepage lists six VPS configurations plus the two Forge bare-metal plans. The VPS range runs $39–$199/month; Forge starts at $399 plus setup. Both Forge plans use the same chip.

| Plan | CPU / RAM | Storage | Traffic / Port | Price | Order |
| --- | --- | --- | --- | --- | --- |
| Ryzen 9 9950X Mini | 2 vCPU / 4 GB | 40 GB NVMe | 1,000 GB / 2 Gbps | $59/mo | [Order the Ryzen Mini](https://bit.ly/Gomami) |
| Ryzen 9 9950X Air | 4 vCPU / 8 GB | 60 GB NVMe | 2,000 GB / 2 Gbps | $99/mo | [Order the Ryzen Air](https://bit.ly/Gomami) |
| Ryzen 9 9950X Pro | 6 vCPU / 16 GB | 80 GB NVMe | 5,000 GB / 5 Gbps | $199/mo | [Order the Ryzen Pro](https://bit.ly/Gomami) |
| EPYC 7763 Mini | 2 vCPU / 4 GB | 40 GB NVMe | 1,000 GB / 1 Gbps | $39/mo | [Order the EPYC Mini](https://bit.ly/Gomami) |
| EPYC 7763 Air | 4 vCPU / 8 GB | 60 GB NVMe | 2,000 GB / 1 Gbps | $79/mo | [Order the EPYC Air](https://bit.ly/Gomami) |
| EPYC 7763 Pro | 8 vCPU / 16 GB | 80 GB NVMe | 5,000 GB / 3 Gbps | $169/mo | [Order the EPYC Pro](https://bit.ly/Gomami) |
| **HKG.Forge.Mini** | EPYC 7663, 56C/112T / 128 GB | 960 GB NVMe | 10 TB / 2 Gbps | **$399/mo + $68 setup** | [Order Forge Mini](https://bit.ly/Gomami) |
| **HKG.Forge.Air** | EPYC 7663, 56C/112T / 256 GB | 4 TB NVMe | 20 TB / 2 Gbps | **$699/mo + $68 setup** | [Order Forge Air](https://bit.ly/Gomami) |

How to read the VPS half: Mini and Air are configured identically on both platforms, so the $20 monthly premium on Ryzen buys clock speed and a wider port rather than more resources. Pro breaks that pattern. $199 on Ryzen gets 6 vCPU and a 5 Gbps port; $169 on EPYC gets 8 vCPU at 3 Gbps. The cheaper Pro plan has more cores.

GoMami's documentation also names HKG Turin (with an additional Ultra tier), JPN Pulse and SIN Pulse without publishing prices, so they can't be compared here.

Both Forge boxes sit on a TYAN B8033 platform with the whole EPYC 7663 to yourself — no vCPU slicing, no noisy neighbour sharing the memory bus.

On DDoS, the numbers need a footnote. Official docs describe best-effort protection by default with 600 Gbps advanced scrubbing available as a purchasable extra, while third-party write-ups list 600 Gbps as standard on both Forge plans. If that capacity is load-bearing for your threat model, get support to confirm it in writing.

## Forge Mini or Air? The $300 gap, itemised

The two Forge plans share the same CPU, port speed and network. Every dollar of the $300 monthly difference goes into memory, storage and traffic: 128 GB → 256 GB RAM, 960 GB → 4 TB NVMe, 10 TB → 20 TB.

Run the traffic portion through GoMami's own overage rate of $0.06/GB and the maths gets interesting. An extra 10 TB billed as overage comes to roughly $600. So if you expect to actually use 20 TB a month, Air isn't really a $300 upgrade — the traffic alone would cost more than that on the Mini, and 128 GB of extra RAM plus 3 TB of extra NVMe come along for free at that point.

Flip it around: if your workload lives inside 10 TB and 128 GB, Air is $300/month — $3,600 a year, plus the same $68 setup — for capacity you won't touch. Mini is the correct purchase.

Neither plan has a third tier. There's no Forge Pro, no higher-memory option, no second location. If you need 512 GB of RAM or a Frankfurt rack, GoMami isn't the answer, and no amount of clicking around the order page will change that.

## What the $399 actually leaves out

The advertised monthly price excludes four things: the setup fee, extra IPs, traffic overage and any promotional discount you haven't applied yet. Budget for all four.

**The setup fee.** $68, once, per server. It doesn't recur, but it also doesn't shrink under any promotional discount.

**Extra IPs.** $10 each per month, capped at four per server. For anything terminating multiple TLS services or running separate mail identities, that's up to $40/month on top.

**Traffic overage.** $0.06/GB past the included allowance, with no hard cut-off mentioned in the spec sheet. At that rate a runaway backup job gets expensive quietly rather than loudly, so watch the traffic graph in the panel.

**Promo codes.** The cart screen has a Promo Code field, and third-party write-ups circulate codes claiming a recurring percentage off across the range, setup fee excluded. GoMami's own pages don't advertise these, so treat any figure you see quoted elsewhere as unconfirmed until the order summary reflects it. Enter it before you hit Checkout, not after.

GoMami's docs note that longer billing cycles usually price better than monthly. The discount percentages aren't published, so compare the order summary across cycles rather than assuming.

Refund terms are the other soft spot. The official FAQ lists questions about trials, traffic overage handling and non-profit discounts but doesn't answer them on the page, and independent guides describe a 24-hour window with exclusions. If a refund guarantee is part of your decision, open a ticket and get it in writing before paying.

## Total cost over three years, not one month

Sticker prices mislead because the entry rate often expires after year one. Take the mid-market example tracked by CloudsPress: a Xeon E-2236 box with 32 GB RAM, 960 GB SSD and 100 TB of transfer lists at $37.33/month on a one-year term and renews at $74.66 — a 100% jump, and $2,240 over three years. The advertised price is roughly half the real run rate.

GoMami's Forge pricing doesn't carry that trap in the figures available: $399 and $699 are listed as flat monthly rates with a one-off setup fee, not introductory pricing. Assuming those rates hold, the totals look like this.

| Plan | Monthly | First year (incl. $68 setup) | Year one over 12 months |
| --- | --- | --- | --- |
| HKG.Forge.Mini | $399 | $4,856 | $404.67 |
| HKG.Forge.Air | $699 | $8,456 | $704.67 |

That's the honest comparison point against any promotional dedicated offer. A $37/month headline sounds like a tenth of the price until you see year two.

## Who this box fits, and who should stay on a VPS

Forge is the right purchase when the workload is CPU- or IO-bound in a way a shared host can't absorb, and when the audience is largely in mainland China or nearby Asia. Databases with large buffer pools, container hosts running a dozen or more instances, video transcoding, CDN origins, crawler fleets — the kind of thing where a neighbour's disk burst shows up in your own latency graphs.

The routing is the other half of the pitch. GoMami labels both Forge plans "China Mainland Optimized Pro" and routes over CN2 for China Telecom, AS9929 for China Unicom and CMIN2 for China Mobile, with a claimed mainland RTT under 50 ms. That matters if your users are in Shenzhen or Shanghai and your server is in Hong Kong; it matters much less if they're in Frankfurt.

There's a second difference worth knowing before you choose: VPS plans on GoMami throttle traffic overage to around 20 KB/s, while Forge bills overage at $0.06/GB and keeps the port running. If your monthly transfer is unpredictable — backups, media, big downloads — the metered model is the safer one, and it's a reason to move up from VPS even before CPU becomes the bottleneck.

Plenty of readers should not buy this. A blog, a small API, a game server for a dozen friends — the EPYC 7763 Mini at $39/month handles that, and Forge costs ten times as much for capacity nobody will use. If your traffic is entirely European or North American, a local provider beats a Hong Kong box on both latency and price. And if the appeal of "dedicated" is mainly the word itself, a VPS on a fast single core is the better spend.

👉 [See the EPYC 7763 VPS tier at $39/month before deciding you need bare metal](https://bit.ly/Gomami)

## How it stacks up against the bigger dedicated-server names

What separates these providers is less about spec sheets and more about the shape of the company you're buying from. GoMami is small and geographically narrow; the large incumbents are broad and slow-moving.

| Provider | Entry dedicated offer | Listed price | Shape of the offer |
| --- | --- | --- | --- |
| GoMami (HKG Forge) | EPYC 7663, 56C/112T, 128 GB, 960 GB NVMe, 10 TB | $399/mo + $68 setup | One location, two plans, China-optimised routing |
| Liquid Web | 16-core Xeon, 64 GB RAM, fully managed | From $167.50/mo | Managed, migration included, email as paid add-on |
| Mid-market example tracked by CloudsPress | Xeon E-2236, 32 GB RAM, 960 GB SSD, 100 TB traffic | $37.33/mo year one, $74.66/mo renewal | Promotional first-term pricing, 100% renewal increase, $2,240 over three years |

Liquid Web shows the other end of the market. At $167.50/month for a managed 16-core with 64 GB, you're paying for somebody else to patch the kernel. That box has fewer cores and less RAM than Forge Mini, so the comparison is really about who does the operations work — and if the answer you want is "them", the unmanaged segment is the wrong shelf.

Where GoMami lands: a 56-core, 128 GB bare-metal box with premium China routing and DDoS capacity bundled into one line item. The per-core price is unremarkable; what's harder to replicate elsewhere is routing and scrubbing arriving in the same package.

## Buying it: the screens you'll click through

Provisioning is fast and mostly automated, but there are two places where people get it wrong.

1. **Pick the location and product line.** Hong Kong holds Turin, Pulse and Forge; Japan and Singapore carry Pulse only. Landing on a Pulse plan when you meant Forge is the classic mistake.
2. **Configure.** The order summary updates live as you change the billing cycle. Longer cycles are priced better; the percentages aren't published, so read the summary.
3. **Cart.** This is where the Promo Code field lives. Verify the product and the price, then continue.
4. **Checkout.** Account details, then payment: account credit, credit card, Stripe Alipay, or crypto. Tick the terms box and submit.
5. **Deployment.** Automatic, typically minutes. You get an email with the IP and login credentials.

Forge carries instant activation and fully automated setup — nobody has to rack anything by hand — and the control panel handles OS reinstalls whenever you want to switch distributions.

## FAQ

**Is GoMami Forge managed?** No. You get root and full responsibility for the OS, software stack, security patching and application configuration. The provider covers hardware, network, power and DDoS mitigation.

**How much does the cheapest Forge server cost?** $399/month plus a one-time $68 setup fee, which comes to $4,856 in the first year. That includes 128 GB RAM, 960 GB NVMe and 10 TB of traffic on a 2 Gbps port.

**What happens if I exceed the traffic allowance?** Overage is billed at $0.06/GB, with no throttling mentioned for Forge. Included traffic is 10 TB on Mini and 20 TB on Air.

**How many IPs do I get?** Extra IPs cost $10 each per month, with a maximum of four per server.

**Is there a China-optimised network?** Yes — both plans are labelled China Mainland Optimized Pro, using CN2, AS9929 and CMIN2. GoMami states mainland RTT of under 50 ms.

**Can I install Windows?** Licensing isn't included; bring your own key or confirm options with support first.

**Can I get a refund if the routing isn't what I expected?** The official FAQ doesn't publish the terms. Independent write-ups describe a short refund window with exclusions, so confirm the current policy through a support ticket before ordering.

👉 [Start a Forge order and see the live total at checkout](https://bit.ly/Gomami)

## Picking your configuration

If your workload fits inside 10 TB of monthly traffic and 128 GB of RAM, buy Forge Mini at $399 plus the $68 setup. Air earns its extra $300 when you'd otherwise be paying overage or fighting memory pressure — at $0.06/GB, 10 TB of overage alone runs about $600, which is more than the upgrade costs.

If you're not certain you need the whole physical machine, start on the EPYC 7763 Mini at $39/month and watch CPU steal and disk latency for a month. Moving up later is a migration; overpaying from day one is just rent.

If your users aren't in China or East Asia, none of this applies, and a regional provider serves you better on both hops and dollars.

Two things to settle before you enter card details: confirm the billing cycle discount actually shows in the order summary, and get the current refund terms in writing. Then, once the box is live, run an mtr or traceroute from a mainland vantage point before migrating anything production-critical. Routing claims are easy to make and occasionally contested by users; fifteen minutes on day one is cheaper than a migration in month two.

👉 [Compare GoMami Forge and VPS plans side by side](https://bit.ly/Gomami)
