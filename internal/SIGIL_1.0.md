# SockLove Audits Internal Sigil 1.0

> The page that reads nothing and sends nothing, attacked as it will be placed.

---

An internal security review by
🔥 **[Sockpusher](https://etherscan.io/address/sockpusher.socklove.eth)**
([sockpusher@tuta.io](mailto:sockpusher@tuta.io)) alone.

---

## 📋 Summary

👀 **[Sigil](https://sigil.socklove.eth.limo)** `1.0 · Proposal`: one
[HTML](https://html.spec.whatwg.org/)
📄 **[Page](https://github.com/socklove-eth/pages/tree/v1.0)** turning a
transaction hash into ten numbered
🧿 **[Marks](https://github.com/socklove-eth/pages/blob/v1.0/marks/marks.json)**
that two people read aloud and compare.

Sigil's **CID**: `bafybeiaccoud5ul67etgcyzmciqtabj2uha5cgrp6xr2pttmrnfindzcj4`,
rebuilt from a clean checkout;
[Kubo](https://github.com/ipfs/kubo/releases/tag/v0.43.1) `0.43.1` agrees under
`unixfs-v1-2025`.

**No findings**, Critical to Informational. Sigil draws Marks only for the hash
given, and sends nothing. The residual risk is the reader's: the right bytes,
all ten Marks compared.

---

## 🗺️ Scope

- **Source:** tag `v1.0`, which builds the CID above.
- **Code:**
[main.ts](https://github.com/socklove-eth/pages/blob/v1.0/src/sigil/main.ts),
[index.html](https://github.com/socklove-eth/pages/blob/v1.0/src/sigil/index.html),
[marks/](https://github.com/socklove-eth/pages/tree/v1.0/marks), the
✨ **[Light](https://github.com/socklove-eth/docs/blob/v1.0/STYLE.md)**,
the shell, [fonts/](https://github.com/socklove-eth/pages/tree/v1.0/fonts),
[logo.png](https://github.com/socklove-eth/pages/blob/v1.0/logo.png),
[favicon.png](https://github.com/socklove-eth/pages/blob/v1.0/favicon.png).
- **Build:**
[build.mjs](https://github.com/socklove-eth/pages/blob/v1.0/build.mjs),
[scripts/](https://github.com/socklove-eth/pages/tree/v1.0/scripts),
[package-lock.json](https://github.com/socklove-eth/pages/blob/v1.0/package-lock.json),
[pages.yml](https://github.com/socklove-eth/pages/blob/v1.0/.github/workflows/pages.yml).
- **Claims:**
[SECURITY.md](https://github.com/socklove-eth/pages/blob/v1.0/SECURITY.md),
[STANDARD.md](https://github.com/socklove-eth/pages/blob/v1.0/STANDARD.md),
[ARCHITECTURE.md](https://github.com/socklove-eth/docs/blob/v1.0/ARCHITECTURE.md).
- **Evidence:** unit, harness and browser
([Chromium](https://www.chromium.org/), [Firefox](https://www.firefox.com/))
tests; the Marks read aloud, and heard through a screen reader, by hand.

---

## 🔬 Method

| # | Step | Result |
|---|---|---|
| 1 | Every claim, then [main.ts](https://github.com/socklove-eth/pages/blob/v1.0/src/sigil/main.ts) and [marks/](https://github.com/socklove-eth/pages/tree/v1.0/marks), attacked as an adversary would, in rounds until none remained. | No findings. |
| 2 | [npm](https://docs.npmjs.com/)'s `npm ci` in a clean copy, `npm run build`; Kubo, [SHA-512](https://csrc.nist.gov/pubs/fips/180-4/upd1/final)-checked. | One CID three ways. |
| 3 | The reference vector in [Node.js](https://nodejs.org/docs/latest/api/), [Python](https://docs.python.org/3/), Chromium and Firefox. | `tongue, seat, fire, hammer, moon, candle, pill, bed, hourglass, rose` |
| 4 | The built policy and the bundle: network, storage, navigation, string-to-HTML and messaging calls. | `default-src 'none'`, hashes only; none. |
| 5 | Every input path, and 300 random sequences of typing, pasting, Enter and waiting. | Marks only for a valid hash; drawn, labelled and spoken alike. |
| 6 | One derivation timed. | 0.43 s on a laptop. |
| 7 | `npm audit`; [age.mjs](https://github.com/socklove-eth/pages/blob/v1.0/scripts/age.mjs), as `scripts/age.mjs 7`; action pins against their tags. | 0; none too young; each pin its tag's commit. |

---

## 📏 Severity

| Level | Meaning |
|---|---|
| Critical | Moves the 💍 **[Ring](https://etherscan.io/address/socklove.eth)**, 🌐 `socklove.eth` or anything else 🧦💜 **[SockLove](https://github.com/socklove-eth)** owns, without both parties' consent. |
| High | Makes anyone sign, send or execute other than what they were shown, with no unusual step. |
| Medium | The same, or a stated protection defeated, given a step anyone can be led into. |
| Low | Stalls, misleads or exposes anyone, or weakens a check; nothing moves. |
| Informational | A gap in a guard, a test or a document, with no path to harm. |

---

## ✅ Claims checked

Every claim holds; one marked *caveat* holds with a limit, named beside it.

### 🛡️ SECURITY.md

| Claim | Evidence |
|---|---|
| Sigil trusts the browser's cryptography, the gateway and `contenthash`; no wallet, no network. | `marks()` on [Web Crypto](https://developer.mozilla.org/en-US/docs/Web/API/Web_Crypto_API) alone; e2e "Sigil refuses a request made from the page", "derives the reference vector with no request made". |
| A faulty Sigil makes the Marks disagree; a hostile one could make them agree: verify its name and CID. | Step 2. |
| Runs as a saved file. | E2e "runs from a local file". |
| Never draws Marks for a hash it was not given. | `render()`'s generation guard; e2e "a newer hash wins over one still being read"; step 5. |
| Frame and path gateway refusals in script (*caveat*: a frame that runs no script leaves the Page inert). | `framed()`, `onSharedGateway()`; e2e "Sigil refuses to run inside a frame" and under five paths. |
| Current engines enforce [Trusted Types](https://developer.mozilla.org/en-US/docs/Web/API/Trusted_Types_API). | E2e "Sigil refuses HTML written from a string". |
| Sixty bits guard a fixed hash, not two chosen together. | About 2⁶⁰ attempts, 13 million card-years; two together about 2³⁰, days on one card; unit "make an offline grind expensive". |

### 🏗️ ARCHITECTURE.md

| Claim | Evidence |
|---|---|
| One inlined file; script and style by hash; a [CSP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy) of `default-src 'none'`. | `lockCsp`, `audit()`; unit "declares a CSP with no network access, so a pasted hash cannot leave the page". |
| Every screen from elements and text. | `draw()`; unit "lets no script write HTML from a string". |
| [PBKDF2](https://www.rfc-editor.org/rfc/rfc8018.html)-[SHA-256](https://csrc.nist.gov/pubs/fips/180-4/upd1/final), 4,000,000 iterations, prefix and salt; the password as 64 lowercase hex digits; a byte shifted right by two. | `marks()`, `normalize()`; unit "match the reference vectors, index and name", "are domain-separated and versioned". |
| Numbered 1 to 10; spoken to a screen reader once, never translated. | `draw()`, `#spoken`; harness "each Mark numbered 1 to 10, in order", "and spoken from a hidden live line, the image itself not live", "and neither the Marks nor their spoken line is translated". |
| [Emoji `13.0`](https://www.unicode.org/emoji/charts-13.0/emoji-released.html) or earlier, no joiners or skin tones; each named for what it shows; no repeat, prefix, one-edit pair, same-length three-letter ending, or rhyme on the stressed syllable. | Unit "carry nothing after Emoji 13.0", "carry no ZWJ sequence and no skin-tone modifier", "repeat no name, and no name is a prefix of another", "keep every pair more than one edit apart", "let no two names of the same length rhyme"; the names read aloud, by hand. |
| Refusals silent, the field marked invalid until it next changes or takes a paste. | `refuseField()`; e2e "says nothing for …"; harness "a pasted non-hash: emptied, marked invalid for a screen reader". |
| The hash on screen, entered again, starts no second derivation. | `render()`'s `current`; harness "then Enter, and the same hash pasted in capitals: still no new derivation". |
| One error without Web Crypto. | `CannotRead`; e2e "Sigil outside a secure context says it cannot read the Marks". |
| Pinned forever. | Unit "has pinned bytes", "are domain-separated and versioned", "make an offline grind expensive". |

### 📐 STANDARD.md

| Claim | Evidence |
|---|---|
| No navigation; refusals present and run; one file. | `audit()`; unit "never navigates away and never opens a tab", "refuses to run inside a frame, or on a shared path gateway"; e2e gateway refusals. |
| The shell; only the middle scrolls. | E2e "Sigil fits, and only its middle scrolls". |
| Refused fields. | `.quill.pricked`, `--thorn`: [STYLE.md](https://github.com/socklove-eth/docs/blob/v1.0/STYLE.md). |

---

## 🙈 Not reviewed

- **Engines** other than Chromium and Firefox.
- **Other screen readers**: one heard by hand; the rest, what the
accessibility tree exposes.
- **Browser translation, keyboard insertions, drag-and-drop**: reasoned, not
exercised.
- **The GPU rate**: one public benchmark,
[hashcat](https://hashcat.net/hashcat/) on an RTX 5090 at 11,157.2 kH/s for 999
iterations, not measured.
- Gateways serving this CID: no name carries it yet.
