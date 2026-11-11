# ALL-CHAIN: A Unified Multi-Chain Liquidity Protocol & Universal USD-Equivalency Layer
**Version 1.1 — November 2026**

---

## Abstract
Modern blockchain ecosystems suffer from severe fragmentation. Users must manage dozens of incompatible wallets, navigate vulnerable cross-chain bridges, and hold multiple native gas tokens simply to interact with digital assets. **All-Chain** solves wallet and network fragmentation by introducing a unified Layer 1 settlement hub powered by **All-Coin (ALL)**—a universal, $1.00 USD-pegged asset backed strictly by native Layer 1 cryptocurrencies and whitelisted stablecoins. Through isolated, time-locked collateral vaults, triple-layer price protection, and a quarterly dynamic fee structure (**Conversion Equity**), All-Chain converts fragmented crypto holdings into a single spendable currency while allowing depositors to retain 100% of their underlying asset's price upside.

---

## 1. The Problem: Fragmentation & Wallet Fatigue
Despite over a decade of blockchain development, real-world adoption remains bottlenecked by structural friction:
* **Wallet & Network Silos:** Holding Bitcoin, Ethereum, Solana, Dogecoin, and Litecoin requires managing separate private keys, incompatible address formats, and isolated ecosystems.
* **Bridge Vulnerability:** Traditional cross-chain bridges create wrapped representations of assets, acting as centralized honeypots responsible for billions of dollars in exploits.
* **Speculative Dilution:** Hundreds of competing networks launch secondary tokens with inflationary emissions, fracturing liquidity and confusing everyday users.

**The All-Chain Thesis:** Users do not want thirty blockchains; they want one balance, one wallet, and one universal unit of account that works everywhere without sacrificing ownership of their core Layer 1 assets.

---

## 2. Core Architecture & The All-Coin (ALL) Standard
All-Chain operates as a high-throughput Proof-of-Stake Layer 1 blockchain engineered around a single, universal currency: **All-Coin (ALL)**.

* **Strict 1:1 USD Equivalency:** Every 1.00 ALL represents exactly $1.00 USD in locked protocol collateral.
* **Single-Token Simplicity:** All-Coin serves simultaneously as the network's medium of exchange, unit of account, and gas fee token. There is no secondary inflationary governance token diluting network value.
* **Unified User Interface:** Users interact with a single All-Chain wallet address to send, receive, and spend ALL across the ecosystem, completely abstracted from the underlying home chains of their deposited assets.

---

## 3. Strict Collateral Whitelist (Zero Meme-Coin Policy)
To protect network solvency and eliminate speculative contagion, **All-Chain strictly prohibits secondary tokens** (no ERC-20 meme coins, SPL tokens, NFTs, or synthetic wrapped assets). 

Collateral deposits are restricted exclusively to two categories:
1. **Battle-Tested Native Layer 1 Coins:** Bitcoin (BTC), Ethereum (ETH), Solana (SOL), Litecoin (LTC), Dogecoin (DOGE), Avalanche (AVAX), Cardano (ADA), and Cosmos (ATOM).
2. **Whitelisted Native Stablecoins:** Tier-1 fiat-backed stablecoins (USDC, USDT) issued natively on supported Layer 1 networks.

---

## 4. The Mint, Time-Lock & Burn Lifecycle

### 4.1 Deposit & Minting Mechanics
When a user deposits a whitelisted native asset (e.g., 1 SOL at a confirmed price of $85.00), the All-Chain smart vault locks the native asset on its home chain via decentralized Multi-Party Computation (MPC) custody and mints **All-Coin (ALL)** at **85% of the confirmed USD value** (leaving a 15% volatility cushion):

$$\text{Gross Minted ALL} = \text{Asset Quantity} \times \text{Confirmed USD Price} \times 0.85$$

$$\text{Net Minted ALL} = \text{Gross Minted ALL} \times (1 - f_{\text{CE}})$$

*Example:* Depositing 1 SOL at $85.00 yields a gross mint of **72.25 ALL** (minus the applicable Conversion Equity fee).

### 4.2 Fixed-Debt Vault Ledger
At the exact moment of confirmation, the user's repayment obligation is permanently locked in USD terms (72.25 ALL) and recorded on a non-transferable **Vault Receipt** tied to the depositor's wallet.
* **Price Appreciation (Upside Retention):** If 1 SOL rises from $85.00 to $250.00 during the lock period, the user still only owes **72.25 ALL** to unlock their 1 SOL, keeping 100% of the capital gains.
* **Price Depreciation (User-Isolated Downside):** Every vault is strictly isolated. If SOL drops in value, only the individual depositor of that vault bears the price risk—never other users or the broader All-Coin supply.

### 4.3 Mandatory Time-Lock Schedule
To prevent short-term oracle arbitrage and enable sustainable protocol yield generation, all deposits are subject to a mandatory minimum lock duration:
* **Phase 1 (Network Launch):** **90-day (3-month)** minimum lock period.
* **Phase 2 (Protocol Maturity):** **30-day (1-month)** minimum lock period, unlocked automatically once the Protocol Insurance Reserve reaches its target capitalization threshold.

### 4.4 Redemption & Permanent Burn
Once the mandatory time-lock expires, the depositor initiates redemption by returning the exact gross minted ALL debt (72.25 ALL) plus the exit Conversion Equity fee to the vault contract. The smart contract **permanently burns** the returned ALL debt—maintaining a strict 1:1 supply-to-collateral ratio—routes the exit fee to the treasury, and releases the exact original native asset (1 SOL) back to the user's home-chain wallet.

---

## 5. Triple-Layer Price & Solvency Protection
To protect both users and the $1.00 All-Coin peg from flash crashes and execution latency, every deposit is governed by three automated safeguards:

1. **Pre-Lock Slippage Guard (User Protection):** Before submitting a deposit, the user defines a minimum acceptable ALL payout. If the asset's market price drops below that floor while the transaction is confirming, the contract automatically cancels the deposit and returns the native coins untouched.
2. **Confirmation Block Pricing (Anti-Manipulation):** The protocol ignores front-end UI quotes and locks in the decentralized oracle price at the **exact block timestamp** the deposit confirms on its native blockchain.
3. **85% Collateral Buffer & Auto-Liquidation (Peg Protection):** The 15% initial collateral haircut absorbs normal daily market fluctuations without impacting the user's position. However, if a locked asset experiences a severe market crash and falls to the vault's break-even threshold (102% of the gross minted ALL debt), the smart contract executes an automatic liquidation into USD reserves. The depositor retains the All-Coin they already minted, forfeits the crashed collateral, and ensures every circulating ALL remains backed by $1.00 of real value.

---

## 6. Dynamic Conversion Equity (Quarterly Fee Model)
Rather than charging arbitrary flat fees, All-Chain assesses **Conversion Equity**—a dynamic entry and exit fee calibrated to each asset's trailing 12-month annualized price volatility.

* **Quarterly Recalibration:** Decentralized volatility oracles recalculate asset tiers automatically on the **1st day of each calendar quarter** (**January 1, April 1, July 1, and October 1** at 00:00 UTC).
* **Rate Lock Guarantee:** Once a user initiates a vault deposit, their exit Conversion Equity rate is locked for the duration of that contract, ensuring zero surprise fee increases upon redemption.

| Volatility Tier | Trailing 12-Month Annualized Volatility | Conversion Equity Fee (Mint / Burn) | Representative Assets |
| :--- | :--- | :--- | :--- |
| **Tier 1: Stable** | $< 2\%$ | **0.10%** | USDC, USDT *(Native L1)* |
| **Tier 2: Low Volatility** | $2\% - 45\%$ | **0.50%** | Bitcoin (BTC), Ethereum (ETH) |
| **Tier 3: Moderate Volatility** | $45\% - 75\%$ | **1.00%** | Solana (SOL), Litecoin (LTC), Cardano (ADA) |
| **Tier 4: High Volatility** | $> 75\%$ | **1.50%** | Dogecoin (DOGE), Avalanche (AVAX) |

---

## 7. Sustainable Protocol Economics & Yield Engine
All-Chain generates self-sustaining real yield without relying on inflationary token emissions:

1. **Time-Locked Staking & Liquidity Deployment:** During the mandatory 3-month (or 1-month) lock window, deposited Proof-of-Stake assets (ETH, SOL, ADA, ATOM) are natively staked with vetted institutional validators. Proof-of-Work assets (BTC, LTC, DOGE) are deployed into audited, over-collateralized institutional liquidity facilities.
2. **Revenue Distribution:** 100% of native staking yields and Conversion Equity fees flow into the All-Chain Protocol Treasury, allocated across three core pillars:
   * **50% — Insurance & Peg Stabilization Reserve:** Ring-fenced USD and Tier-1 reserves guaranteeing All-Coin's $1.00 redemption integrity under extreme market stress.
   * **30% — Network Security & Validator Operations:** Funding node operators, decentralized oracle feeds, and MPC custody infrastructure.
   * **20% — Ecosystem & Merchant Integration Fund:** Subsidizing zero-fee point-of-sale payment rails and wallet infrastructure.

---

## 8. Roadmap & Phased Rollout
* **Phase I — Genesis & Core Vaults:** Launch of All-Chain Mainnet, MPC custody vaults for BTC, ETH, SOL, LTC, DOGE, and native USDC/USDT with 90-day time-locks and quarterly Conversion Equity recalibration.
* **Phase II — Merchant & Unified Wallet SDK:** Release of the All-Chain consumer wallet and instant payment API, allowing users to spend All-Coin directly with zero gas friction.
* **Phase III — 30-Day Lock Activation:** Upon reaching target Insurance Reserve capitalization, reduce minimum vault time-locks from 90 days to 30 days and expand native Layer 1 support via supermajority governance.

---

## Appendix A: Mathematical Specification & Worked Scenarios

### A.1 Core Protocol Equations

#### 1. Collateral Valuation & Minting Formula
Let:
* $Q$ = Quantity of native Layer 1 asset deposited
* $P_0$ = Confirmed decentralized oracle USD price at block confirmation timestamp $t_0$
* $\alpha = 0.85$ = Protocol Loan-to-Value (LTV) collateralization factor (leaving a $15\%$ safety buffer)
* $f_{\text{CE}}$ = Quarterly Conversion Equity fee rate for the asset's volatility tier
* $M_{\text{min}}$ = User-defined Pre-Lock Slippage Guard minimum payout

**Vault Debt ($D_{\text{ALL}}$):** The fixed USD-denominated obligation recorded on the user's Vault Receipt:
$$D_{\text{ALL}} = Q \times P_0 \times \alpha$$

**Entry Fee ($F_{\text{in}}$) & Net User Payout ($M_{\text{net}}$):**
$$F_{\text{in}} = D_{\text{ALL}} \times f_{\text{CE}}$$
$$M_{\text{net}} = D_{\text{ALL}} - F_{\text{in}} = D_{\text{ALL}} \times (1 - f_{\text{CE}})$$

**Slippage Execution Condition:** The smart contract executes the lock if and only if:
$$M_{\text{net}} \ge M_{\text{min}}$$
If $M_{\text{net}} < M_{\text{min}}$, the transaction reverts and $Q$ is returned to the depositor without penalty.

---

#### 2. Volatility Tier Classification Formula
On the first day of each calendar quarter ($t_q$), the protocol calculates each whitelisted asset's trailing 365-day annualized realized volatility ($\sigma_{\text{annual}}$) from daily logarithmic oracle returns $r_i = \ln(P_i / P_{i-1})$:

$$\sigma_{\text{annual}} = \sqrt{365} \times \sqrt{\frac{1}{364} \sum_{i=1}^{365} (r_i - \bar{r})^2}$$

The resulting $\sigma_{\text{annual}}$ assigns the asset's Conversion Equity rate $f_{\text{CE}}$ for the upcoming quarter:
$$f_{\text{CE}} = \begin{cases} 0.0010 & \text{if } \sigma_{\text{annual}} < 0.02 \text{ (Tier 1: Stable)} \\ 0.0050 & \text{if } 0.02 \le \sigma_{\text{annual}} \le 0.45 \text{ (Tier 2: Low)} \\ 0.0100 & \text{if } 0.45 < \sigma_{\text{annual}} \le 0.75 \text{ (Tier 3: Moderate)} \\ 0.0150 & \text{if } \sigma_{\text{annual}} > 0.75 \text{ (Tier 4: High)} \end{cases}$$

---

#### 3. Health Factor & Auto-Liquidation Threshold
At any timestamp $t > t_0$, let $P_t$ be the current oracle price of the locked asset. The live USD value of the vault's collateral is $V_t = Q \times P_t$.

**Vault Health Factor ($H_t$):**
$$H_t = \frac{Q \times P_t}{D_{\text{ALL}}}$$

**Liquidation Trigger Price ($P_{\text{liq}}$):** Auto-liquidation triggers when $H_t$ drops to the protocol break-even floor $\beta = 1.02$ (102% of gross minted ALL debt, leaving a 2% execution buffer for market slippage and liquidation gas):
$$P_{\text{liq}} = \frac{\beta \times D_{\text{ALL}}}{Q} = 1.02 \times \alpha \times P_0 = 0.867 \times P_0$$

*Note:* Every deposit can withstand a **13.3% price drop** immediately upon confirmation before approaching liquidation. Any surplus USD recovered above $D_{\text{ALL}}$ during liquidation (up to $2\%$) is swept into the **Insurance & Peg Stabilization Reserve**.

---

#### 4. Redemption & Burn Formula
At any timestamp $t \ge t_0 + T_{\text{lock}}$ (where $T_{\text{lock}} \in \{90\text{ days}, 30\text{ days}\}$), assuming $H_t > 1.02$ throughout the lock period, the user reclaims $Q$ by submitting:

$$\text{Total ALL Required} = D_{\text{ALL}} + F_{\text{out}} = D_{\text{ALL}} \times (1 + f_{\text{CE}})$$

Upon receipt:
1. $D_{\text{ALL}}$ is **permanently burned**, reducing circulating ALL supply to match the unlocked collateral.
2. $F_{\text{out}} = D_{\text{ALL}} \times f_{\text{CE}}$ is routed to the Protocol Treasury.
3. Exact asset quantity $Q$ is released to the user's home-chain address.

---

#### 5. Global Peg Solvency Invariant
Across all active vaults $k = 1, 2, \dots, N$ and the Insurance Reserve balance $R_{\text{USD}}$, All-Chain enforces strict 1:1 backing at all times:

$$\sum_{k=1}^{N} \min\left(Q_k \times P_{k,t},\; D_{\text{ALL},k}\right) + R_{\text{USD}} \ge \text{Total Circulating ALL}$$

---

### A.2 Worked User Scenarios

#### Scenario 1: Bull Market Upside Retention (SOL Deposit)
A user deposits **$Q = 10\text{ SOL}$** when **$P_0 = \$85.00$** (Tier 3 Moderate Volatility, $f_{\text{CE}} = 1.00\%$), setting a slippage minimum of $M_{\text{min}} = 700\text{ ALL}$.

1. **Deposit & Mint ($t = 0$):**
   * Confirmed Collateral Value: $10 \times \$85.00 = \$850.00$
   * Fixed Vault Debt: $D_{\text{ALL}} = \$850.00 \times 0.85 = \mathbf{722.50\text{ ALL}}$
   * Entry Conversion Equity ($1.00\%$): $F_{\text{in}} = 722.50 \times 0.01 = \mathbf{7.225\text{ ALL}}$
   * Net Payout to User: $M_{\text{net}} = 722.50 - 7.225 = \mathbf{715.275\text{ ALL}}$ (passes $M_{\text{min}} = 700\text{ ALL}$)
   * Liquidation Price Floor: $P_{\text{liq}} = 0.867 \times \$85.00 = \mathbf{\$73.70}$
2. **Market Rally ($t = 90\text{ days}$):**
   * SOL rallies to **$P_{90} = \$200.00$** (Vault collateral is now worth **$\$2,000.00$**).
   * The user's debt remains fixed at **722.50 ALL**.
3. **Redemption & Profit:**
   * Exit Conversion Equity ($1.00\%$): $F_{\text{out}} = 722.50 \times 0.01 = \mathbf{7.225\text{ ALL}}$
   * Total ALL Paid by User: $722.50 + 7.225 = \mathbf{729.725\text{ ALL}}$
   * User receives all **10 SOL** (worth $\$2,000.00$), capturing **100% of the $\$1,150.00$ price gain** while having had $715.275\text{ ALL}$ in liquid spending power for 3 months.

---

#### Scenario 2: Severe Market Crash & Auto-Liquidation (DOGE Deposit)
A user deposits **$Q = 10,000\text{ DOGE}$** when **$P_0 = \$0.20$** (Tier 4 High Volatility, $f_{\text{CE}} = 1.50\%$).

1. **Deposit & Mint ($t = 0$):**
   * Confirmed Collateral Value: $10,000 \times \$0.20 = \$2,000.00$
   * Fixed Vault Debt: $D_{\text{ALL}} = \$2,000.00 \times 0.85 = \mathbf{1,700.00\text{ ALL}}$
   * Entry Conversion Equity ($1.50\%$): $F_{\text{in}} = 1,700.00 \times 0.015 = \mathbf{25.50\text{ ALL}}$
   * Net Payout to User: $M_{\text{net}} = 1,700.00 - 25.50 = \mathbf{1,674.50\text{ ALL}}$
   * Liquidation Price Floor: $P_{\text{liq}} = 0.867 \times \$0.20 = \mathbf{\$0.1734}$
2. **Market Crash ($t = 42\text{ days}$):**
   * DOGE crashes from $\$0.20$ down to **$\$0.1734$** (a $13.3\%$ drop), hitting $H_t = 1.02$.
3. **Automated Protocol Execution:**
   * The vault sells the $10,000\text{ DOGE}$ at $\$0.1734$ for **$\$1,734.00$** in USD reserves.
   * **$1,700.00$** is locked into the 1:1 Peg Backing Pool to cover the $1,700.00\text{ ALL}$ circulating in the economy.
   * **$34.00$** (the $2\%$ liquidation buffer) is deposited into the Insurance Reserve.
   * **Outcome:** The user keeps their **$1,674.50\text{ ALL}$** spendable balance, only the depositor loses upside exposure to DOGE, and All-Coin's $\$1.00$ peg remains 100% solvent.

---

#### Scenario 3: Multi-Chain Portfolio Consolidation (Single Wallet)
A user tired of managing four wallets consolidates their portfolio into All-Chain in a single session:

| Asset Deposited | Confirmed Price ($P_0$) | Gross USD Value | Volatility Tier ($f_{\text{CE}}$) | Gross Debt ($D_{\text{ALL}}$) | Entry Fee ($F_{\text{in}}$) | Net ALL Minted |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **1.00 ETH** | $\$3,000.00$ | $\$3,000.00$ | Tier 2 ($0.50\%$) | $2,550.00\text{ ALL}$ | $12.75\text{ ALL}$ | **$2,537.25\text{ ALL}$** |
| **10.00 SOL** | $\$85.00$ | $\$850.00$ | Tier 3 ($1.00\%$) | $722.50\text{ ALL}$ | $7.23\text{ ALL}$ | **$715.27\text{ ALL}$** |
| **12.00 LTC** | $\$80.00$ | $\$960.00$ | Tier 3 ($1.00\%$) | $816.00\text{ ALL}$ | $8.16\text{ ALL}$ | **$807.84\text{ ALL}$** |
| **2,000 USDC** | $\$1.00$ | $\$2,000.00$ | Tier 1 ($0.10\%$) | $1,700.00\text{ ALL}$ | $1.70\text{ ALL}$ | **$1,698.30\text{ ALL}$** |
| **Total Portfolio** | — | **$\$6,810.00$** | — | **$5,788.50\text{ ALL}$** | **$29.84\text{ ALL}$** | **$5,758.66\text{ ALL}$** |

* **Result:** Four separate blockchains are consolidated into one unified balance of **$5,758.66 ALL** in a single wallet, while the protocol earns 90 days of native staking and liquidity yield across all four underlying assets.
