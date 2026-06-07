# Sergei Klimov - Senior / Lead Go Blockchain Engineer

**Rio de Janeiro, Brazil, UTC-03:00**

[GitHub](https://github.com/klim0v) ·
[LinkedIn](https://www.linkedin.com/in/klim0v/) ·
[Telegram](https://t.me/klmff) ·
[X](https://x.com/0xGoDev) ·
[crazyuser704@gmail.com](mailto:crazyuser704@gmail.com)

---

## Profile

Go backend and protocol engineer — **8+ years** in service-oriented architecture, **6+ years** building blockchain infrastructure. Currently Lead Blockchain Engineer at **[NuConstruct](https://nuconstruct.xyz/)** on **TOOL Node**, a [go-ethereum](https://github.com/ethereum/go-ethereum) fork implementing TEE-attested distributed block building with 1-second sub-slots inside the 12-second Ethereum slot. Author of **[EVAA's official Go SDK](https://github.com/evaafi/evaa-go-sdk)**, former Lead Core Developer of the [Minter](https://www.minter.network/) L1, and upstream contributor to **Prysm**, **MEV-Boost**, **Cosmos IAVL**, **Tendermint tm-db**, and **btcsuite**.

**Open to:** Senior / Lead Go roles — IC or tech lead — at MEV / orderflow teams, L1 / L2 protocols, RPC and indexing infrastructure, on-chain trading desks.

---

## Core Skills

**Languages.** Go (primary, 7+ yrs), FunC, Tact, SQL.

**Ethereum.** go-ethereum (extensive forking), Prysm consensus client, MEV-Boost, builder / relay APIs, Engine API, Intel TDX / SGX, attested TLS, Automata Linux verifiable execution.

**Cosmos / Tendermint.** Tendermint Core, Cosmos SDK, ABCI, IAVL+, tm-db, DPoS, in-core AMM with order book, RLP.

**TON.** Custom FunC highload-wallet contracts, TVM gas optimisation, jetton / NFT standards, ADNL / DHT / Overlay networking, lite-server pool management, tonutils-go, [`evaa-go-sdk`](https://github.com/evaafi/evaa-go-sdk).

**Infrastructure.** gRPC, grpc-gateway, Protobuf, PostgreSQL, ClickHouse, Kafka, Redis, Kubernetes, Grafana / Prometheus.

---

## Experience

### NuConstruct — Lead Blockchain Engineer (Ethereum)
*December 2024 – present · Remote (UK) · [nuconstruct.xyz](https://nuconstruct.xyz/)*

Building **TOOL** (Trustless Orderflow Operations Layer) — a P2P, TEE-attested block-building protocol that replaces monolithic MEV-Boost builders with a distributed network of operators, introduces 1-second sub-slots inside the 12-second Ethereum slot, and provides pre-confirmation of execution before finalisation.

- **Lead engineer on the [go-ethereum](https://github.com/ethereum/go-ethereum) fork.** Designed the `tool/` package (pool, execution engine, blockchain wrapper) driving the sub-slot lifecycle, and the `relay/` package coordinating nodes and external systems.
- Built the **orderflow ingress, intermediate-state publication, and dynamic transaction-addition** mechanics enabling searchers and dApps to receive inclusion feedback every sub-slot.
- Drove the **[Automata Linux](https://blog.ata.network/verifiable-private-and-decentralized-orderflow-processing-with-automata-linux-and-tool-daf0c345e73c)** integration for verifiable execution — container / binary / config attestation, attested TLS on the TEE port, on-chain anchoring of attestations.

**Upstream contributions (Ethereum core infrastructure):**

- [`flashbots/mev-boost` #855](https://github.com/flashbots/mev-boost/pull/855) — race fix in `getPayload` version negotiation across relays (could cause a missed slot).
- [`OffchainLabs/prysm` #15871](https://github.com/OffchainLabs/prysm/pull/15871) — epoch-transition flag on head events when the first slot of an epoch is missed or reorged. *"h/t to the NuConstruct team for reporting this."*
- [`OffchainLabs/prysm` #15548](https://github.com/OffchainLabs/prysm/pull/15548) — `validateConsensus` post-state-root lookup fix. *"Reported by NuConstruct."*
- [`OffchainLabs/prysm` #15541](https://github.com/OffchainLabs/prysm/pull/15541) — payload-attribute event firing on early blocks (event feed alignment with payload-id cache).

---

### EVAA Protocol — Lending Protocol Liquidator & Official Go SDK Author (TON)
*April 2024 – March 2025 · Remote · [evaa.finance](https://evaa.finance/)*

Designed EVAA's official Go SDK and built an end-to-end production liquidator on top of it. Held a leading position on EVAA mainnet for an extended period against active competitors.

- **Authored [`evaafi/evaa-go-sdk`](https://github.com/evaafi/evaa-go-sdk)** — the protocol's official Go integration layer, published under the EVAA organisation and listed on [pkg.go.dev](https://pkg.go.dev/github.com/evaafi/evaa-go-sdk). Five packages: `config` (Main / LP / Testnet pool selection), `asset`, `price` (oracle prices and packaging), `principal` (health factor, predictions, liquidatability checks), `transaction` (supply / withdrawal / liquidation).
- **Production liquidator bot (Go).** Real-time indexer over the EVAA master via TonAPI + a redundant pool of public / private lite-clients; **multi-source price aggregation** (EVAA middleware + ICP) with per-asset medians across 4 oracles and continuous pump / dump scenario simulation to rank candidates.
- **Custom FunC highload-wallet contracts (V2 / V3 / V4)** with a 180-second message TTL and an in-payload `uniq` / "mining" field exploiting TVM message-hash ordering to gain priority during contention.
- **Multi-RPC broadcast layer** — every external message fan-outs in parallel to TonAPI + 9 independent providers (TonCenter, TonHub, EVAA RPC, GetBlock, RockX, Orbs, Ankr, Chainstack, QuickNode) to minimise inclusion latency.
- **DEX integration** for collateral disposal via [swap.coffee](https://swap.coffee/) across DeDust, STON.fi v1 / v2, TONCO, with TLB validation of every constructed swap; tsTON unstaking via the staker SC.
- Adapted the bot through the v2 protocol upgrade (one-shot bad-debt liquidation, custom-payload chaining into DeDust). *"His programming skills in Go and deep blockchain understanding helped him be the leading liquidator for a long time."* — public recommendation from a competitor.

---

### Ankr — Blockchain Engineer (Backend)
*November 2022 – December 2024 · Remote (United States) · [ankr.com](https://www.ankr.com/)*

Multi-chain Web3 API platform (45+ blockchains). Built Go backend services across **payments**, **user-manager**, **statistics**, and **accounting**.

- Implemented the **Premium plan billing** surface — per-API-credit Pay-as-You-Go and the recurring "Deal" subscription; **Stripe** (one-time and recurring) plus parallel on-chain USDT / USDC payment flows.
- Owned the **user-manager** domain — JWT-scoped private endpoints (`rpc.ankr.com/<chain>/<JWT>`), Projects, Team Accounts with RBAC, identity via MetaMask / Google / GitHub.
- Built the **usage-statistics pipeline** powering per-project request, latency, and cost dashboards — Kafka ingest, ClickHouse aggregation, PostgreSQL state, Redis hot paths, Grafana / Prometheus.

---

### Minter Network — Lead Golang Blockchain Core Developer
*September 2019 – November 2022 · Remote (UK) · [github.com/MinterTeam](https://github.com/MinterTeam)*

L1 DeFi blockchain on Tendermint with DPoS, in-core AMM with order book, and ETH / BSC bridges.

- Lead developer of **[`minter-go-node`](https://github.com/MinterTeam/minter-go-node)**, the official Go implementation. Owned the Tendermint integration, IAVL+ state tree, transaction execution layer, and Minter 2's in-core **AMM with Order Book (AMMOB)**.
- Owned **[`node-grpc-gateway`](https://github.com/MinterTeam/node-grpc-gateway)** — single Protobuf → gRPC + REST + WebSocket + OpenAPI / Swagger — and **[`minter-go-sdk v2`](https://github.com/MinterTeam/minter-go-sdk)**.

**Upstream fixes shipped with `@klim0v` attribution:**

- [`cosmos/iavl` #324](https://github.com/cosmos/iavl/pull/324) — orphan-node cleanup in `DeleteVersions` + new `DeleteVersionsRange` API. Released in [IAVL v0.14.3](https://github.com/cosmos/iavl/blob/v0.14.3/CHANGELOG.md).
- [`tendermint/tm-db` #134](https://github.com/tendermint/tm-db/pull/134) — bounded GoLevelDB iterator range, measurable iteration speedup during IAVL pruning. Released in [tm-db v0.6.3](https://github.com/tendermint/tm-db/blob/v0.6.3/CHANGELOG.md).
- [`btcsuite/btcutil` #161](https://github.com/btcsuite/btcutil/pull/161) — BIP-32 leading-zero `ser256(p)` derivation fix + regression test.

---

### Additional experience (2016 – 2019)

**Dr.Cash** — Go microservices for an international CPA network (Go, gRPC, NATS, ClickHouse, Kubernetes).
**Wormsoft** — Go / PHP backend, REST APIs, GitLab-webhook deploy service.
**Vitbiomed** — Bitrix → Laravel migration.
**Darvin Studio / Be on TOP** — Symfony CMS, blogs and online stores.

---

## Recognition

- **TON Smart Challenge #2 — 1st place out of 181 participants** (FunC, five gas-optimised smart-contract tasks).
- TON Smart Challenge #5 and TON Tact Challenge — participant.

---

## Speaking, Writing & Teaching

- **[GolangConf 2020](https://golangconf.ru/2020/abstracts/6761)** — *"Tools for Generating API Code and Documentation"*: comparison of `swagger-codegen`, `go-swagger`, `swaggo/swag`, and `grpc-gateway`. [Video](https://www.youtube.com/watch?v=Q9x1FVPDGu4).
- **Netology — Golang Course Teacher** (Oct 2020 – Feb 2021). [Sample lesson](https://youtu.be/wTbH3FpxI0o).
- **Minter Demo Day 2019** — Minter architecture overview. [Video](https://youtu.be/7bZREmkcpiY).
- **Articles**: [Medium](https://medium.com/@klim0v) · [Habr](https://habr.com/ru/users/klim0v/articles/)
---

## Education

**Vladimir State University** — B.Sc. Applied Mathematics & Computer Science, 2013 – 2017.

---

## Languages

Russian (native) · English (professional working) · Portuguese (basic).
