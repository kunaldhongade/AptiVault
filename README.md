# **AptiVault**

**Secure. Stake. Swap. All in One Vault.**

AptiVault is a **comprehensive DeFi asset management platform** built on the **Aptos blockchain**, designed to seamlessly integrate **NFTs, staking, yield farming, lending, swapping, governance, and cross-chain bridging**. Unlock the full potential of your assets through a secure and scalable ecosystem powered by Aptos.

---

## **Table of Contents**

1. [Features](#features)
2. [How It Works](#how-it-works)
3. [Getting Started](#getting-started)
4. [Smart Contracts](#smart-contracts)
5. [Usage Guide](#usage-guide)
6. [Roadmap](#roadmap)
7. [Contributing](#contributing)
8. [License](#license)

---

## **Features**

- **NFT Management:** Mint, stake, and utilize NFTs for rewards and collateral.
- **Staking & Yield Farming:** Earn passive income through single-token and liquidity pool staking.
- **DEX & Swapping:** Swap native Aptos tokens and liquidity pool (LP) tokens with real-time data insights.
- **Lending & Borrowing:** Borrow against crypto and NFT collateral with dynamic interest rates.
- **Governance DAO:** Influence platform development and protocol updates with governance tokens.
- **Cross-Chain Bridge:** Transfer assets between Aptos and other blockchains seamlessly.
- **Restaking Mechanism:** Automatically reinvest staking rewards to compound earnings.

---

## **How It Works**

AptiVault brings together all the essential DeFi tools into one easy-to-use platform:

1. **Stake Tokens & NFTs**

   - Earn governance tokens or NFT-based rewards by staking assets.
   - Restake earnings to maximize your returns with compounding rewards.

2. **Yield Farming & Liquidity Pools**

   - Add liquidity to pools and earn LP tokens along with farming incentives.

3. **Decentralized Exchange (DEX)**

   - Swap tokens directly on our DEX with advanced features like limit orders and gasless swaps.

4. **Borrow & Lend**

   - Use crypto or NFTs as collateral to unlock loans and pay with flexible interest rates.

5. **Participate in Governance**

   - Influence key decisions through DAO voting with staked governance tokens.

6. **Cross-Chain Transfers**
   - Use our bridge to transfer assets to and from other major blockchains securely.

---

## **Getting Started**

### Prerequisites

- **Node.js** >= v16.x
- **Aptos Wallet** (e.g., Petra, Martian)
- **Aptos Testnet Account**

### Installation

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/kunaldhongade/aptivault.git
   cd aptivault
   ```

2. **Install Dependencies:**

   ```bash
   npm install
   ```

3. **Start the Development Server:**

   ```bash
   npm run dev
   ```

4. **Deploy Smart Contracts on Testnet:**

   ```bash
   aptos move publish --profile testnet
   ```

5. **Connect Your Wallet:**
   - Open your Aptos wallet (e.g., Petra).
   - Add the deployed **AptiVault Testnet address** to interact with the platform.

---

## **Smart Contracts**

AptiVault leverages **Move**, the native language of Aptos, for smart contract development. Key modules include:

- **Staking Module:** Manage token and NFT staking.
- **Liquidity Pool Module:** Handle liquidity provisioning and yield farming.
- **Governance Module:** Implement DAO proposals and voting mechanics.
- **Bridge Module:** Facilitate cross-chain transfers.

Find the full smart contract code [here](./contracts/).

---

## **Usage Guide**

1. **Mint and Stake NFTs:**

   - Navigate to the NFT section and mint new NFTs or stake existing ones for rewards.

2. **Swap Tokens:**

   - Use the DEX interface to swap between Aptos-native tokens or LP tokens.

3. **Borrow Against Collateral:**

   - Head to the **Borrow & Lend** section, deposit collateral, and borrow available assets.

4. **Participate in Governance:**
   - View active proposals and vote using your governance tokens to shape the future of AptiVault.

---

## **Roadmap**

- **Phase 1:** Launch on Aptos Testnet with basic DeFi functionality.
- **Phase 2:** Integrate NFT staking and lending.
- **Phase 3:** Launch DAO governance and cross-chain bridge.
- **Phase 4:** Full platform launch on Aptos Mainnet.
- **Phase 5:** Introduce social trading and personalized yield strategies.

---

## **Contributing**

We welcome contributions from the community! Here's how you can help:

1. **Fork the repository**
2. **Create a new feature branch:**
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Commit your changes:**
   ```bash
   git commit -m "Add your feature description"
   ```
4. **Push your branch:**
   ```bash
   git push origin feature/your-feature-name
   ```
5. **Submit a pull request**

We appreciate all contributions, from code improvements to documentation updates.

---

## **License**

This project is licensed under the **MIT License**. See the [LICENSE](./LICENSE) file for details.

---

## **Conclusion**

AptiVault aims to become the **ultimate DeFi and NFT asset management platform** by combining **security, efficiency, and scalability** through Aptos. Join us on this journey to **redefine decentralized finance**!

## Create Aptos Dapp Token staking dapp Template

The Token staking dapp template provides an end-to-end Staking dapp with a beautiful pre-made UI users can quickly adjust and deploy into a live server.

## Read the Token staking dapp template docs

To get started with the Token staking dapp template and learn more about the template functionality and usage, head over to the [Token staking dapp template docs](https://learn.aptoslabs.com/en/dapp-templates/token-staking-template)

## Overview

- The token staking dapp template lets contract deployer choose an arbitrary fungible asset as the staked asset and the reward asset.
- The reward creator set in config can create reward schedules with a reward per second (RPS) rate and a duration in seconds.
  - Note: in current implementation, only 1 reward schedule is allowed. If you want to create multiple reward schedules, you need to deploy multiple stake pools.
- Users can stake their assets in the pool and claim rewards based on the reward schedule.

## Reward calculation

- We first calculate reward index, reward index is amount of reward per staked asset.
  ```
  reward index = old_index + (current_ts - last_update_ts) * rps / total_stake
  ```
- Then we calculate reward for a user
  ```
  reward = user_stake * (reward_index - user_index_at_last_claim)
  ```

## Limitation

For simplicity of the template, we didn't implement the function for the reward provider to claim back any orphaned reward after the duration has passed. There are multiple ways to implement this, the simplest way is to transfer all the reward left from reward store after the duration has passed, but this makes anyone who still has pending claim reward have no reward to claim.

## The Token Staking Template provides:

- **Stake Fungible Asset Page** - A page for anyone to stake a token
- **Claim Staking Rewards** - A component for any staker to claim the staking rewards
- **Unstake Fungible Asset** - A component for any staker to unstake
- **Create an incentivize pool of a Fungible Asset** - A component for a defined creator to create an incentivize (rewards) pool of a fungible asset

### What tools the template uses?

- React framework
- Vite development tool
- shadcn/ui + tailwind for styling
- Aptos TS SDK
- Aptos Wallet Adapter
- Node based Move commands

### What Move commands are available?

The tool utilizes [aptos-cli npm package](https://github.com/aptos-labs/aptos-cli) that lets us run Aptos CLI in a Node environment.

Some commands are built-in the template and can be ran as a npm script, for example:

- `npm run move:publish` - a command to publish the Move contract
- `npm run move:test` - a command to run Move unit tests
- `npm run move:compile` - a command to compile the Move contract
- `npm run move:upgrade` - a command to upgrade the Move contract
- `npm run dev` - a command to run the frontend locally
- `npm run deploy` - a command to deploy the dapp to Vercel

For all other available CLI commands, can run `npx aptos` and see a list of all available commands.
