# Resilient VPN — experimental Android build

Noncommercial fork of [Hiddify](https://github.com/hiddify/hiddify-app), under its [extended GPLv3 license](LICENSE.md). Not affiliated with or endorsed by Hiddify.

## Corresponding source

`resilient-source.tar.gz` contains the complete Android application source, tests,
feed attribution and build instructions. Extract it into an empty directory.
Based on official Hiddify v4.1.1 (`abbd671bf6bf05195acd4158c714bff267cada8f`),
with changes through local commit `dc8ca90`. The unrelated prebuilt iOS core binary
is omitted; the pinned Android engine is downloaded and checksum-verified during build.

Source archive SHA-256:
`ba915a32215f3bcc8cbd2d074db9e4d6eeca8d394dee932305f40e7e7fedcef0`

## Changes

- Separate app ID `org.goldis.resilientvpn` and distinct icon; Persian/English dashboard.
- 434 untested public profiles cached for offline startup, eight GitHub feeds from
  two maintainers, HTTPS refresh, Contents API fallback, atomic cache and rollback.
- Secure VLESS/Trojan/Hysteria2 profile parsing; no plaintext or disabled TLS.
- One tunnel at a time, 12-second attempts, 90-second search budgets, retained search
  progress, recent working profiles, cooldowns and transport diversity.
- Connection status based on expected HTTPS payloads through the local VPN proxy.
- Native permission cancellation guards, confirmed shutdown, and selected-network
  generation invalidation. Private local history and redacted diagnostics.
- No analytics, promotional remote flows, or arbitrary configuration execution.

## Build and limitations

The manual **Resilient Android** Actions workflow verifies/extracts this archive,
runs the tests and builds an ARM64 APK using a dedicated private signing key.
Signing secrets must be configured before the signed build can run.

All 53 Flutter tests and the native consent-generation test passed locally.
No physical Android or Iranian network test has been performed. Native tunnel
routing, permission dialogs, DNS/IPv6 leaks and Wi-Fi/mobile switching still need
device validation. This is experimental software, not a proven emergency service.
Unknown public server operators are not trustworthy merely because profiles pass
parsing. No VPN can restore connectivity when no route to an external relay exists.
Download/install alternatives and save information while connectivity is available.

Manual Refresh can retry after an offline failure; automatic refresh is best-effort
while the app runs and may wait six hours. Public configurations can stop working
at any time. See `docs/` inside the source archive for research, licensing and
verification details.
