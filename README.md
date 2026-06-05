# AT Protocol (at-protocol)

The AT Protocol (atproto) is an open, federated networking protocol for
social applications, originally developed by Bluesky Social PBC and the
Bluesky team. It defines a decentralized architecture where user identity
and data are portable across providers, anchored in DIDs, signed records,
and content-addressed storage. The protocol is composed of independently
operable services — Personal Data Servers (PDS), Relays (firehose
aggregators), and AppViews (read-side indexers) — that communicate using
XRPC and exchange records described by Lexicon schemas. Bluesky (bsky.app)
is the reference application built on AT Protocol, but the protocol is
designed for any social or social-adjacent application that wants
user-owned identity, portable data, and an open federation model. Official
and community SDKs exist for TypeScript, Go, Python, Rust, Dart, Swift,
C#/.NET, Ruby, PHP, and more, and the full lexicon, network topology, and
reference implementations are open source.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/at-protocol/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/at-protocol/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Provider
- **Access:** Public

## Tags

- AT Protocol
- atproto
- Bluesky
- Federation
- Decentralized Social
- Social Networking
- DID
- Lexicon
- XRPC
- PDS
- Relay
- AppView
- Open Protocol

## Timestamps

- **Created:** 2026-05-23
- **Modified:** 2026-05-29

## APIs

### AT Protocol XRPC API

XRPC is the AT Protocol's HTTP-based remote procedure call layer. All
protocol interactions — querying records, writing records, subscribing
to streams, resolving identity, moderating content — are exposed as
XRPC methods defined in Lexicon schemas. PDS, Relay, and AppView
services all speak XRPC, so the same client library can be pointed at
different network roles. The HTTP surface uses /xrpc/{nsid} paths and
JSON request/response bodies (with optional CBOR for record content).

- **Human URL:** [https://atproto.com/specs/xrpc](https://atproto.com/specs/xrpc)
- **Base URL:** `https://atproto.com/xrpc`

#### Tags

- XRPC
- RPC
- HTTP
- JSON
- Protocol Surface

#### Properties

- [Specification](https://atproto.com/specs/xrpc)
- [Documentation](https://atproto.com/guides/glossary)
- [GitHub Organization](https://github.com/bluesky-social)
- [Postman Collection](collections/at-protocol.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/at-protocol.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### AT Protocol Lexicon Schemas

Lexicon is the schema definition language for AT Protocol. Every
record type, XRPC method, and event subscription on the network is
described by a Lexicon document, which acts as both contract and code
generation source for client libraries. Bluesky publishes the
app.bsky.* and com.atproto.* lexicons that power the reference
Bluesky application; third parties define their own NSIDs to ship
independent applications on the same network.

- **Human URL:** [https://atproto.com/guides/lexicon](https://atproto.com/guides/lexicon)
- **Base URL:** `https://atproto.com/lexicons`

#### Tags

- Lexicon
- Schema
- NSID
- Record Types

#### Properties

- [Documentation](https://atproto.com/guides/lexicon)
- [Specification](https://atproto.com/specs/lexicon)
- [Repository](https://github.com/bluesky-social/atproto/tree/main/lexicons)
- [Postman Collection](collections/at-protocol.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/at-protocol.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Personal Data Server (PDS) API

The PDS hosts a user's repository of signed records and exposes the
com.atproto.* XRPC methods for account creation, authentication,
record CRUD, blob upload, and repository sync. A PDS is the home
server for an actor; users can migrate their account (and full
record history) between PDS hosts while keeping the same DID.

- **Human URL:** [https://atproto.com/guides/self-hosting](https://atproto.com/guides/self-hosting)
- **Base URL:** `https://atproto.com/xrpc/com.atproto`

#### Tags

- PDS
- Personal Data Server
- Repository
- Sync
- Self-Hosting

#### Properties

- [Documentation](https://atproto.com/guides/self-hosting)
- [Specification](https://atproto.com/specs/repository)
- [Reference](https://github.com/bluesky-social/atproto/tree/main/packages/pds)
- [Postman Collection](collections/at-protocol.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/at-protocol.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### AT Protocol Relay & Firehose

The Relay aggregates the com.atproto.sync.subscribeRepos firehose
across PDS hosts and re-broadcasts the combined event stream over
WebSocket. AppViews and indexers subscribe to a Relay to get a
near-real-time view of every public record written on the network
without polling individual PDS instances.

- **Human URL:** [https://atproto.com/guides/glossary](https://atproto.com/guides/glossary)
- **Base URL:** `wss://bsky.network`

#### Tags

- Relay
- Firehose
- WebSocket
- Streaming
- Sync

#### Properties

- [Specification](https://atproto.com/specs/sync)
- [Reference](https://github.com/bluesky-social/indigo)
- [AsyncAPI](https://raw.githubusercontent.com/api-evangelist/at-protocol/refs/heads/main/asyncapi/at-protocol-asyncapi.yml) — [AsyncAPI Specification](https://www.asyncapi.com/docs/reference/specification/latest)
- [Postman Collection](collections/at-protocol.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/at-protocol.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Bluesky AppView API

The Bluesky AppView indexes the firehose and exposes the app.bsky.*
XRPC methods that the Bluesky client (and any compatible client)
uses to render timelines, threads, profiles, notifications, search,
and graph data. It is the reference AppView for the app.bsky lexicon
family and the primary read API for Bluesky applications.

- **Human URL:** [https://docs.bsky.app/](https://docs.bsky.app/)
- **Base URL:** `https://public.api.bsky.app/xrpc`

#### Tags

- AppView
- Bluesky
- Timeline
- Feed
- Graph
- Notifications

#### Properties

- [Documentation](https://docs.bsky.app/)
- [API Reference](https://docs.bsky.app/docs/category/http-reference)
- [Lexicons](https://github.com/bluesky-social/atproto/tree/main/lexicons/app/bsky)
- [Postman Collection](collections/at-protocol.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/at-protocol.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### AT Protocol Identity (DID & Handles)

Identity in AT Protocol is anchored in DIDs (did:plc or did:web),
with human-readable handles resolved through DNS TXT records or
well-known HTTP endpoints. The protocol specifies how DIDs map to
PDS endpoints, signing keys, and rotation, allowing users to keep
a stable identity while changing handles or migrating providers.

- **Human URL:** [https://atproto.com/specs/did](https://atproto.com/specs/did)
- **Base URL:** `https://plc.directory`

#### Tags

- Identity
- DID
- did:plc
- Handles
- DNS

#### Properties

- [Specification](https://atproto.com/specs/did)
- [Specification](https://atproto.com/specs/handle)
- [Service](https://plc.directory/)
- [Postman Collection](collections/at-protocol.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/at-protocol.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Website](https://atproto.com/)
- [Documentation](https://atproto.com/guides/overview)
- [Specifications](https://atproto.com/specs/atp)
- [S D Ks](https://atproto.com/sdks)
- [GitHub Organization](https://github.com/bluesky-social)
- [Reference Implementation](https://github.com/bluesky-social/atproto)
- [Go Implementation](https://github.com/bluesky-social/indigo)
- [Bluesky](https://bsky.app/)
- [Bluesky Docs](https://docs.bsky.app/)
- [Blog](https://bsky.social/about/blog)
- [Cookbook](https://github.com/bluesky-social/cookbook)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
