# Avalanche GraphQL Schema

## Overview

This conceptual GraphQL schema covers the Avalanche blockchain platform APIs, including the Glacier Data API, Metrics API, RPC API, and Webhooks API. Avalanche is a high-performance blockchain platform supporting EVM-compatible C-Chain, Platform Chain (P-Chain), Exchange Chain (X-Chain), and 100+ L1 subnets.

The schema is derived from the [Avalanche Data API (Glacier)](https://developers.avacloud.io/data-api/overview) and the [Avalanche build documentation](https://build.avax.network/docs/api-reference/data-api/usage).

## Source APIs

- **Data API (Glacier):** https://developers.avacloud.io/data-api/overview
- **Metrics API:** https://developers.avacloud.io/metrics-api/overview
- **RPC API:** https://build.avax.network/docs/api-reference/data-api/usage
- **Webhooks API:** https://developers.avacloud.io/webhooks-api/overview

## Schema File

See `avalanche-schema.graphql` for the full type definitions.

## Type Summary

| Category | Types |
|---|---|
| Node & Network | Node, NodeDetails, NodeVersion, Network, NodeInfo, InfoDetails |
| Subnet & Blockchain | Subnet, SubnetDetails, Blockchain, BlockchainDetails, Chain, ChainType |
| Block | Block, BlockDetails, BlockHash, BlockNumber |
| Transaction | Transaction, TransactionDetails, TransactionType, SignedTransaction, UnsignedTransaction |
| Asset | Asset, AssetDetails, AssetDescription, NativeToken, Token, TokenDetails |
| UTXO & Ledger | UTXO, UTXODetails, Input, Output |
| Address | Address, AddressBalance |
| Staking | Staker, StakerDetails, Delegation, DelegationDetails, Validator, ValidatorDetails, ValidatorStatus, StakingPeriod |
| Rewards | Reward, RewardDetails |
| Peers | Peer, PeerDetails |
| Health | Health, HealthCheck |
| Keystore | Keystore, Keychain |
| Platform & Token | Platform, AVAX, APIKey, RPC, WebSocket, Webhook |
| Metrics | ChainMetrics, GasMetrics, ThroughputMetrics, StakingMetrics, AddressMetrics, ContractMetrics, MetricDataPoint, MetricWindow |
| NFT | NFT, NFTMetadata, NFTCollection, NFTTransfer |
| Interchain | InterchainMessage, InterchainTransfer |
| EVM | EVMTransaction, EVMLog, EVMBlock, EVMContract |
| Pagination | PageInfo, Connection |

## Query Surface

### Queries
- `node(id: ID!)` — look up a node by ID
- `network(networkId: String!)` — fetch a network by identifier
- `block(networkId: String!, blockId: String!)` — fetch a block by hash or number
- `transaction(networkId: String!, txHash: String!)` — fetch a transaction
- `address(networkId: String!, address: String!)` — fetch address details and balances
- `asset(networkId: String!, assetId: String!)` — fetch an asset
- `validator(nodeId: String!, networkId: String!)` — fetch a validator
- `subnet(subnetId: String!)` — fetch a subnet
- `blockchain(blockchainId: String!)` — fetch a blockchain
- `utxos(networkId: String!, addresses: [String!]!)` — fetch UTXOs for addresses
- `nft(networkId: String!, address: String!, tokenId: String!)` — fetch an NFT
- `chainMetrics(networkId: String!, window: MetricWindow!)` — fetch chain metrics
- `interchainMessages(sourceNetworkId: String!, destinationNetworkId: String!)` — interchain messages

### Mutations
- `submitTransaction(networkId: String!, signedTx: String!)` — submit a signed transaction
- `createWebhook(input: CreateWebhookInput!)` — register a webhook subscription
- `deleteWebhook(webhookId: ID!)` — remove a webhook subscription
- `createAPIKey(name: String!)` — create an API key

### Subscriptions
- `blockAdded(networkId: String!)` — real-time new block events
- `transactionAdded(networkId: String!, address: String)` — real-time transaction events
- `validatorStatusChanged(nodeId: String!)` — validator state change events

## Authentication

All queries require an API key provided via the `x-glacier-api-key` HTTP header or Bearer token. Keys are provisioned through [AvaCloud](https://app.avacloud.io/).

## Rate Limits

See [rate limits documentation](https://developers.avacloud.io/data-api/rate-limits) for tier-specific request quotas. The schema supports cursor-based pagination via `pageToken` / `pageSize` arguments on all list queries.
