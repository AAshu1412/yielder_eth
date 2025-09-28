# Yielder Protocol: An Autonomous Cross-DEX Yield Aggregator on Ethereum Sepolia

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Platform: Ethereum Sepolia](https://img.shields.io/badge/Platform-Ethereum%20Sepolia-blue.svg)
![Language: Solidity](https://img.shields.io/badge/Language-Solidity-purple.svg)

**Yielder** is an autonomous yield aggregator on **Ethereum Sepolia** that automatically finds and stakes your assets in the most profitable liquidity pools across multiple DEXs, ensuring you always get the best returns with minimal effort.

**Website:** [`https://yielder_aykansal.ar.io/`](https://yielder_aykansal.ar.io/)

---

## Table of Contents

- [The Problem: Yield Farming is Hard](#the-problem-yield-farming-is-hard)
- [The Solution: Yielder Makes it Easy](#the-solution-yielder-makes-it-easy)
- [How It Works: The Yielder Lifecycle](#how-it-works-the-yielder-lifecycle)
  - [1. On-Chain Analysis & Pool Discovery](#1-on-chain-analysis--pool-discovery)
  - [2. Automated Liquidity Provision](#2-automated-liquidity-provision)
  - [3. YLP Token Abstraction](#3-ylp-token-abstraction)
  - [4. Continuous Optimization & Rebalancing](#4-continuous-optimization--rebalancing)
  - [5. Seamless Redemption](#5-seamless-redemption)
- [The Problem: Yield Farming is Hard](#the-problem-yield-farming-is-hard)
- [The Solution: Yielder Makes it Easy](#the-solution-yielder-makes-it-easy)
- [How It Works: The Yielder Lifecycle](#how-it-works-the-yielder-lifecycle)
  - [1. On-Chain Analysis & Pool Discovery](#1-on-chain-analysis--pool-discovery)
  - [2. Automated Liquidity Provision](#2-automated-liquidity-provision)
  - [3. YLP Token Abstraction](#3-ylp-token-abstraction)
  - [4. Continuous Optimization & Rebalancing](#4-continuous-optimization--rebalancing)
  - [5. Seamless Redemption](#5-seamless-redemption)
- [Protocol Architecture](#protocol-architecture)
  - [Key Processes](#key-processes)
  - [Core Assets (Yielder Token Suite)](#core-assets-yielder-token-suite)
  - [Key Processes](#key-processes)
  - [Core Assets (Yielder Token Suite)](#core-assets-yielder-token-suite)
  - [Integrated Liquidity Pools](#integrated-liquidity-pools)
- [Getting Started: A User's Guide](#getting-started-a-users-guide)
  - [Step 1: Acquire Test Tokens](#step-1-acquire-test-tokens)
  - [Step 2: Find the Best Pool to Stake In](#step-2-find-the-best-pool-to-stake-in)
  - [Step 3: Stake Your Tokens](#step-3-stake-your-tokens)
  - [Step 4: Withdraw Your Assets](#step-4-withdraw-your-assets)
- [DEX Pools MCP Server](#dex-pools-mcp-server)
  - [Features](#features)
  - [Installation & Usage](#installation--usage)
  - [MCP Client Integration](#mcp-client-integration)
  - [Available Tools](#available-tools)
- [Getting Started: A User's Guide](#getting-started-a-users-guide)
  - [Step 1: Acquire Test Tokens](#step-1-acquire-test-tokens)
  - [Step 2: Find the Best Pool to Stake In](#step-2-find-the-best-pool-to-stake-in)
  - [Step 3: Stake Your Tokens](#step-3-stake-your-tokens)
  - [Step 4: Withdraw Your Assets](#step-4-withdraw-your-assets)
- [DEX Pools MCP Server](#dex-pools-mcp-server)
  - [Features](#features)
  - [Installation & Usage](#installation--usage)
  - [MCP Client Integration](#mcp-client-integration)
  - [Available Tools](#available-tools)
- [Development & Setup](#development--setup)
- [License](#license)
- [License](#license)

---

## The Problem: Yield Farming is Hard

Providing liquidity to earn yield can be a complicated and expensive process. Yielder is designed to fix these common challenges:

* **Constant Monitoring:** You have to constantly watch the markets to find the best returns.
* **Time-Consuming:** Frequently moving your funds between pools to chase better yields is tedious.
* **High Complexity:** Managing investments across many different platforms (e.g., Uniswap, SushiSwap) is confusing and difficult.

## The Solution: Yielder Makes it Easy

Yielder is an automated system that handles the entire yield farming process for you:

* **Smart Analysis:** Yielder constantly analyzes performance metrics like APR, TVL, and Swap Fees to find the most profitable liquidity pools across supported DEXs.
* **Automatic Staking:** Once the best pool is found, the protocol automatically deploys your assets into it.
* **Dynamic Rebalancing:** Yielder continuously monitors the market. If a more profitable opportunity appears, it automatically moves your funds to the better pool.
* **Simple Portfolio Management:** Your entire position is represented by a single token: the **Yielder LP Token (YLP)**. This simplifies portfolio management down to tracking a single asset.
* **Shared Costs:** By managing assets collectively, the protocol socializes transaction costs, leading to greater capital efficiency for everyone involved.
## The Problem: Yield Farming is Hard

Providing liquidity to earn yield can be a complicated and expensive process. Yielder is designed to fix these common challenges:

* **Constant Monitoring:** You have to constantly watch the markets to find the best returns.
* **Time-Consuming:** Frequently moving your funds between pools to chase better yields is tedious.
* **High Complexity:** Managing investments across many different platforms (e.g., Uniswap, SushiSwap) is confusing and difficult.

## The Solution: Yielder Makes it Easy

Yielder is an automated system that handles the entire yield farming process for you:

* **Smart Analysis:** Yielder constantly analyzes performance metrics like APR, TVL, and Swap Fees to find the most profitable liquidity pools across supported DEXs.
* **Automatic Staking:** Once the best pool is found, the protocol automatically deploys your assets into it.
* **Dynamic Rebalancing:** Yielder continuously monitors the market. If a more profitable opportunity appears, it automatically moves your funds to the better pool.
* **Simple Portfolio Management:** Your entire position is represented by a single token: the **Yielder LP Token (YLP)**. This simplifies portfolio management down to tracking a single asset.
* **Shared Costs:** By managing assets collectively, the protocol socializes transaction costs, leading to greater capital efficiency for everyone involved.

---

## How It Works: The Yielder Lifecycle

The Yielder protocol automates the entire yield farming lifecycle through a sophisticated, multi-stage process designed to be completely hands-off for the user after the initial deposit.
## How It Works: The Yielder Lifecycle

The Yielder protocol automates the entire yield farming lifecycle through a sophisticated, multi-stage process designed to be completely hands-off for the user after the initial deposit.

![Yielder Workflow](./processes/yirlder.png)

### 1. On-Chain Analysis & Pool Discovery 📈

Yielder continuously monitors all supported liquidity pools to identify the most profitable opportunities.

* **On-Demand Analysis:** A user can call the `Best-Stake` handler with a token pair to get an immediate recommendation for the best pool.
* **Continuous Background Monitoring:** An automated cron job runs every two minutes, calling the `cronnn` handler to fetch the latest data for all supported pools, ensuring the system's information is always up-to-date.
* **Metric Calculation:** It calculates critical performance indicators for each pool in real-time, including Total Value Locked (TVL), 24-Hour Volume, and Annual Percentage Rate (APR).

### 2. Automated Liquidity Provision 🔗

Once a user decides to stake, Yielder acts as a proxy to execute the transaction on their behalf.

* The protocol takes the user's deposited tokens and programmatically calls the `AddLiquidity` function on the optimal DEX pool (either on Uniswap V3 or SushiSwap).
* The DEX pool then mints its native LP token and sends it directly to the Yielder process, which holds it in custody within its treasury.

### 3. YLP Token Abstraction 🎟️

In exchange for the deposited assets, Yielder mints and distributes its own derivative token, the **`YLP` (Yielder LP Token)**, to the user.

* The `YLP` token serves as a liquid receipt for the user's stake.
* This powerfully abstracts the investment—the user's entire, potentially complex position is represented by this single `YLP` token, drastically simplifying portfolio management.

### 4. Continuous Optimization & Rebalancing 🤖

The true power of Yielder lies in its autonomous optimization engine.

* The `Auto-Yield-Optimizer` handler periodically analyzes the fresh market data.
* It compares the APR of the pool currently holding a user's funds against all other available pools for the same token pair.
* If the optimizer finds a new pool with a significantly higher APR, it automatically triggers a rebalance—withdrawing liquidity from the underperforming pool and redeploying it into the new, higher-yielding one.

### 5. Seamless Redemption 📤

When a user wants to exit their position, the process is as simple as the deposit.

* The user calls the `burn` handler, sending their `YLP` tokens back to the Yielder process.
* Yielder calculates the user's proportional share of the underlying assets, withdraws them from the appropriate DEX pool(s), and transfers the base tokens directly back to the user's wallet.


### 1. On-Chain Analysis & Pool Discovery 📈

Yielder continuously monitors all supported liquidity pools to identify the most profitable opportunities.

* **On-Demand Analysis:** A user can call the `Best-Stake` handler with a token pair to get an immediate recommendation for the best pool.
* **Continuous Background Monitoring:** An automated cron job runs every two minutes, calling the `cronnn` handler to fetch the latest data for all supported pools, ensuring the system's information is always up-to-date.
* **Metric Calculation:** It calculates critical performance indicators for each pool in real-time, including Total Value Locked (TVL), 24-Hour Volume, and Annual Percentage Rate (APR).

### 2. Automated Liquidity Provision 🔗

Once a user decides to stake, Yielder acts as a proxy to execute the transaction on their behalf.

* The protocol takes the user's deposited tokens and programmatically calls the `AddLiquidity` function on the optimal DEX pool (either on Uniswap V3 or SushiSwap).
* The DEX pool then mints its native LP token and sends it directly to the Yielder process, which holds it in custody within its treasury.

### 3. YLP Token Abstraction 🎟️

In exchange for the deposited assets, Yielder mints and distributes its own derivative token, the **`YLP` (Yielder LP Token)**, to the user.

* The `YLP` token serves as a liquid receipt for the user's stake.
* This powerfully abstracts the investment—the user's entire, potentially complex position is represented by this single `YLP` token, drastically simplifying portfolio management.

### 4. Continuous Optimization & Rebalancing 🤖

The true power of Yielder lies in its autonomous optimization engine.

* The `Auto-Yield-Optimizer` handler periodically analyzes the fresh market data.
* It compares the APR of the pool currently holding a user's funds against all other available pools for the same token pair.
* If the optimizer finds a new pool with a significantly higher APR, it automatically triggers a rebalance—withdrawing liquidity from the underperforming pool and redeploying it into the new, higher-yielding one.

### 5. Seamless Redemption 📤

When a user wants to exit their position, the process is as simple as the deposit.

* The user calls the `burn` handler, sending their `YLP` tokens back to the Yielder process.
* Yielder calculates the user's proportional share of the underlying assets, withdraws them from the appropriate DEX pool(s), and transfers the base tokens directly back to the user's wallet.

---

## Protocol Architecture

### Key Processes

* **Main Yielder Contract:** The central smart contract that contains all protocol logic and also serves as the `YLP` token contract.
    * **Contract Address:** `0x1234567890123456789012345678901234567890`
* **Cron Job Contract:** A utility contract that calls the main contract's functions every two minutes to refresh data.
    * **Contract Address:** `0x0987654321098765432109876543210987654321`

### Core Assets (Yielder Token Suite)

These are test tokens used within the Yielder ecosystem for providing liquidity on Ethereum Sepolia testnet.

* **USDC:** `0x94a9D9AC8a22534E3FaCa9F4e7F2E2cfB85B5b29`
* **USDT:** `0x7169D38820dfd117C3FA1f22a697dBA58d90BA06`
* **DAI:** `0xFF34B3d4Aee8ddCd6F9AFFFB6Fe49bD371b8a357`
* **Cron Job Process:** A utility process that calls the main process's handlers every two minutes to refresh data.
    * **Process ID:** `pim8QULY_SxUwx8yMarH4O4NwiWtP4awcgyGhgsE-FA`

### Core Assets (Yielder Token Suite)

These are test tokens used within the Yielder ecosystem for providing liquidity on Ethereum Sepolia testnet.

* **USDC:** `0x94a9D9AC8a22534E3FaCa9F4e7F2E2cfB85B5b29`
* **USDT:** `0x7169D38820dfd117C3FA1f22a697dBA58d90BA06`
* **DAI:** `0xFF34B3d4Aee8ddCd6F9AFFFB6Fe49bD371b8a357`

### Integrated Liquidity Pools

Yielder actively monitors and manages liquidity across the following live pools on Uniswap V3 and SushiSwap.

| Token Pair  | DEX       | Pool Address & Link                                                                                                 |
| :---------- | :-------- | :------------------------------------------------------------------------------------------------------------------ |
| **USDC / WETH** | Uniswap V3 | [`0x88e6A0c2dDD26FEEb64F039a2c41296FcB3f5640`](https://app.uniswap.org/pools/0x88e6A0c2dDD26FEEb64F039a2c41296FcB3f5640) |
| **USDT / WETH** | Uniswap V3 | [`0x11b815efB8f581194ae79006d24E0d814B7697F6`](https://app.uniswap.org/pools/0x11b815efB8f581194ae79006d24E0d814B7697F6)   |
| **DAI / WETH** | Uniswap V3 | [`0xC2e9F25E6252C396f0D2B7B0C4C3C4C3C4C3C4C3`](https://app.uniswap.org/pools/0xC2e9F25E6252C396f0D2B7B0C4C3C4C3C4C3C4C3)   |
| **USDC / USDT** | SushiSwap | [`0x3416cF6C708Da44DB2624D63ea0AAef7113527C6`](https://app.sushi.com/pools/0x3416cF6C708Da44DB2624D63ea0AAef7113527C6)                         |
| **WETH / WBTC** | SushiSwap | [`0x4585FE77225b41b697C938B018E2Ac67Ac5a20c0`](https://app.sushi.com/pools/0x4585FE77225b41b697C938B018E2Ac67Ac5a20c0)                         |
| **USDC / DAI** | SushiSwap | [`0x5777d92f208679DB4b9778590Fa3CAB3aC9e2168`](https://app.sushi.com/pools/0x5777d92f208679DB4b9778590Fa3CAB3aC9e2168)                         |

---

## Getting Started: A User's Guide

### Step 1: Acquire Test Tokens

Use the built-in faucet functions to get test tokens sent directly to your wallet.
* **Get 10 USDC:**
    ```solidity
    yielderContract.requestUSDC(10);
    ```
* **Get 20 USDT:**
    ```solidity
    yielderContract.requestUSDT(20);
    ```
* **Get 30 DAI:**
    ```solidity
    yielderContract.requestDAI(30);
    ```

### Step 2: Find the Best Pool to Stake In 🔍
Use the `Best-Stake` handler to perform a live analysis and find the most profitable pool for a given pair.

```bash
Send({ 
    Target = "SpJdYt1_CdMG0W5JjDVYfu-tJNGB2bXC6usBSyrQAys",
    Action = "Best-Stake",
    TokenX = "_IxG5qxfgSBBj1wH7BL0j1vkihOcfx2ntXS19NZjDFU", -- YT1
    TokenY = "Zg8ihIkD2Tpm2E0vRbJSD0J3Jb3dqK8XUZ4OlOZ9kcc"  -- YT2
Yielder actively monitors and manages liquidity across the following live pools on Uniswap V3 and SushiSwap.

| Token Pair  | DEX       | Pool Address & Link                                                                                                 |
| :---------- | :-------- | :------------------------------------------------------------------------------------------------------------------ |
| **USDC / WETH** | Uniswap V3 | [`0x88e6A0c2dDD26FEEb64F039a2c41296FcB3f5640`](https://app.uniswap.org/pools/0x88e6A0c2dDD26FEEb64F039a2c41296FcB3f5640) |
| **USDT / WETH** | Uniswap V3 | [`0x11b815efB8f581194ae79006d24E0d814B7697F6`](https://app.uniswap.org/pools/0x11b815efB8f581194ae79006d24E0d814B7697F6)   |
| **DAI / WETH** | Uniswap V3 | [`0xC2e9F25E6252C396f0D2B7B0C4C3C4C3C4C3C4C3`](https://app.uniswap.org/pools/0xC2e9F25E6252C396f0D2B7B0C4C3C4C3C4C3C4C3)   |
| **USDC / USDT** | SushiSwap | [`0x3416cF6C708Da44DB2624D63ea0AAef7113527C6`](https://app.sushi.com/pools/0x3416cF6C708Da44DB2624D63ea0AAef7113527C6)                         |
| **WETH / WBTC** | SushiSwap | [`0x4585FE77225b41b697C938B018E2Ac67Ac5a20c0`](https://app.sushi.com/pools/0x4585FE77225b41b697C938B018E2Ac67Ac5a20c0)                         |
| **USDC / DAI** | SushiSwap | [`0x5777d92f208679DB4b9778590Fa3CAB3aC9e2168`](https://app.sushi.com/pools/0x5777d92f208679DB4b9778590Fa3CAB3aC9e2168)                         |

---

## Getting Started: A User's Guide

### Step 1: Acquire Test Tokens

Use the built-in faucet functions to get test tokens sent directly to your wallet.
* **Get 10 USDC:**
    ```solidity
    yielderContract.requestUSDC(10);
    ```
* **Get 20 USDT:**
    ```solidity
    yielderContract.requestUSDT(20);
    ```
* **Get 30 DAI:**
    ```solidity
    yielderContract.requestDAI(30);
    ```

### Step 2: Find the Best Pool to Stake In 🔍
Use the `findBestPool` function to perform a live analysis and find the most profitable pool for a given pair.

```solidity
yielderContract.findBestPool(
    0x94a9D9AC8a22534E3FaCa9F4e7F2E2cfB85B5b29, // USDC
    0x7169D38820dfd117C3FA1f22a697dBA58d90BA06  // USDT
);
```

### Step 3: Stake Your Tokens 🔗
First, transfer your tokens to the Yielder Process. Then, call the `Stake-User-Token` handler. The protocol will automatically stake them in the optimal pool and mint `YLP` tokens back to you.

```bash
Send({ 
    Target = "SpJdYt1_CdMG0W5JjDVYfu-tJNGB2bXC6usBSyrQAys",
    Action = "Stake-User-Token", 
    Pool = "Q9uyLNaNvuFHvNrQQZ_XuOrRZ6OEE0KqSEPJJj8Z4Ys", -- Example Pool ID from Step 2
    User = "YOUR_WALLET_ADDRESS",
    TokenXAddress ="_IxG5qxfgSBBj1wH7BL0j1vkihOcfx2ntXS19NZjDFU", 
    TokenXQuantity = "2000000000000",  
    TokenYAddress ="Zg8ihIkD2Tpm2E0vRbJSD0J3Jb3dqK8XUZ4OlOZ9kcc", 
    TokenYQuantity = "2727272727272"
### Step 3: Stake Your Tokens 🔗
First, approve the Yielder contract to spend your tokens. Then, call the `stakeTokens` function. The protocol will automatically stake them in the optimal pool and mint `YLP` tokens back to you.

```solidity
// First approve the contract
IERC20(0x94a9D9AC8a22534E3FaCa9F4e7F2E2cfB85B5b29).approve(
    yielderContractAddress, 
    2000000000000
);

// Then stake
yielderContract.stakeTokens(
    0x3416cF6C708Da44DB2624D63ea0AAef7113527C6, // Pool Address
    0x94a9D9AC8a22534E3FaCa9F4e7F2E2cfB85B5b29, // USDC
    0x7169D38820dfd117C3FA1f22a697dBA58d90BA06, // USDT
    2000000000000,  // USDC Amount
    2727272727272   // USDT Amount
);
```
### Step 4: Withdraw Your Assets 📤
To exit your position, simply call the `burn` function with your `YLP` tokens. The protocol will automatically withdraw the underlying assets from the DEX and return them to your wallet.

```solidity
yielderContract.burn(ylpTokenAmount);
```

---

## DEX Pools MCP Server 🖥️
A companion Model Context Protocol (MCP) server that provides real-time, structured access to DEX pool data from the Yielder protocol.

### Features
* **`get_all_pools`**: Retrieve all monitored DEX pools with detailed information.
* Supports both Uniswap V3 and SushiSwap DEX protocols.
* Provides TVL, APR, fees, token details, and contract addresses.
* Fetches real-time data directly from Ethereum Sepolia testnet.

### Installation & Usage
1.  **Clone the repository**
2.  **Install dependencies:**
    ```bash
    pnpm install
    ```
3.  **Build the project:**
    ```bash
    pnpm run build
    ```
4.  **Run the server:**
    * Development: `pnpm run dev`
    * Production: `pnpm start`

### MCP Client Integration
Add the server to your Claude Desktop or Cursor configuration.

* **`claude_desktop_config.json` Example:**
    ```json
    {
      "mcpServers": {
        "dex-pools": {
          "command": "node",
          "args": ["dist/index.js"]
        }
      }
    }
    ```

### Available Tools
#### get_all_pools
Retrieves all DEX pools from Uniswap V3 and SushiSwap with comprehensive information.

* **Input**: No parameters required.
* **Output**: A detailed list of all pools.
* **Example Query**: "Show me all available DEX pools" or "Find pools with APR above 10%".

---

## Development & Setup 🛠️
*(This section can include details on how to set up the development environment, run tests, and deploy the protocol).*

---

## License 📄
This project is licensed under the MIT License. See the `LICENSE` file for details.
