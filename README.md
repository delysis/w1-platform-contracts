# W1 contract suite

> [!IMPORTANT]
> This source repository is frozen. Its accepted history and migration evidence
> now live in [`delysis/native-platform`](https://github.com/delysis/native-platform),
> and no independent feature work lands here. File defects in the
> [canonical issue tracker](https://github.com/delysis/native-platform/issues)
> and report vulnerabilities privately through
> [native-platform Security Advisories](https://github.com/delysis/native-platform/security/advisories/new).
> This repository remains readable and unarchived through the two-release
> retirement window.

This is the temporary, packet-owned executable specification accepted by
`W1-CONTRACTS`. It is not a production runtime kit and grants no authority.

`platform-contracts-v0` contains only versioned serialized data envelopes.
`platform-contract-testkit` contains test-only adapters and shared semantic
model tests. During W2 these bytes moved into `delysis/native-platform` and the
temporary external dependency pins were retired.

Lifecycle conformance also has an ownership-specific compositional surface.
Its traits are grouped by proof obligation, not by product or runtime. Every
adapter binds a compile-time product and implementation marker. Suites mint
typed private coverage evidence only after their assertions return, and a
manifest accepts only same-marker evidence whose union includes every ADR-003
invariant and each required suite exactly once. This prevents accidental
cross-implementation mixing; it cannot make a deliberately dishonest wrapper
truthful. Source review must still prove that every adapter method and shutdown
worker fact comes from the named production owner rather than shadow state.
Cross-boundary obligations such as progress-to-shutdown and
panic-to-shutdown remain bridge suites; unrelated component-local results
cannot be combined into those claims. These are test traits only, never a new
production runtime abstraction.

The durable Wave 1 snapshot remains preserved as
`delysis/w1-platform-contracts`. The repository publishes no crates and is no
longer an active dependency source. W2 imported its Git history and replaced
the temporary pins; this source repository remains frozen until the two-release
retirement criterion permits archival.

The suite deliberately contains no Tauri, product, backend, network,
filesystem, credential, clock, randomness, or live-authority implementation.

The v0 privacy-policy envelope is declarative only. It records a local-only or
explicit hosted-routing boundary, opaque provider IDs, hosted data tiers,
payload-redaction requirements, and a safe logging mode. Its pure decision
method denies invalid policies, unknown observations, and routes not expressly
allowed. It carries no credentials, provider endpoints, clients, or authority.

Every golden fixture is validated against its JSON Schema using only an
in-memory schema registry. `fixtures/v0/MANIFEST.sha256` authenticates the exact
checked-in bytes; typed round trips assert semantic JSON shape. The suite does
not claim a canonical JSON byte format.

`platform-vertical-fixtures-v0` is an additive, test-only protocol for freezing
the eighteen Wave 1 vertical rows after contract acceptance. It validates only
caller-supplied byte streams and observations, never executes replay recipes,
and cannot access files, processes, networks, models, credentials, or platform
state. Lock validation authenticates all supplied manifest bytes. Exact
prerequisites are hashed incrementally from caller-owned chunks into opaque
verification tokens, so model and audio artifacts need not be contiguous or
resident in memory; baseline and candidate comparison consume those tokens.
Candidate comparison separately authenticates and binds caller-supplied
production-tree bytes. See
[VERTICAL-FIXTURE-PROTOCOL.md](VERTICAL-FIXTURE-PROTOCOL.md). This
protocol revision contains no product fixture manifests and does not accept
`W1-VERTICALS`.
