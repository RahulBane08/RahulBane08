# Rahul Bane

**Smart Contract & Protocol Engineer** · Solidity · Rust · Golang · TypeScript

I build upgradeable Solidity suites that carry margin, liquidation and settlement,
and the Rust backends that keep them honest against an external order book.

**[Portfolio →](https://rahulbane.vercel.app)** · there is a record player in the corner, and it plays itself

---

### Now · Blinq

Leveraged trading on Polymarket's prediction markets. Traders open leveraged positions
on binary-outcome tokens; orders match on Polymarket's external CLOB and settle on-chain
against an LP vault that funds the position and absorbs the P&L. Deployed on Polygon,
internal beta.

- An upgradeable contract suite on OpenZeppelin v5: UUPS implementations behind ERC-1967
  proxies, plus delegatecall peers carrying settlement and emergency logic so the main
  protocol stays inside the EIP-170 code-size limit.
- A settlement money-waterfall: vault principal repaid first, shortfall socialised across
  LPs before fees, trader paid last. Beside it an EIP-712 quorum multisig with
  strictly-ascending signer recovery, and an oracle deviation-band and freshness check.
- An ERC-4626-style LP vault: virtual-offset donation protection, a utilisation-capped
  borrow facility, a utilisation-slope borrow fee, pro-rata bad-debt socialisation.
- A time-ramped Dutch-auction liquidation engine priced by single-use EIP-712 oracle
  quotes, executed by permissionless bots posting USDC for the position's ERC-1155 shares
  atomically, behind a vault-loss circuit breaker.
- A Rust workspace on Axum, Tokio and ethers-rs reconciling the on-chain ledger against
  an asynchronous off-chain order book: orchestrator state machine, reorg-safe indexer,
  CLOB executor, settlement executor, and a price oracle signing marks under GG20
  threshold ECDSA.
- Postgres leased job queues, a distributed nonce allocator letting replicas share one
  executor EOA, and a landed-transaction probe that recomputes the signed-transaction
  hash and checks the chain before retrying, so an RPC that errors after mining cannot
  cause a double spend.

### Before · Router Protocol

Cross-chain infrastructure, ending on Xplore / Open Graph Architecture, the off-chain
routing engine written in Rust.

- Built provider nodes on the external-node framework, which lets SDK-only providers
  join the Rust routing engine as dynamic nodes at runtime: Everclear, NEAR Intents
  across EVM, Solana, NEAR and Bitcoin, Chainflip as a self-run broker with shortfall
  detection and BTC PSBT generation, plus Meson and GasZip.
- Deposit-address discovery, inverting a source transaction hash back to a bridge
  deposit address: hash-format detection to prioritise chains, explorers raced in
  parallel, batched per-chain probes with error isolation, behind a cache and in-flight
  de-duplication. Every deposit-style bridge in the system shares it.
- Golang solvers, orchestrators and SDKs for interoperability on a Cosmos SDK chain,
  with distributed messaging pipelines and intent-based execution engines.
- Bitcoin execution engines: UTXO aggregation, SegWit/Bech32 signing, P2WSH multisig
  witnesses, OP_RETURN encoding, a native-node transaction streamer, and native BTC
  bridges to Ethereum, Solana and Sui with refund and execution-safety logic.
- Wrote the Node Integration Guide, published as the "Integrate into OGA" section of
  Router's developer docs.

### Also · Dfyn Network

Dfyn V2, a concentrated-liquidity and on-chain limit-order DEX: tick math, NFT liquidity
positions, quoter and router. Published
[Superimposed Liquidity](https://ethresear.ch/t/superimposed-liquidity-enhancing-concentrated-liquidity-amm-pools-with-on-chain-limit-order-book/15489)
on ethresear.ch, which layers uni-directional limit-order liquidity onto a
concentrated-liquidity curve at the same tick.

---

### Open source

**[solidity-drills](https://github.com/RahulBane08/solidity-drills)** — a pattern library
where each EVM pattern is isolated far enough to be read in one sitting: UUPS, Transparent
and EIP-1167 proxies, delegatecall peers, CREATE2, vault share accounting and rounding
policy, vesting, Merkle claims, EIP-712 signed actions, storage layout. Foundry unit,
fuzz, invariant and fork tests, with deliberately vulnerable contracts and attacker
harnesses next to them.

---

### Working areas

| | |
|---|---|
| **Contracts** | Solidity 0.8.x, Yul, UUPS and Transparent proxies, delegatecall peers, EIP-1167 clones, CREATE2, ERC-20/721/1155/4626, EIP-712/1271/1967, storage-layout discipline, gas optimisation, CEI and reentrancy |
| **Protocol design** | lending pools, collateralisation, liquidation engines, interest-rate and borrow-fee models, ERC-4626 vaults, accounting invariants, oracle deviation and freshness bands, settlement waterfalls, AMMs, concentrated liquidity, CLOB integration |
| **Rust** | Axum, Tokio, ethers-rs / alloy, sqlx, tonic / gRPC, durable leased queues, reorg-safe indexers, distributed nonce allocation, EOA broadcast with RPC failover, typed-error state machines |
| **Backend** | Golang, TypeScript / Node.js, Python, microservices, event-driven pipelines, idempotent at-least-once processing, CQRS read-models, graceful degradation |
| **Cryptography** | EIP-712/1271 typed data, quorum multisig with replay guards, ECDSA, GG20 threshold signing, Merkle proofs, SegWit P2WSH witnesses |
| **Cross-chain & Bitcoin** | interchain messaging, native asset bridges, bridge and DEX aggregation, deposit-address bridges, UTXO scripting, SegWit/Bech32, PSBT, OP_RETURN |
| **Testing** | Foundry unit, fuzz, invariant and fork suites, Hardhat, Tenderly, Slither, adversarial modelling of insolvency, oracle failure, liquidation stress and upgrade risk |
| **Infrastructure** | AWS, GCP, Docker, Kubernetes (working knowledge), CI/CD, PostgreSQL, MongoDB, Redis, Kafka, Prometheus, on-call |
| **Ecosystems** | EVM, Bitcoin, Solana, Sui, Aptos, NEAR, Cosmos SDK, Aleph Zero |

---

### Reach me

[Portfolio](https://rahulbane.vercel.app) · [LinkedIn](https://linkedin.com/in/rahulbane) · [X](https://x.com/0xImDatDude) · [rahulbane99@gmail.com](mailto:rahulbane99@gmail.com)
