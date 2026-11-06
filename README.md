# Squeek Tx Lab

squeekchain-project: f0086d9d-a399-4c35-8055-9786d69ad0e3

A Sepolia-only transaction tool for **Squeekchain**, the hamster-powered proof-of-work toychain on Ethereum.

Built by [@riyyui](https://squeekchain.com/genesis/n32chzt8) (Squeekchain Genesis member `n32chzt8`,
wallet `0x52edc297c892A9F8EE998FBb44C75980BF547740`) as a community project for the Squeekchain Genesis Build track.

## What it does

1. **Live chain state** — reads SqueekCore `state()`, SqueekMining `state()` / `checkpointStatus()` and
   SqueekNFT `totalSupply()` directly from the deployed contracts on Sepolia and shows the Squeek block
   height and progress, settled round, settled wheel work, difficulty, $SQK issued by Mining and the
   number of Squeeks minted — with the Ethereum block the values were read at.
2. **Wallet panel** — connect a browser wallet (EIP-1193); the page enforces Sepolia (chain ID 11155111,
   offering to switch/add the network) and shows the address, Sepolia ETH balance, $SQK balance and
   Squeeks held.
3. **Ping SQK** — sends `approve(your own address, 0)` to the $SQK contract: a safe first transaction
   that moves no tokens and grants no spendable allowance. The call is dry-run (`staticCall`) before the
   user is asked to sign. Sent transactions are listed in the on-page log with Blockscout links.
4. **Contract directory** — the five protocol contracts with Blockscout links.

## Safety

- Sepolia testnet only; chain guard on every wallet action. Testnet $SQK and Squeeks have no monetary value.
- The page never asks for, handles or logs a private key or seed phrase.
- Fully self-contained single HTML file: no external scripts, fonts, analytics or trackers
  (ethers.js v6.13.4 is vendored inline; Sepolia RPC endpoints are the only network calls, with fallbacks).
- All contract addresses come from the official deployment record
  (release `core-sepolia-20261103`) at https://docs.squeekchain.com/developers — nowhere else.

## Run it

Open `index.html` in any browser (or serve the folder with any static file server). No build step is
needed to use it. `src.html` is the same page with ethers.js loaded from a CDN instead of vendored;
`index.html` is generated from it by inlining `vendor/ethers.umd.min.js`.

## Contracts (Sepolia, chain ID 11155111)

| Contract | Address |
| --- | --- |
| SqueekCore | `0xFD6C166D4B8E2962E65746a13e5a0797CD4dE0c4` |
| SqueekToken ($SQK) | `0xd78a3956cF63164d1Fa1C622ad3c66623162Fa1e` |
| SqueekNFT (Squeeks) | `0xC4C7982657f00509548F3a3a41db7FA439a6856B` |
| SqueekMining | `0x2dCcB11fcC2dEfdd188555e45aCb52231e82e218` |
| SqueekStaking | `0x50fd1780526C3186A0c037c7622203bC4fb611ca` |

## License

MIT for the application code in this repository. ethers.js is © Richard Moore, MIT License.
Not affiliated with the Squeekchain team.
