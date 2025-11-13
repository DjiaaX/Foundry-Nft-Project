# Foundry NFT Project

Minimal README for a Solidity NFT project using Foundry (forge, cast, anvil).

## Table of contents
- What this is
- Requirements
- Quick start
- Common commands
- Testing & debugging
- Deploying
- Verifying on Etherscan
- Contracts (overview)
- Security
- Contributing & license

## What this is
A small NFT project built with Solidity and Foundry. Contains:
- ERC-721 NFT contract(s)
- deployment scripts (forge script)
- unit tests (forge test)
- optional mocks for local development

## Requirements
- Foundry (forge, cast, anvil). Install with:
```bash
curl -L https://foundry.paradigm.xyz | bash
foundryup
```
- Node.js (optional, for frontends/scripts)
- A JSON-RPC provider URL (Infura/Alchemy) and Etherscan API key for verification
- PRIVATE_KEY for deployment (use a throwaway/test key; never commit)

## Quick start
1. Clone and open:
```bash
git clone <repo-url>
cd Foundry-NFT-Project
```
2. Install/update Foundry:
```bash
foundryup
```
3. Build:
```bash
forge build
```

## Common commands
- Run tests:
```bash
forge test
```
- Verbose test output:
```bash
forge test -vv
```
- Run a single contract/test:
```bash
forge test --match-contract MyContractTest
```
- Start a local chain (Anvil):
```bash
anvil
# or run in background: anvil > /dev/null 2>&1 &
```
- Run a deploy script locally (broadcast to Anvil):
```bash
forge script script/Deploy.s.sol:DeployScript --rpc-url http://127.0.0.1:8545 --private-key <PRIVATE_KEY> --broadcast
```

## Environment variables
Create a .env (do NOT commit) or export variables:
- PRIVATE_KEY — deployer's private key
- RPC_URL (or named per network) — JSON‑RPC endpoint
- ETHERSCAN_API_KEY — for contract verification

Example (bash):
```bash
export PRIVATE_KEY="0x..."
export RPC_URL="https://eth-goerli.alchemyapi.io/v2/..."
export ETHERSCAN_API_KEY="..."
```

## Deploying to a testnet / mainnet
Use a forge script and broadcast:
```bash
forge script script/Deploy.s.sol:DeployScript --rpc-url $RPC_URL --private-key $PRIVATE_KEY --broadcast
```
You can add `--verify` or run etherscan verification after deployment (see below).

## Verifying on Etherscan
After deployment, verify using:
```bash
forge verify-contract --chain-id <CHAIN_ID> <CONTRACT_ADDRESS> src/YourContract.sol:YourContract $ETHERSCAN_API_KEY
```
Or use `forge create --verify` flags depending on project setup.

## Testing tips
- Use cheatcodes in tests (vm) for forking and state manipulation.
- Fuzz inputs with `forge test --fuzz-limit`.
- Use Foundry snapshots and gas reports:
```bash
forge test --gas-report
```

## Contracts (typical layout)
- src/
    - NFT.sol — ERC-721 implementation (minting, metadata)
    - NFTMarketplace.sol — optional listing/auction logic
    - MockERC20.sol — test token for marketplace flows
- script/
    - Deploy.s.sol — deployment script(s)
- test/
    - NFT.t.sol — unit tests
    - Marketplace.t.sol — integration tests

Replace filenames/names with your actual contracts.

## Security
- Follow best practices: access control, reentrancy guards, safe math where needed.
- Run static analysis and slither where possible.
- Review minting/payment logic and metadata sources.

## Contributing
- Open issues for bugs/feature requests.
- Send PRs with clear descriptions and tests.
- Keep changes small and focused.

## License
MIT — see LICENSE file.

(generate by AI XD)