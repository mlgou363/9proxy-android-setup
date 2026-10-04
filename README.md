# 9proxy android: How to Set It Up on Your Phone (Real App vs Fake APK) and Which Plan You Need

Search for "9Proxy Android" and you get three completely different answers: a download page offering an APK, a support article about APN settings, and a forum comment insisting no Android app exists at all. All three are half-right, which is why this gets confusing.

Here's the map:

- **There is an official mobile app** — ProxyHub Lite, launched in March 2026 for Android and iOS. It ships as an APK, not through Google Play.
- **You don't need it** if you're on a GB-based plan. Those credentials work straight from the web dashboard using username/password authentication.
- **IP-based plans are the awkward one on Android.** They activate through port forwarding inside the desktop app, so a computer has to be running on the same network.
- **Third-party "9Proxy APK" mirrors are a real risk.** 9Proxy's own documentation states the APK should only ever come from its official download page.

Everything below is based on 9Proxy's official documentation, its published price list, and its pricing announcement from May 2026.

## What ProxyHub Lite actually is

ProxyHub Lite is 9Proxy's phone app. You install it, sign in with your 9Proxy account, tap to allow it to create a connection, and your traffic routes through a proxy. That's the whole flow — no config files, no port juggling on the phone itself.

Worth knowing before you start:

- **Requirements:** Android 7.0 or later, about 100 MB of free storage, and a stable connection.
- **Installation:** APK only. Android will show an "unknown sources" or "install blocked" warning — that's standard behaviour for anything installed outside the Play Store, not a sign something is wrong.
- **Updates are manual.** There's no auto-update, so you re-download the APK when a new version lands.
- **It works standalone.** You don't need ProxyHub Pro to use Lite. If you do sign into both with the same account, the phone shows up in ProxyHub Pro automatically and can be controlled from your computer.

The catch most articles skip: because the app isn't on the Play Store, there's no store-level verification for you to lean on. 9Proxy's documentation is explicit that the APK should be downloaded from official 9Proxy sources only, and it names the expected file — `9proxy-hub-lite-v1.0.0.apk`. If a random site is offering a "9Proxy mod" or an "unlocked" build, that file has nothing to do with 9Proxy.

## Two more ways to get a proxy onto Android

The app isn't the only route. Depending on which plan you're on, you might not need it at all.

**Manual system proxy (APN or Wi-Fi).** Android lets you set a proxy at the network level, and 9Proxy documents both variants. This path uses a structured username and password rather than an app, which is exactly how GB-based residential plans authenticate.

**IP-based plans via desktop port forwarding.** Here the proxy list lives in the 9Proxy desktop app. You forward an IP to a local port, then point the phone at your computer's LAN IP and that forwarded port. Both devices must be on the same network, and firewalls or antivirus tools blocking the connection will break it.

| Setup route | Who it suits | Needs a PC | Protocol notes |
| --- | --- | --- | --- |
| ProxyHub Lite app | Anyone who wants a phone-only workflow | No | As documented, connects directly on-device |
| Manual APN / Wi-Fi proxy | GB-based plan holders, people who want system-wide routing | No | Mobile-data proxies can be HTTP only |
| Desktop port forwarding | IP-based plan holders already running the desktop app | Yes, on the same LAN | Traffic goes through your computer |

If you're phone-first, the third option is the one to plan around. It's not broken — it's just built for a desktop workflow first.

## Setting it up, step by step

### Route 1: ProxyHub Lite

1. Create a 9Proxy account and pick a plan.
2. Download the ProxyHub Lite APK from the official 9Proxy download page.
3. Open the file from your Downloads folder and tap **Install anyway** if Android asks.
4. Launch the app and sign in with your 9Proxy account.
5. Tap **OK** when Android asks permission to create a connection and manage network traffic.
6. Connect a proxy and check your IP has changed.

### Route 2: Manual configuration

Before touching Android settings, two things have to exist in your account: a sub-user, and a generated proxy session. The credentials come from those.

**On mobile data (APN):** go to **Settings → Network & internet → Internet**, tap your carrier, scroll to **Access Point Names**, pick the APN you're currently using, and fill in the proxy fields.

- Server: your proxy IP address
- Port: your proxy port, for example `17521`
- Username: the structured proxy string
- Password: your sub-account password

The username carries your targeting rules, so it looks like this rather than a plain login:


useruser123-country-US-ssid-rhdN1907ma


That string says: use the `useruser123` sub-user, route through the United States, and keep this session separate under the ID `rhdN1907ma`. Sticky sessions add a duration parameter — `country-us-sst-15-ssid-device1` holds the same IP for 15 minutes.

**On Wi-Fi:** go to **Settings → Network & internet → Internet**, tap the connected network, hit the edit icon, expand **Advanced options**, set **Proxy** to **Manual**, and enter the hostname and port. Your browser will prompt for the credentials, or you can enter them when asked and hit Sign in.

> One limitation to know in advance: when you proxy a mobile network at the APN level, the connection type can only be HTTP. If your tool needs SOCKS5, the APN route won't be the one.

### Testing and troubleshooting

Run a quick check that the exit IP matches the country, city, or ISP you targeted. If it doesn't connect, the usual culprits are, in order: a mistyped IP or port, the phone and computer not being on the same Wi-Fi network, a firewall or VPN interfering, and a browser that cached the old connection. Restart the browser or try a different one before assuming the proxy is dead.

For the app itself: if the APK won't install, check that installation from unknown sources is enabled for your browser or file manager and that your Android version is supported. If the app installs but won't open, restart the device or reinstall.

## Which plan makes sense when Android is your main device

This is where the "which one do I buy" question actually has a clear answer, because the two billing models behave differently on a phone.

**GB-based plans (pay per gigabyte)** are the smoother fit. Authentication is username/password from the dashboard, so nothing needs to be installed on a computer — you can go from purchase to a working Android connection in one sitting. You also get rotating mode (a new IP per request) or sticky mode (same IP held for the session minutes you set). The trade-off is a validity window: 180 days on standard GB packs, unlimited on the enterprise tiers.

**IP-based plans (pay per IP, unlimited bandwidth)** suit heavy, always-on work — long scraping runs, a pile of separate browser profiles, sessions where bandwidth is unpredictable. Unused IPs never expire, and once activated an IP stays online from a few hours up to roughly 24 hours depending on the pool. But activation goes through the desktop app's port forwarding, and auto-refresh plus auto-rotation are configured there too. On a phone-only setup, that's friction you're signing up for deliberately.

Practical Android use cases split along the same line. Rotating through many countries to check geo-restricted listings, testing how an app behaves in another region, or running a handful of social accounts points at GB plans. Keeping one stable identity alive for hours on one device points at per-IP.

Two features are worth factoring in either way. **Today List** lets you reuse any proxy from the previous 24 hours at no extra cost, which matters if your tasks repeat daily. The **60-second invalid-IP policy** credits or replaces a proxy that fails to connect in its first minute, so a dead IP doesn't turn into a paid dead IP. Support runs 24/7 through live chat, email, and Telegram.

## The full price list

These are the current figures. 9Proxy raised prices on IP-based and bundle packages on 1 June 2026 — GB-based pricing was left untouched in that change, so older comparisons you find online may quote lower IP-based numbers that no longer apply.

| Model | Package | Price | Effective rate | Billing / validity | Get it |
| --- | --- | --- | --- | --- | --- |
| Residential by IP | 100 IPs | $24 | $0.24 / IP | One-off, IPs never expire | [Buy the 100 IP pack](https://bit.ly/9-Proxy) |
| Residential by IP | 500 IPs | $72 | $0.144 / IP | One-off, IPs never expire | [Buy the 500 IP pack](https://bit.ly/9-Proxy) |
| Residential by IP | 1,000 + 500 bonus IPs | $126 | $0.084 / IP | One-off, IPs never expire | [Buy the 1,500 IP pack](https://bit.ly/9-Proxy) |
| Residential by IP | 2,500 IPs | $210 | $0.084 / IP | One-off, IPs never expire | [Buy the 2,500 IP pack](https://bit.ly/9-Proxy) |
| Residential by IP | 5,000 IPs | $360 | $0.072 / IP | One-off, IPs never expire | [Buy the 5,000 IP pack](https://bit.ly/9-Proxy) |
| Residential by IP | 15,000 IPs | $720 | $0.048 / IP | One-off, IPs never expire | [Buy the 15,000 IP pack](https://bit.ly/9-Proxy) |
| Residential by IP | 25,000 IPs | $863 | $0.035 / IP | One-off, IPs never expire | [Buy the 25,000 IP pack](https://bit.ly/9-Proxy) |
| Residential by IP | 50,000 IPs | $1,438 | $0.029 / IP | One-off, IPs never expire | [Buy the 50,000 IP pack](https://bit.ly/9-Proxy) |
| Business IP | 100,000 IPs | $2,300 | $0.023 / IP | One-off, IPs never expire | [Buy the 100,000 IP pack](https://bit.ly/9-Proxy) |
| Business IP | 200,000 IPs | $4,140 | $0.021 / IP | One-off, IPs never expire | [Buy the 200,000 IP pack](https://bit.ly/9-Proxy) |
| Business IP | 500,000 IPs | $8,625 | $0.018 / IP | One-off, IPs never expire | [Buy the 500,000 IP pack](https://bit.ly/9-Proxy) |
| Residential by GB | 5 GB | $15 | $3.00 / GB | Prepaid, 180-day validity | [Buy the 5 GB pack](https://bit.ly/9-Proxy) |
| Residential by GB | 50 GB + 5 GB bonus | $105 | $2.10 / GB | Prepaid, 180-day validity | [Buy the 55 GB pack](https://bit.ly/9-Proxy) |
| Residential by GB | 100 GB | $150 | $1.50 / GB | Prepaid, 180-day validity | [Buy the 100 GB pack](https://bit.ly/9-Proxy) |
| Residential by GB | 200 GB | $200 | $1.00 / GB | Prepaid, 180-day validity | [Buy the 200 GB pack](https://bit.ly/9-Proxy) |
| Residential by GB | 1,000 GB | $800 | $0.80 / GB | Prepaid, 180-day validity | [Buy the 1,000 GB pack](https://bit.ly/9-Proxy) |
| Residential by GB | 2,000 GB | $1,500 | $0.75 / GB | Prepaid, 180-day validity | [Buy the 2,000 GB pack](https://bit.ly/9-Proxy) |
| Enterprise GB | 3,000 GB | $2,160 | $0.72 / GB | Prepaid, never expires | [Buy the 3,000 GB pack](https://bit.ly/9-Proxy) |
| Enterprise GB | 6,000 GB | $4,200 | $0.70 / GB | Prepaid, never expires | [Buy the 6,000 GB pack](https://bit.ly/9-Proxy) |
| Enterprise GB | 10,000 GB | $6,800 | $0.68 / GB | Prepaid, never expires | [Buy the 10,000 GB pack](https://bit.ly/9-Proxy) |
| Bundle | Starter — 100 IPs + 5 GB | $30 | — | Bundled traffic valid 180 days | [Buy the Starter bundle](https://bit.ly/9-Proxy) |
| Bundle | Popular — 1,500 IPs + 50 GB | $180 | — | Bundled traffic valid 180 days | [Buy the Popular bundle](https://bit.ly/9-Proxy) |
| Bundle | Pro — 5,000 IPs + 500 GB | $720 | — | Bundled traffic valid 180 days | [Buy the Pro bundle](https://bit.ly/9-Proxy) |

Payment methods include credit card, cryptocurrency, local payment options, Google Pay, Alipay, and the built-in 9Proxy wallet. Registering an account is free, so you can create the login and look at the dashboard before committing to anything. The cheapest way to test the whole Android flow — app or manual config included — is the 5 GB pack at $15.

## What the reviews actually say

9Proxy's Trustpilot page is genuinely mixed, and the pattern in the negative reviews is worth understanding before you pay. The recurring complaints are about refunds: buyers who expected a plain IP:Port list and got an app-based service, or who bought the smallest package expecting rotating proxies and discovered it was residential-only. 9Proxy's public replies on those threads point back to its refund policy and offer live chat, which is a fair answer and also a reminder to read the policy at checkout.

The positive reviews tend to come from people running data-heavy work, and they focus on stability and speed rather than price. Independent reviews land in the same place: geekflare's 2026 assessment treats the per-IP unlimited-bandwidth model as the main differentiator, while noting the GB-based structure is usually cheaper for high-rotation, low-bandwidth jobs.

The honest takeaway: if your Android use case fits the GB model — limited, bursty, geo-checking style work — start with the $15 pack and see how the app behaves on your device and carrier. Buying 25,000 IPs before you've confirmed your phone's APN config plays nicely with your network is the expensive way to learn.

## FAQ

### Is there an official 9Proxy app for Android?

Yes. ProxyHub Lite launched in March 2026 for Android and iOS. On Android it's distributed as an APK rather than through Google Play, requires Android 7.0 or later, and updates are manual.

### Is the 9Proxy APK on third-party download sites safe?

Treat it as unverified at best. 9Proxy's documentation says to get the APK from official 9Proxy sources only. There's no store review process standing between you and a repackaged file on a mirror site.

### Can I use 9Proxy on Android without a PC?

Yes — with ProxyHub Lite, or with GB-based credentials entered manually in APN or Wi-Fi settings. Only IP-based residential plans require the desktop app's port forwarding, which means a computer on the same local network.

### Do IP-based plans work on an Android phone at all?

They do, but through your computer: forward an IP to a port in the desktop app, then set the phone's proxy to the computer's LAN IP and that port. Firewalls and antivirus blocking the connection are the usual failure point.

### Can I use a proxy on mobile data rather than Wi-Fi?

Yes, through the APN settings. One constraint from the documentation: mobile-network proxies can be HTTP only, so SOCKS5-dependent tools need the Wi-Fi route or the app.

### How long does a proxy IP stay alive?

On GB-based plans you control it — sticky mode holds an IP for the session time you set, or you rotate per request. On IP-based plans an activated IP lasts from a few hours to roughly 24 hours, and auto-refresh replaces ones that drop.

### What's the cheapest way to start?

Registering an account costs nothing, and the 5 GB residential package is $15 with 180-day validity. If you'd rather test the per-IP workflow, 100 IPs is $24 and those IPs don't expire.

👉 [Create your 9Proxy account and pick a plan](https://bit.ly/9-Proxy)
