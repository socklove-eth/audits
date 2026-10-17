# SockLove Audits

[![Release](https://img.shields.io/badge/release-1.0%20%C2%B7%20Proposal-FF3355?style=flat-square)](https://github.com/socklove-eth/.github/blob/v1.0/RELEASE.md)
[![Licence](https://img.shields.io/badge/licence-CC%20BY%204.0-666?style=flat-square)](https://github.com/socklove-eth/audits/blob/v1.0/LICENSE)

> Every page and contract, reviewed before it is placed.

---

## 📋 Reviews

Each names the release and the **CIDs** or address it covers; every one in
`1.0` is an internal security review. Report a finding:
[SECURITY.md](https://github.com/socklove-eth/.github/blob/v1.0/SECURITY.md).

| Review | Covers | CID | By |
|---|---|---|---|
| [ALTAR_1.0.md](https://github.com/socklove-eth/audits/blob/v1.0/internal/ALTAR_1.0.md) | 💒 **[Altar](https://altar.socklove.eth.limo)** `1.0` | `bafybeievodve5kgje5s4xzntroaz46w3hqyrlkmggfk3xgnuu5mckmqfoy` | 🔥 **[Sockpusher](https://etherscan.io/address/sockpusher.socklove.eth)** |
| [SIGIL_1.0.md](https://github.com/socklove-eth/audits/blob/v1.0/internal/SIGIL_1.0.md) | 👀 **[Sigil](https://sigil.socklove.eth.limo)** `1.0` | `bafybeiaccoud5ul67etgcyzmciqtabj2uha5cgrp6xr2pttmrnfindzcj4` | Sockpusher |

---

## ➕ Adding a review

`<SCOPE>` is the narrowest of
📄 **[Page](https://github.com/socklove-eth/pages/tree/v1.0)** or contract,
repository, or 🧦💜 **[SockLove](https://github.com/socklove-eth)** covering the
review: `ALTAR`, `PAGES`, `SOCKLOVE`. A review is final: a fix release gets a
new file.

- **[`internal/`](https://github.com/socklove-eth/audits/tree/v1.0/internal)**:
internal security reviews, Markdown, `<SCOPE>_<VERSION>.md`, one per scope and
release.
- **`external/`**, from the first third-party report: audit reports as
delivered, `<SCOPE>_<VERSION>_<AUTHOR>.pdf`, one per engagement; each one's
author named here, in a NOTICE, and in
[REUSE.toml](https://github.com/socklove-eth/audits/blob/v1.0/REUSE.toml).
