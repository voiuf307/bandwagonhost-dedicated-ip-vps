# dedicated IP VPS annual: Which BandwagonHost Plans Actually Include a Dedicated IPv4, Yearly Pricing Compared, and How to Pick the Right Plan Without Overpaying

If you've ever run a mail server, self-hosted a site with proper DNS records, or needed a stable IP for a VPN endpoint, you already know the pain of shared or rotating IPs. One bad neighbor and your emails land in spam folders. That's usually the moment people start searching for a dedicated IP VPS on an annual plan — you get a static IPv4 that only your server uses, and you lock in a predictable yearly price instead of juggling monthly invoices.

The complication is that "VPS with dedicated IP" isn't a standardized product. Some providers charge extra for the IP, some bundle a shared address and call it dedicated, and prices for otherwise similar specs can differ by 10x depending on the network behind them. BandwagonHost (often shortened to BWH or, in Chinese communities, 搬瓦工) is one of the longest-running budget VPS providers in this space, and one thing it does consistently: **every VPS plan includes 1 dedicated IPv4 address and a routed /64 IPv6 subnet as standard** — it's printed on every plan listing, not an add-on you have to hunt for.

This guide walks through what you actually get, the full current plan lineup with annual pricing, where the real differences between plans are (spoiler: it's mostly the network, not the CPU), and which plan makes sense for which use case.

**What "dedicated IP" means on BandwagonHost — and why it matters**

Every BandwagonHost KVM plan ships with:

- **1 dedicated IPv4 address** — assigned to your VPS alone, not shared with other customers
- **1 routed IPv6 /64 subnet** — an absurdly large block by comparison (2^64 addresses)
- Full root access, instant rDNS (PTR) record updates from the control panel, and support for tun/tap, so VPN and proxy setups work out of the box

The rDNS detail is worth pausing on. If you're buying a dedicated IP VPS specifically to send email, a matching PTR record is non-negotiable — most receiving mail servers check it. On many cheap hosts you have to open a ticket and wait for someone in support to set PTR records manually. On BandwagonHost you update rDNS yourself from the KiwiVM panel in seconds, which removes one of the usual bottlenecks of running your own mail infrastructure.

One caveat from the provider's own terms: if an assigned IP gets blacklisted, the datacenter migration feature can't be used until it's resolved. In practice, BandwagonHost says it tests each IP before assigning it to a VPS to make sure new machines start with a clean address, but "clean at assignment" is not a guarantee forever — what you do with the IP afterwards is on you.

**The platform itself: KVM, KiwiVM, and self-managed everything**

All plans run on KVM virtualization with the in-house KiwiVM control panel. You get the standard self-managed toolbox: start/stop, OS reload, an emergency console (useful when you lock yourself out of SSH at 2 a.m.), snapshots, usage statistics, an API, and free migration between datacenters on eligible plans.

OS options cover AlmaLinux, RockyLinux, CentOS, CentOS Stream, Debian, Ubuntu, and Fedora, plus a library of bootable ISOs you can mount manually if you want something else. There are no managed services here — this is strictly self-managed hosting, which is precisely why the pricing stays where it is. If you need someone else to patch your server, this is the wrong product category entirely.

Uptime on standard KVM plans is listed at a **99.95% guarantee** with a **30-day money-back guarantee** on top, so trying one out for a month is a fairly low-commitment experiment.

**The full plan lineup, with annual pricing**

BandwagonHost's catalog splits into three families: the general-purpose KVM Promo line (multiple datacenter locations), the SPECIAL CN2 GIA line (fixed premium locations in Asia), and the E-Commerce SLA line (Los Angeles, NVMe, contractual uptime). Here's the current lineup as shown on the official order pages.

**KVM Promo line — multi-location, most flexible**

| Plan | SSD (RAID-10) | RAM | CPU | Transfer | Port | Annual Price | Other Cycles |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 20G KVM PROMO | 20 GB | 1 GB | 2x Intel Xeon | 1 TB/mo | 1 Gbps | **$49.99/yr** | Annual only |
| 40G KVM PROMO | 40 GB | 2 GB | 3x Intel Xeon | 2 TB/mo | 1 Gbps | **$99.99/yr** | $52.99 / 6 mo |
| 80G KVM PROMO | 80 GB | 4 GB | 4x Intel Xeon | 3 TB/mo | 1 Gbps | **$199.99/yr** | $19.99/mo |
| 160G KVM PROMO | 160 GB | 8 GB | 5x Intel Xeon | 4 TB/mo | 1 Gbps | **$399.99/yr** | $39.99/mo |
| 320G KVM PROMO | 320 GB | 16 GB | 6x Intel Xeon | 5 TB/mo | 1 Gbps | **$799.99/yr** | $79.99/mo |
| 480G KVM PROMO | 480 GB | 24 GB | 7x Intel Xeon | 6 TB/mo | 1 Gbps | **$1,199.99/yr** | $119.99/mo |

All six include the dedicated IPv4, /64 IPv6, free backups, free snapshots, free migration between datacenters, and the 99.95% uptime guarantee. If you just want to compare the annual options side by side, the lineup starts at the 20G plan and scales up in fairly even steps.

**E-Commerce SLA line — Los Angeles, NVMe, 99.99% contractual uptime**

This is the tier built for anything revenue-adjacent. You get AMD EPYC dedicated cores, local NVMe RAID-10 storage, ECC RAM, a Tier III facility with SOC 1/SOC 2/ISO 27001/PCI DSS certifications, and a **contractual 99.99% SLA** with service credits. Networking is the other big difference: 2.5–5 Gbps ports, CN2 GIA/CTGNet routing to China Telecom, premium China Unicom and China Mobile (CMIN2) routes, and direct peering with Apple, Google, Facebook, and Bytedance. A free IP change is included once every two weeks — quietly useful if you ever need to rotate your dedicated IPv4.

| Plan | SSD | RAM | CPU (dedicated) | Transfer | Port | Annual Price | Other Cycles |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 20G E-Commerce SLA | 20 GB NVMe | 1 GB ECC | 2x AMD | 1 TB/mo | 2.5 Gbps | **$239.99/yr** | $65.89 / 3 mo |
| 40G E-Commerce SLA | 40 GB NVMe | 2 GB ECC | 3x AMD | 2 TB/mo | 2.5 Gbps | **$399.99/yr** | $116.99 / 3 mo, $219.99 / 6 mo |
| 80G E-Commerce SLA | 80 GB NVMe | 4 GB ECC | 4x AMD | 3 TB/mo | 2.5 Gbps | **$699.99/yr** | $69.99/mo |
| 160G E-Commerce SLA | 160 GB NVMe | 8 GB ECC | 6x AMD | 5 TB/mo | 5 Gbps | **$1,099.99/yr** | $109.99/mo |

**SPECIAL CN2 GIA line — fixed premium locations in Asia**

These plans live in specific Equinix datacenters — Singapore (SG1), Osaka, Tokyo (TY8), and Hong Kong (HK2) — with direct routing via China Telecom CN2 GIA, China Unicom, and China Mobile. Prices scale steeply with capacity, and Hong Kong/Tokyo carry a premium over Singapore/Osaka.

| Tier | Specs (all locations) | Singapore Annual | Osaka Annual | Tokyo Annual | Hong Kong Annual |
| --- | --- | --- | --- | --- | --- |
| 40G | 2 GB RAM, 2 cores, 500 GB/mo | $499.99 | $499.99 | $899.99 | $899.99 |
| 80G | 4 GB RAM, 4 cores, 1 TB/mo | $869.99 | $869.99 | $1,559.99 | $1,559.99 |
| 160G | 8 GB RAM, 6 cores, 2 TB/mo | $1,665.99 | $1,665.99 | $2,999.99 | $2,999.99 |
| 320G | 16 GB RAM, 8 cores, 4 TB/mo | $3,199.00 | $3,199.00 | $5,899.99 | $5,899.99 |
| 640G | 32 GB RAM, 10 cores, 6 TB/mo | $5,549.99 | $5,549.99 | $9,989.99 | $9,989.99 |
| 1280G | 64 GB RAM, 12 cores, 8 TB/mo | $10,559.99 | $10,559.99 | $18,989.99 | $18,989.99 |

Monthly and quarterly billing are available across this line too (e.g., the 40G Singapore runs $49.99/month or $139.99/quarter), but the annual rate is where the per-month math improves most.

For most readers, the practical decision is between the first table and the third — and honestly, between the 20G, 40G, and 80G plans. If you want to check current stock across locations, the promo plans periodically sell out at popular datacenters.

👉 [View all current BandwagonHost annual plans and locations](https://bit.ly/BandwagonHost)

**Annual billing: is it actually worth it?**

Mostly, yes — with one exception worth knowing about. On the 40G plan, paying $99.99/year works out to about $8.33/month versus $52.99 on the six-month cycle. The 80G is $16.67/month annually against $19.99 monthly. The pattern holds up and down the catalog: annual is the cheapest per-month rate, quarterly sits in the middle, and monthly carries the largest premium.

The exception is the 20G plan, which is **annual-only at $49.99** — there's no monthly option to compare against. That's a feature rather than a bug at this price point; it exists as a loss-leader-style deal, and annual-only billing is part of how it stays that way.

The trade-off of annual billing anywhere is commitment. BandwagonHost does not bill you automatically mid-term, but renewals do generate invoices that get paid from your account balance if funds exist — so keep an eye on renewal notices if you don't want a surprise charge from a pre-funded balance. And if a plan turns out to be the wrong fit, the 30-day refund window gives you a clean exit.

**Picking a location: the part people get wrong**

Here's the thing that separates BandwagonHost's lineup from generic "cheap VPS" listings: identical specs can perform very differently depending on the network route. The KVM Promo plans can be deployed in a long list of locations — Vancouver, Fremont, Los Angeles, New York, Amsterdam, Dubai, Osaka, Tokyo, Hong Kong, and more — and can be migrated between them later from the control panel without data loss.

What that flexibility means in practice:

- **General-purpose hosting for Western audiences**: Los Angeles, Fremont, New York, or Amsterdam on a KVM Promo plan. Cheap, capable, no reason to overthink it.
- **China or Asia-facing traffic**: the network matters enormously. CN2 GIA routing (China Telecom's premium transit) avoids the congested public peering that makes budget US-hosted VPSes painful from mainland China during evening hours. The provider itself notes CN2 GIA IP transit can cost as much as $120 per megabit wholesale, which explains why the SPECIAL plans cost 10x the basic line.
- **E-commerce or anything with an SLA requirement**: the LA E-Commerce SLA line, full stop. The 99.99% contractual commitment with service credits is the whole point of the tier.

The CN2 GIA-E E-Commerce plans also support free migration between a large set of datacenters (the LA DC6/DC9 facilities plus several others), so you can start on one route and move if your traffic patterns change.

**Who should buy which plan**

A few grounded recommendations based on the actual pricing above:

- **Personal projects, small sites, VPN endpoint, testing**: the 20G KVM PROMO at $49.99/year. 1 GB RAM is tight but workable for a static site, a small VPS workload, or a WireGuard endpoint. At this price, nothing else with a dedicated IPv4 and 1 TB of transfer really competes.
- **A small production site or app server**: the 40G ($99.99/yr) or 80G ($199.99/yr). The jump to 2 GB or 4 GB RAM matters more than it looks once you add a database and a web server to the same box.
- **Mail server with modest volume**: 40G or 80G, deployed somewhere with clean IP reputation, rDNS set immediately from KiwiVM. Budget headroom for the fact that deliverability is an ongoing project, not a one-time setup.
- **Anything generating revenue, especially China-facing**: E-Commerce SLA. The 40G at $399.99/year is the entry point, and the NVMe + dedicated cores + 99.99% SLA combination justifies the jump from the Promo line.
- **Hong Kong/Tokyo CN2 GIA**: only if you have a specific, verified need for those routes — the annual prices start at $899.99 and climb fast.

If you're unsure which tier fits, the 30-day refund window makes it cheap to start small on the Promo line and upgrade later — migrations between plans and locations are handled from the panel.

👉 [Order a dedicated IP VPS with annual billing](https://bit.ly/BandwagonHost)

**How ordering works**

The process is short. You pick a plan, choose a datacenter location (on multi-location plans), pick your billing cycle — annual, in this case — and pay. Account setup and VPS provisioning are instant and automated; your credentials arrive by email, and the server is manageable from KiwiVM immediately. From there, the usual first steps apply: log in, update the OS, set your rDNS record if you're running mail, and take a snapshot before making configuration changes so you have a rollback point.

**Common questions**

**Is the IPv4 truly dedicated, or shared?** Dedicated. Every plan listing explicitly states "IPv4: 1 dedicated address" — it's bound to your VPS, not shared among customers.

**Can I get more than one IP?** Additional IPv4 addresses can be arranged, subject to justification requirements that are standard across the industry. For most use cases — including mail — one clean dedicated IP with proper rDNS is sufficient, and the free IP change on SLA plans covers the rotate-if-needed case.

**Do the promo plans stay in stock?** Not always at every location. Popular datacenters on the cheaper annual plans sell out periodically. If a specific location matters to you, check availability before planning around it, and remember you can migrate between locations later on multi-location plans.

**Is there a cheaper catch-and-release option?** The provider occasionally runs limited-edition plans (community forums track them closely), but stock is unpredictable and they're not something you can reliably plan an annual purchase around. The standard $49.99/year 20G plan is always the safer baseline.

**Bottom line**

For a dedicated IP VPS on an annual budget, the decision tree is simpler than the plan list makes it look. Under $100/year: the KVM Promo line, where every plan includes the dedicated IPv4, /64 IPv6, and rDNS control that justify the search in the first place — the 20G at $49.99/year is the anchor deal. Anything touching real revenue or China traffic: the E-Commerce SLA line in Los Angeles, starting at $239.99/year with a contractual 99.99% uptime commitment. The Hong Kong and Tokyo SPECIAL plans are excellent at what they do, but they're solving a specific network problem at a specific price, and most buyers searching for an annual dedicated IP VPS don't need to go there.
