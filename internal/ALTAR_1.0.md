# SockLove Audits Internal Altar 1.0

> The one page that asks for a signature, attacked as it will be placed.

---

An internal security review by
🔥 **[Sockpusher](https://etherscan.io/address/sockpusher.socklove.eth)**
([sockpusher@tuta.io](mailto:sockpusher@tuta.io)) alone.

---

## 📋 Summary

💒 **[Altar](https://altar.socklove.eth.limo)** `1.0 · Proposal`: one
[HTML](https://html.spec.whatwg.org/)
📄 **[Page](https://github.com/socklove-eth/pages/tree/v1.0)** taking the
💍 **[Ring](https://etherscan.io/address/socklove.eth)**, the
🔐 **[Safe](https://safe.global/)** `1.4.1` at
`0x0857293192bF97Ee73bB471c185E1933Fa51E0ca`, from 1-of-1 to 2-of-2.

Altar's **CID**: `bafybeievodve5kgje5s4xzntroaz46w3hqyrlkmggfk3xgnuu5mckmqfoy`,
rebuilt from a clean checkout;
[Kubo](https://github.com/ipfs/kubo/releases/tag/v0.43.1) `0.43.1` agrees under
`unixfs-v1-2025`.

**No findings**, Critical to Informational. Served from its own origin, Altar
signs and executes only the
🧎 **[Proposal](https://github.com/socklove-eth/.github/blob/v1.0/RELEASE.md)**
batch it shows.

---

## 🗺️ Scope

- **Source:** tag `v1.0`, which builds the CID above.
- **Code:**
[main.ts](https://github.com/socklove-eth/pages/blob/v1.0/src/altar/main.ts),
[lib/](https://github.com/socklove-eth/pages/tree/v1.0/src/altar/lib),
[index.html](https://github.com/socklove-eth/pages/blob/v1.0/src/altar/index.html),
the bundled [viem](https://viem.sh/) and [qr](https://github.com/paulmillr/qr),
the
✨ **[Light](https://github.com/socklove-eth/docs/blob/v1.0/STYLE.md)**,
the shell, [fonts/](https://github.com/socklove-eth/pages/tree/v1.0/fonts),
[logo.png](https://github.com/socklove-eth/pages/blob/v1.0/logo.png),
[favicon.png](https://github.com/socklove-eth/pages/blob/v1.0/favicon.png).
- **Build:**
[build.mjs](https://github.com/socklove-eth/pages/blob/v1.0/build.mjs),
[scripts/](https://github.com/socklove-eth/pages/tree/v1.0/scripts),
[.env](https://github.com/socklove-eth/pages/blob/v1.0/.env),
[package-lock.json](https://github.com/socklove-eth/pages/blob/v1.0/package-lock.json),
[pages.yml](https://github.com/socklove-eth/pages/blob/v1.0/.github/workflows/pages.yml).
- **Claims:**
[SECURITY.md](https://github.com/socklove-eth/pages/blob/v1.0/SECURITY.md),
[STANDARD.md](https://github.com/socklove-eth/pages/blob/v1.0/STANDARD.md),
[ARCHITECTURE.md](https://github.com/socklove-eth/docs/blob/v1.0/ARCHITECTURE.md),
[REGISTRY.md](https://github.com/socklove-eth/docs/blob/v1.0/REGISTRY.md).
- **Evidence:** unit, harness, browser ([Chromium](https://www.chromium.org/),
[Firefox](https://www.firefox.com/)) and fork tests.

---

## 🔬 Method

| # | Step | Result |
|---|---|---|
| 1 | Every claim, then [main.ts](https://github.com/socklove-eth/pages/blob/v1.0/src/altar/main.ts) and each module in [lib/](https://github.com/socklove-eth/pages/tree/v1.0/src/altar/lib), attacked as an adversary would, in rounds until none remained. | No findings. |
| 2 | [npm](https://docs.npmjs.com/)'s `npm ci` in a clean copy, `npm run build`; Kubo, [SHA-512](https://csrc.nist.gov/pubs/fips/180-4/upd1/final)-checked. | One CID three ways. |
| 3 | Every test layer; the fork check on a fork of ⛓️ **[Ethereum](https://ethereum.org/)**. | Green. |
| 4 | The built policy; the bundle searched for `window.open`, `location.assign`, `location.replace`, `innerHTML`, `outerHTML`, `insertAdjacentHTML`, `document.write`, `eval(`, `new Function`, `sendBeacon`, `WebSocket(`, `new Worker`, `postMessage`, `srcdoc`, `sourceMappingURL`, `localStorage`, `indexedDB`. | Hashes only; none. Network only through viem's [JSON-RPC](https://ethereum.org/developers/docs/apis/json-rpc/) transport; its off-chain lookup off (`ccipRead: false`). |
| 5 | `npm audit`; [age.mjs](https://github.com/socklove-eth/pages/blob/v1.0/scripts/age.mjs), as `scripts/age.mjs 7`; [Node.js](https://nodejs.org/docs/latest/api/) per [.nvmrc](https://github.com/socklove-eth/pages/blob/v1.0/.nvmrc); action pins against their tags. | 0; none too young; `26.11.1`; each pin its tag's commit. |
| 6 | Each of the ten baked endpoints from Altar's origin: preflight, `eth_chainId`, a read at a block hash. | Origin allowed, `0x1`, an unknown hash refused. |
| 7 | The .eth.limo gateway: a served name's headers; `/ipfs/`, `/IPFS/`, `/ipns/` under it. | `frame-ancestors 'self'`, `X-Frame-Options: SAMEORIGIN`; `404` each. |

---

## 📏 Severity

| Level | Meaning |
|---|---|
| Critical | Moves the Ring, 🌐 `socklove.eth` or anything else 🧦💜 **[SockLove](https://github.com/socklove-eth)** owns, without both parties' consent. |
| High | Makes anyone sign, send or execute other than what they were shown, with no unusual step. |
| Medium | The same, or a stated protection defeated, given a step anyone can be led into. |
| Low | Stalls, misleads or exposes anyone, or weakens a check; nothing moves. |
| Informational | A gap in a guard, a test or a document, with no path to harm. |

---

## ✅ Claims checked

Every claim holds; each marked *caveat* holds with a limit, named beside it.

### 🛡️ SECURITY.md

| Claim | Evidence |
|---|---|
| Endpoints lie but move nothing: the Ring and resolver pinned, off-chain lookups off; the first answer sets the chain, each endpoint held to it. | `readSafeState()`, `readResolver()`, `connectChain()`, `onChain()`; e2e "refuses a kept endpoint on another chain, and says so". |
| At 1-of-1 another resolver or address is refused. | `ResolverMismatch`; harness "a Ring awaiting the Proposal is not read when the name resolves elsewhere". |
| A supplied endpoint replaces the rest; no record moves it; it is forgotten when the first read through it fails at load or after the Connect button, when it cannot be reached or answers for another chain as the Ask or Yes button acts, or when it reads the name unset or moved where the screen can be redrawn. | `initialUrls()`, `rpcFailed()`, `unreached()`, `nameGone()`; harness "a supplied endpoint is kept: the record is not followed", "a typed endpoint naming another resolver: the RPC prompt, saying what it read, never a final refusal". |
| The 🔧 **[Living Registry](https://github.com/socklove-eth/docs/blob/v1.0/REGISTRY.md)**: written by the Ring alone; its endpoints trusted no more, named once they answer for the chain, passed over once unreachable (*caveat*: operator approvals for the Ring not enumerated). | `endpointsFrom()`, `adoptRecordEndpoints()`, `checked()`; unit "tells only an endpoint on the chain that it is trusted, and only once", "passes over an endpoint it could not reach, for good, without asking it again", "passes over an endpoint that stops answering after it was trusted, without asking it again"; fork check. |
| The signed link recovered, never trusted; recovery byte 27 or 28, low `s`. | `signedByOwner()`, `validHandoff()`, `lowS()`; unit "refuses a tampered field, another Safe and another nonce", "refuses the high-s twin of a signature, so each signature has one form". |
| The link a capability: any holder at **Threshold** 1; only as a [QR code](https://www.iso.org/standard/83389.html), query dropped; the **Nonce** voids it, the one the endpoint reports. | `linkFor()`, `nonceMoved()`; e2e "puts the question, the hash and then the code in that order, and the link only in the code". |
| The wallet shows the **SafeTx**, not the owner inside its data; the hash compares (*caveat*: the asker sees it after signing, by design). | `hashLine()`; harness "the transaction hash is printed in full". |
| What the endpoint learns: the Nonce every five minutes, none while hidden; the receipt wait, until it arrives, its endpoint is forgotten, or a read fails once Done shows; across a reload, a check every twelve seconds until the send is seen, the Nonce moves, a read fails, or six minutes after the send pass. | `watch()`, `installWatch()`, `settle()`, `sendStands()`; harness "a hidden tab reads nothing", "a send never mined, its endpoint then forgotten: the wait stops asking that endpoint, at once", "a reload while it is pending waits again: no Yes to press twice". |
| The notice names the host answering now, and a forgotten one no longer. | `showHost()`, `forgetEndpoints()`; harness "and the notice names the endpoint answering now, alone", "a late answer from a forgotten endpoint names nobody in the footer". |
| Frame, path gateway and `file://` refusals in script. | `framed()`, `onSharedGateway()`; e2e "Altar refuses to run inside a frame", "Altar opened from file:// refuses to run, reading and storing nothing". |
| Current engines enforce [Trusted Types](https://developer.mozilla.org/en-US/docs/Web/API/Trusted_Types_API). | E2e "Altar refuses HTML written from a string", Chromium and Firefox. |
| Local-chain signatures worthless on Ethereum. | `safeTxDomain()`; unit "uses a domain of chainId and verifyingContract only". |

### 🏗️ ARCHITECTURE.md

| Claim | Evidence |
|---|---|
| The Ring read at its own address with no wallet; the name only at 1-of-1; the yes stays shown. | `readSafeState()`, `render()`; e2e "and keeps showing it"; harness "the yes stays shown after the name moves to another resolver". |
| A wallet only on the Ask or Yes button; *Which wallet?* per tab, the first announcement per wallet ID kept; chain switch, silence or a line. | `connect()`, `askForWallet()`, `listenForWallets()`; harness "a second announcement under the same name: the first wallet signs, nothing is asked". |
| The Nonce every five minutes, never over input, a wallet call or a message; read again before each button acts; a lower one ignored; the Done screen final. | `checkNonce()`, `safeToRedraw()`, `nonceMoved()`; e2e "re-reads the Nonce before signing: a moved one redraws instead"; harness "an older Nonce from a lagging node never refuses a valid link". |
| A name moved or unset after load ends the Page, where a redraw is safe; read through your own endpoint, the RPC screen says so. | `nameGone()`; harness "the name moves after the page read it, through the baked set: …", "a moved name the watch reads while a hand is writing: the field is left alone". |
| A checksummed address the Safe could add only; refused fields marked invalid; the Handoff only for an owner's signature. | `renderAsk()`, `refuseField()`, `sign()`; harness "the zero address is cleared, silently", "an owner already is cleared, silently", "a signature no owner made: …", "a wallet returning the high-s twin still produces a link, in its low-s form". |
| Quiet errors; *No wallet.* cleared once a wallet announces itself. | `walletFailed()`, `listenForWallets()`; harness 'no wallet: the ask says "No wallet."', 'a wallet announcing afterwards: "No wallet." is gone'. |
| After Yes: no timeout, the receipt waited for until it holds, then the Ring read in its canonical block; revert, replacement or cancel seen while waiting: the Answer, *It did not go through.*, or, the Nonce risen, *This Proposal cannot be answered.*; never mined: the wait while the tab is open and the Nonce unmoved; after a reload, until, six minutes after the send, the chain does not know it and the Nonce is unmoved; a superseded Yes never re-arms a newer one (*caveat*: the reorg branch untested on [Anvil](https://www.getfoundry.sh/anvil)). | `settle()`, `persist()`, `sendStands()`; harness "a revert seen through a dropped connection: …", "a send replaced by a cancel: …", "a revert that spent the link: it is refused at once", "a reload waiting for an unseen send, the Nonce then moved: the link is spent, and refused", "and keeps waiting: no Yes to press again, nothing said", "and so does a reload of the same tab, once the chain has not known the send for six minutes: it was dropped", "a superseded Yes never re-arms the newer one while it is open in the wallet". |
| Four seconds and one retry per endpoint, the whole answer within them, the set retried up to three times. | `endpoint()`, `fetchWhole()`; viem's fallback; unit "gives up on an answer that stalls after its headers, and the fallback moves on", "gives up on an answer past viem's size cap as it arrives, never holding the rest". |
| Your endpoint: https or loopback; replaces the set; one whose first read fails at load or after the Connect button, or one that cannot be reached or answers for another chain as the Ask or Yes button acts, forgotten; the RPC screen at the Ask and Yes buttons. | `askForRpc()`, `rpcFailed()`, `unreached()`; harness "the Ask button with the typed endpoint gone: …"; unit "is true for an endpoint that answers for another chain, bare or wrapped". |
| One SafeTx, `DELEGATECALL` into [MultiSendCallOnly](https://github.com/safe-fndn/safe-smart-account/blob/v1.4.1/contracts/libraries/MultiSendCallOnly.sol), four calls, owner last, gas and refund fields zero. | `batchSafeTx()`; unit "is exactly four calls, in the order the authorisation requires"; fork check, executed. |
| Invariants: one builder; nothing that acts from data; one set of bytes on both chains; the CID a function of the source (*caveat*: built in the `node_modules` `npm ci` makes). | `safeTxFor()`, `pageConfig()`; harness "the page's SafeTx hash matches the Safe's getTransactionHash"; fork check; step 2. |

### 📐 STANDARD.md and REGISTRY.md

| Claim | Evidence |
|---|---|
| No navigation; refusals present and run; one file; the [CSP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy). | `audit()`; unit "never navigates away and never opens a tab"; e2e gateway refusals. |
| Only the middle scrolls. | E2e "Altar fits, and only its middle scrolls". |
| The wallet in the browser, its signature the act, the Ring batching. | `writeContract` to the wallet alone. |
| Refused fields, buttons read by their words. | Unit "marks the field invalid for a screen reader until the next keystroke"; e2e "no button on any Altar screen is read with its emoji". |
| The record's rules: https, public hosts, no credentials, kept only as the [URL parser](https://url.spec.whatwg.org/) writes it, repeats dropped. | `endpointsFrom()`, `isLocalHost()`; unit "drops every host on this machine or its network", "drops what the URL parser would have to repair". |

---

## 🙈 Not reviewed

- **Real wallets**: how any wallet renders the SafeTx.
- **Engines** other than Chromium and Firefox.
- **The libraries**: only where Altar calls them.
- **Contracts**: the Safe's and 📛 **[ENS](https://ens.domains/)**'s; the fork
check proves the local chain carries Ethereum's bytes, not their correctness.
- **A reorged receipt**: the local chain ignores the canonical flag.
- **CI as it runs**: read only.
- Gateways serving this CID: no name carries it yet.
