<h1 align="center">onchain-counter</h1>

<p align="center">
  <img src="https://res.cloudinary.com/cycy/image/upload/v1794422085/o3n28zegh1apxwqnyut5.gif" alt="Counter demo">
</p>
<p align="center">
  <b>A minimal Solana Anchor program that implements an on-chain counter </b>
</p>

<br>

[![Anchor](https://img.shields.io/badge/anchor-1.2.1-14B8A6?style=for-the-badge&logo=anchor&logoColor=white)](#what-it-does)
[![Solana](https://img.shields.io/badge/solana-4.1.2-9945FF?style=for-the-badge&logo=solana&logoColor=white)](#what-it-does)
[![Rust](https://img.shields.io/badge/rust-1.97.1-F74C00?style=for-the-badge&logo=rust&logoColor=white)](#what-it-does)
![Next.js](https://img.shields.io/badge/next.js-16.4.6-000000?style=for-the-badge&logo=next.js&logoColor=white)
![Tailwind](https://img.shields.io/badge/tailwind-3.4.17-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![Tests](https://img.shields.io/badge/tests-4%20passed-brightgreen?style=for-the-badge&logo=rust&logoColor=white)
![LiteSVM](https://img.shields.io/badge/litesvm-0.18.2-00A86B?style=for-the-badge&logo=rust&logoColor=white)
[![Phantom](https://img.shields.io/badge/phantom-AB9FF2?style=for-the-badge&logo=phantom&logoColor=white)](#wallets)
[![Backpack](https://img.shields.io/badge/backpack-000000?style=for-the-badge&logo=backpack&logoColor=white)](#wallets)
[![License: MIT](https://img.shields.io/badge/license-MIT-00A86B?style=for-the-badge)](LICENSE)

<br>

---



## Getting started

### Prerequisites


- **Rust** `1.97.1` (pinned via `rust-toolchain.toml`)
- **Solana CLI** `4.1.2`
- **Anchor CLI** `1.2.1`
- **Litesvm** `0.18.2`
- **Node.js** + **Next.js** `16.4.6` — for the frontend (`cd app && npm install`)
- **Wallet** — Phantom or Backpack, for the frontend (see [Wallets](#wallets))


### 1. Clone 
```bash
git clone git@github.com:CynthiaWahome/onchain-counter.git
cd onchain-counter
```


### 2. Build the program
```bash
anchor build
```

### 3. Run the tests
```bash
anchor test
```


### 4. Frontend — install & run
```bash
cd app
npm install
npm run dev
```

Open `http://localhost:3000` and connect a wallet (Phantom or Backpack).


### 5. Fund your wallet on devnet
```bash
solana config set --url devnet
solana airdrop 1
# or https://faucet.solana.com/ with your Phantom address
```

### 6. Deploy to devnet
```bash
cd app
cp .env.example .env
# set NEXT_PUBLIC_SOLANA_RPC_URL, NEXT_PUBLIC_PROGRAM_ID, ANCHOR_PROVIDER_URL in app/.env
anchor program deploy --provider.cluster devnet
```

Copy the printed program ID into `app/.env` as `NEXT_PUBLIC_PROGRAM_ID`.


### 7. Stream program logs
```bash
solana logs -k ~/.config/solana/id.json $NEXT_PUBLIC_PROGRAM_ID
```

> ⚠ Run step 4 (`npm run dev`) in **one terminal** — it stays running. Run steps 6–7 in **separate terminals**; they run concurrently with the dev server.

### 8. Use the counter (in the UI)
1. **Initialize** — creates the counter account, sets you as authority, `count = 0`.
2. **Increment** — adds 1 (authority-only, max 10).
3. **Close** — closes the account, returns rent.

---


## Wallets

- **Phantom**: [Create a Phantom wallet](https://phantom.app/) — install the browser extension or mobile app, then create a new wallet.
- **Backpack**: [Create a Backpack wallet](https://backpack.app/) — install Backpack, create a new wallet, and save your seed phrase.

---

## License

MIT. See [LICENSE](LICENSE).
