# Avalanche

Avalanche is a high-performance blockchain platform offering REST APIs via the AvaCloud developer platform (formerly called the Glacier API) for querying transactions, addresses, NFTs, token balances, and cross-chain activity on the Avalanche C-Chain, P-Chain, X-Chain, and over 100 L1 subnets.

## APIs

- **Data API (Glacier)** - Query EVM balances, ERC-20/ERC-721/ERC-1155 tokens, transactions, blocks, NFT metadata, UTXOs, validators, staking rewards, and interchain messaging. Base URL: `https://glacier-api.avax.network/v1`
- **Metrics API** - Chain throughput, gas consumption, TPS, address growth, contract deployment counts, staking metrics, and rolling-window analytics.
- **RPC API** - Platform Chain remote procedure calls for UTXOs, transaction submission, validators, staking, subnet, and blockchain details.
- **Webhooks API** - Real-time push notifications for address activity, ERC-20/ERC-721 transfers, validator events, and staking activities.

## Authentication

All APIs use API key authentication via the `x-glacier-api-key` HTTP header. Keys are generated through the AvaCloud portal at https://app.avacloud.io/.

## Rate Limits

Rate limits use a Compute Unit (CU) system. Each request consumes CUs based on complexity (1–200 CUs per request). Limits apply collectively across Data and Webhooks APIs.

| Plan | Per Minute | Per Day |
|---|---|---|
| Unauthenticated | 6,000 CU | 1,200,000 CU |
| Free | 8,000 CU | 2,000,000 CU |
| Base | 10,000 CU | 3,750,000 CU |
| Growth | 14,000 CU | 11,200,000 CU |
| Pro | 20,000 CU | 25,000,000 CU |

## Links

- Portal: https://developers.avacloud.io/
- Documentation: https://build.avax.network/docs/api-reference/data-api/usage
- Swagger: https://glacier-api.avax.network/api
- SDK: https://github.com/ava-labs/avalanche-sdk-typescript
- Pricing: https://docs.avacloud.io/getting-started/plans
- Status: https://status.avax.network/
- Discord: https://discord.gg/avax
