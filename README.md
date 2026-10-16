# buying a vps: how to size the specs, pick a location, and decide if RackNerd's $1.99/mo budget KVM plans are worth it

Buying a VPS comes down to five decisions: what you'll run on it, how much RAM that takes, where the server physically sits, which billing term you commit to, and who handles the admin work. Sort those out first and provider marketing stops mattering much. This guide walks through each one, using RackNerd — the budget pick in most current comparisons, with plans tracked at $1.99–19.99/mo across five US datacenter locations — as the concrete example wherever a specific plan and price helps.

> **Quick take:** if you want the cheapest honest way to get a real KVM server with full root access — for learning Linux, running a VPN, or hosting a small project — RackNerd is the strongest fit, and its entry specials work out to roughly $1.99/mo on annual prepay. 👉 [Check RackNerd's current plans and prices](https://bit.ly/my-rn). If most of your users are outside the US, or you'd rather never open a terminal, skip to the alternatives section below.

## What buying a VPS actually gets you

You get an isolated slice of a physical server: your own operating system, a fixed allocation of CPU, RAM and disk that the hypervisor enforces, root access, and your own IP address. Unlike shared hosting, nothing another customer does can crash your site, slow it down, or read your data.

Where it sits in the market:

| Hosting type | Control | Typical price | Best for |
| --- | --- | --- | --- |
| Shared hosting | None | $3–10/mo | One small website |
| VPS | Full root | $5–50/mo | Most projects |
| Dedicated server | Full | $50–200+/mo | High traffic |
| Big cloud (AWS/GCP) | Full | Variable, metered | Enterprise scale |

A modern VPS with proper virtualization and SSD or NVMe storage outperforms a dedicated server from several years ago at a small fraction of the price, which is why the old rule that "production belongs on bare metal" has largely aged out.

## Step one: size the plan to the workload

RAM is the spec that decides whether a VPS feels fine or falls over. CPU matters for encoding and AI inference; storage type matters for databases. For everything else, this table covers most buying decisions:

| Use case | Minimum RAM | Comfortable |
| --- | --- | --- |
| Static website | 512MB | 1GB |
| WordPress | 1GB | 2GB |
| Small API or app | 1GB | 2GB |
| Docker (2–3 containers) | 2GB | 4GB |
| n8n / automation | 2GB | 4GB |
| Game server | 4GB | 8GB+ |
| Database server | 4GB | 8GB+ |
| AI/ML inference | 8GB+ | 16GB+ |

When in doubt, buy more RAM rather than more CPU. The cost of starting small is low because upgrades are routine on most VPS platforms; the cost of undersizing is a server that swaps itself to death during your first traffic spike.

Two storage notes that people get wrong in opposite directions. Running a database or a busy build server? NVMe is 3–5x faster than SATA SSD and worth seeking out. Setting up a VPN, a test box, or a small site? You will not notice the difference, so don't pay extra for it.

## RackNerd's plans and prices, in full

RackNerd's standard lineup is five fixed KVM plans. Every plan runs on KVM virtualization — true hardware virtualization with your own kernel, so Docker, WireGuard and custom sysctl tweaks all behave — and includes full root access, a dedicated IPv4 address, a 1Gbps port, and unmanaged service with your choice of Linux distribution at order time.

| Plan | vCPU / RAM | Storage | Transfer / month | Monthly price | Order |
| --- | --- | --- | --- | --- | --- |
| KVM 768MB | 1 / 768MB | 10GB SSD | 750GB | $8.99 | [ Order KVM 768MB](https://bit.ly/my-rn) |
| KVM 1.5GB | 1 / 1.5GB | 20GB SSD | 2TB | $13.99 | [ Order KVM 1.5GB](https://bit.ly/my-rn) |
| KVM 2.5GB | 2 / 2.5GB | 50GB SSD | 3TB | $20.99 | [ Order KVM 2.5GB](https://bit.ly/my-rn) |
| KVM 4GB | 3 / 4GB | 80GB SSD | 4TB | $34.99 | [ Order KVM 4GB](https://bit.ly/my-rn) |
| KVM 8GB | 4 / 8GB | 160GB SSD | 5TB | $59.99 | [ Order KVM 8GB](https://bit.ly/my-rn) |

Mapping the sizing table onto these plans: the KVM 1.5GB handles WordPress and small APIs comfortably. Docker with two or three containers, or an n8n instance, wants the KVM 2.5GB — which is also the first plan with 50GB of storage, clearing the roughly 40GB floor most buying guides suggest for a working server. Game servers and databases should start at KVM 4GB or above.

One honest caveat: the two smallest plans ship 10GB and 20GB of disk. That's plenty for a VPN endpoint, a proxy, or a toy project, and genuinely tight for a full web stack plus logs. Check your disk appetite before grabbing the cheapest option.

## Decoding the $1.99 price tag

The $1.99–19.99/mo range you'll see in third-party comparisons and the $8.99 starting price on the standard monthly lineup are both accurate — the gap is billing term. The sub-$5 effective prices come from RackNerd's rotating specials: real, full-root KVM plans billed annually or on multi-year terms, discounted 30–50% against month-to-month pricing. They rotate through the year rather than sitting permanently on the main pricing page.

To make the math concrete: keeping a KVM 1.5GB plan on month-to-month billing runs $13.99/mo, or about $168 over a year. A comparable special at roughly $2/mo effective costs around $24–30 for the same year. That's the entire appeal of prepaying with this provider.

There's a second detail that matters more than it looks: RackNerd's specials renew at the price you signed up at. Budget hosts in general are famous for cheap year one and a jump at renewal; this one doesn't play that game, so the multi-year math holds up in year two.

A workable strategy:

1. Test on the shortest term you can stand. Support response times and network quality are invisible on a pricing page.
2. Once the provider has earned it, prepay annually or multi-year and collect the discount.
3. Set a calendar reminder a week before renewal regardless.

Before prepaying several years, confirm two things at checkout: the exact money-back window (RackNerd has a refund policy; verify the current terms) and what happens when you exceed your monthly transfer allowance. 👉 [Compare RackNerd's standard plans against the current specials in one place](https://bit.ly/my-rn).

## Pick the datacenter location your users need

Choose the location closest to your users, and the placement should be based on their geography rather than yours. A cheap VPS in the wrong region adds 50–200ms of latency to every request, and that makes even a well-specced server feel sluggish.

RackNerd operates five US datacenter locations, including Los Angeles on the west coast and New York on the east, so US audiences are covered from either side — pick the coast matching most of your traffic. If your audience sits mostly in Europe or Asia-Pacific, RackNerd's US-only footprint is a real limitation. Providers with 15+ global locations such as Vultr or DigitalOcean, or European value specialists like Hetzner, will serve those users better, and paying their slightly higher entry price for it is reasonable.

One more five-minute step before ordering anywhere: run the provider's network test file from your own connection. Speed test results beat guesses.

## Unmanaged is the default — plan for it

RackNerd VPS plans are unmanaged: you handle updates, security patches, configuration and backups, while support covers the hardware and network underneath. Managed plans elsewhere bundle that work in and charge a substantial premium for it.

Unmanaged is less intimidating than it sounds. Install Docker, learn a handful of commands, and most of the daily work takes care of itself. Do these five things in your first half hour on any new server:

1. SSH in, add a non-root user, and set up SSH key authentication
2. Disable password-based root login
3. Run system updates
4. Configure a basic firewall — allow SSH and your web ports, nothing else
5. Set up off-host backups; rsync to cheap object storage costs a few dollars a month and has rescued more projects than any uptime SLA

If that list reads like a foreign language, either budget a weekend for learning or pick a managed provider instead. Both beat discovering the difference during your first outage.

## How the purchase works, start to finish

The buying flow is short and needs no sales call:

1. Pick a plan and a billing term — monthly on the standard lineup, annual or multi-year on specials
2. Choose your datacenter location and operating system; Ubuntu, Debian, AlmaLinux and the other common distros are selectable at order time
3. Pay — PayPal, major cards, and cryptocurrency are accepted
4. Watch for the welcome email containing your IP address and root credentials
5. SSH in and run the five-step checklist above

Provisioning is usually quick after payment. Occasionally a first order gets held for a short manual review — common with brand-new accounts — and answering the verification email is typically all it takes to clear it.

## How RackNerd stacks up against the alternatives

RackNerd wins on price and gives up geographic reach. Here's the rest of the field for context:

| Provider | Entry price | Locations | Known for | Better fit when |
| --- | --- | --- | --- | --- |
| RackNerd | $1.99–19.99/mo | 5 US | Cheapest full-root KVM | Budget, learning, VPN, US users |
| Hostinger | $4.99/mo | 7 global | 4GB RAM at entry price | Beginners wanting more hand-holding |
| Hetzner | €3.79/mo | EU-focused | 2 vCPU + 4GB RAM per euro | Audience in Europe |
| Vultr | from $2.50/mo | 16 global | Hourly billing, 1-click apps | Global footprint, API-driven work |
| DigitalOcean | from $4/mo | 15+ global | Docs, community, API | Production web apps |
| Contabo | €4.99/mo | 9 global | Huge specs for the price | Storage- or RAM-heavy needs, tolerant of a slower network |

The trade-offs behave the way you'd expect. Contabo hands you more raw hardware per euro but with a slower network. DigitalOcean costs roughly 4x more for equivalent specs and buys you the best documentation in the industry. Hostinger sits in the middle with beginner-friendly packaging at $4.99/mo for 4GB of RAM and 50GB of NVMe.

## FAQ

**Is the cheapest RackNerd plan enough for learning Linux or running a VPN?**
Yes. Every plan includes full root access, and a VPN endpoint or personal test box idles well under 1GB of RAM. KVM 768MB is a legitimate starting point; step up to 1.5GB if you'll also run a small website on the same box.

**How much VPS do I need for WordPress?**
Plan for 1GB minimum, 2GB to be comfortable. RackNerd's KVM 1.5GB plan fits, leaving headroom for MySQL and a caching plugin on a small-to-medium site.

**Do I really need NVMe storage?**
For databases and I/O-heavy workloads, yes — it's 3–5x faster than SATA SSD. For VPNs, learning environments, and small sites, no; plain SSD is invisible in practice. RackNerd's standard plans are SSD-backed, which suits the use cases above fine and matters less than RAM does.

**Monthly or annual billing?**
Start monthly, or with the shortest term offered, then prepay longer once you trust the provider. Multi-year discounts of 30–50% are real money, but locking in for years before you've opened a single support ticket is a bet you'll never need to leave.

**Can I upgrade later if I outgrow the plan?**
On most VPS platforms, yes, and upgrades are often instant. On budget providers, a plan change can mean a new order and moving your data, so ask support about in-place upgrades before ordering if growth is likely. Either way, skip the 8GB "just in case" purchase — start right-sized.

## Which plan to pick, by situation

Learning Linux, running a VPN, or hosting personal projects with US-based users: RackNerd's entry and mid-tier specials offer the strongest price-to-value in the budget class, and renewal prices hold steady. 👉 [Check RackNerd's current plans and specials before ordering](https://bit.ly/my-rn).

Running a production web app where documentation and mature APIs matter: DigitalOcean or Vultr justify their higher prices.

Audience concentrated in Europe: Hetzner's €3.79 plan with 2 vCPU and 4GB RAM is difficult to match at that price point.

Zero interest in ever touching a terminal: a managed provider such as Cloudways or ScalaHosting costs more and takes the admin work off your plate.

Two checks before any VPS purchase, RackNerd included: confirm the datacenter location matches where your users actually are, and have a backup destination ready before the server goes live. Both take minutes to set up, and they prevent the two most common regrets people have a year in.
