ADR-0003: Soul Digit Economy
Status: Accepted

Date: 2026-11-03

Decision Type: Architecture Decision Record

Context
Digit World requires a unified economic system capable of supporting:

Player Contracts
Community Treasuries
Governance Systems
War Systems
Asset Markets
Long-Term World Persistence
A traditional MMORPG gold economy was considered insufficient because it typically relies on:

NPC Rewards
Monster Currency Drops
Daily Rewards
Infinite Currency Creation
These approaches tend to cause:

Inflation
Botting
Currency Farming
Economic Instability
Digit World requires an economy that remains sustainable over long periods of operation.

Problem
The project needs a currency system that:

Supports player-driven gameplay
Supports community governance
Supports contracts and escrow
Supports long-term persistence
Minimizes inflation
Prevents uncontrolled currency creation
The currency must also remain compatible with:

Verified Checkpoints
Trusted Verifiers
Ledger Protection
Replay Protection
Decision
Digit World adopts Soul Digit as the primary currency of the world.

Soul Digit is a ledger-backed currency governed by the following principles:

Verifiable
Auditable
Scarcity Controlled
Checkpoint Protected
Soul Digit is treated as a protected subsystem.

Currency Model
Soul Digit acts as:

Currency
+
Reward Unit
+
Treasury Resource
+
Contract Settlement Asset
It is not intended to function as:

Cryptocurrency
Real World Currency
Speculative Token
Its purpose is strictly tied to world operation.

Minting Model
New Soul Digit may only be created through:

Verified Useful Work
        ↓
Attestation
        ↓
Checkpoint Commit
        ↓
Mint
This path is mandatory.

Approved Mint Sources
Verification Work
Examples:

Runtime Verification
Trusted Verifier Work
Validation Tasks
Checkpoint Work
Examples:

Checkpoint Verification
Checkpoint Acceptance
Checkpoint Processing
Replication Work
Examples:

Verified Replication
Data Availability Tasks
Recovery Support Tasks
Community Projects
Examples:

Verified Public Infrastructure
Verified Shared World Improvements
Only approved and verifiable projects qualify.

Prohibited Mint Sources
The following may not create Soul Digit:

Login Rewards
Login
↓
Receive Currency
Rejected.

Daily Rewards
Daily Mission
↓
Receive Currency
Rejected.

Monster Currency Drops
Monster Kill
↓
Soul Digit Drop
Rejected.

Passive Uptime
Node Online
↓
Receive Currency
Rejected.

Resource Farming
Idle Machine Time
↓
Receive Currency
Rejected.

Verified Work Principle
The project adopts:

Proof of Useful Work
instead of:

Proof of Resource
A machine being online is not valuable by itself.

Only completed and verified work may participate in reward distribution.

Reward Pool Model
Soul Digit generation is limited through Reward Pools.

Example:

{
  "epoch_reward_cap": 10000
}
The pool limits total newly created currency.

Workload growth does not automatically increase currency generation.

Reward Formula
Reward allocation follows:

Reward Pool
      ×
Worker Contribution
      ÷
Total Contribution
This prevents unlimited minting.

Soul Digit Ledger
All Soul Digit balances must be recorded in the Ledger system.

The Ledger contains:

Wallets
Transfers
Escrow
Treasuries
Mint History
Transaction History
The Ledger is authoritative.

Wallet Model
Supported wallets include:

Player Wallet
Guild Wallet
Community Wallet
System Wallet
Each wallet must be tracked by the Ledger.

Transfer Model
Wallets support transfers.

Example:

Wallet A
    ↓
Wallet B
Transfers are recorded permanently.

Fee Model
Transfers may include fees.

Examples:

Transfer Fee
Market Fee
Contract Fee
Collected fees may flow into:

Reward Pools
Community Systems
Treasury Systems
according to active Rulesets.

Escrow Model
Contracts use escrow-backed rewards.

Flow:

Create Contract
      ↓
Reserve Reward
      ↓
Escrow
      ↓
Complete Contract
      ↓
Release Reward
Rewards must exist before a contract becomes active.

Community Treasury
Communities may maintain treasuries.

Treasuries may fund:

Community Projects
Community Contracts
Wars
Infrastructure
Treasury funds remain under governance control.

War Funding
War-related contracts may be funded through:

Community Treasury
Guild Treasury
Escrow Systems
War rewards must not bypass ledger controls.

Double Mint Protection
Soul Digit is protected against replay and duplicate processing.

Protected identifiers include:

operation_id
checkpoint_id
authority_version
attestation_id
A mint operation must never execute twice.

Checkpoint Integration
Economic state is included in Verified Checkpoints.

Protected state:

Wallets
Treasuries
Escrow
Mint Records
Reward Pools
This ensures recovery consistency.

Security Requirements
Soul Digit requires:

Replay Protection
Ledger Integrity
Checkpoint Integrity
Mint Validation
Escrow Protection
Economic security is considered a critical subsystem.

Governance Requirements
Changes affecting:

Mint Logic
Reward Pools
Transfer Fees
Ledger Design
require elevated review.

Typical approval requirements:

Economy Review
+
Core Maintainer Review
Migration Requirements
Soul Digit migrations must preserve:

Wallet Balances
Escrow
Treasuries
Transaction History
Mint Records
Migration must never:

Reset Balances
Create Currency
Destroy Currency
Rewrite History
without an explicit governance decision.

Alternatives Considered
Traditional MMORPG Gold System
Rejected because:

Inflation Risk
Botting Incentives
Unlimited Currency Creation
Random Currency Drops
Rejected because:

Encourages Farming
Weak Economic Control
Reward Inflation
Uptime-Based Rewards
Rejected because:

Encourages VM Farming
Rewards Idle Resources
Provides No Useful Work Guarantee
Consequences
Digit World adopts Soul Digit as a controlled, ledger-backed currency.

Currency creation is tied exclusively to:

Verified Useful Work
and protected by:

Attestation
Checkpoint Commit
Ledger Validation
Double Mint Protection
This provides a strong foundation for long-term economic stability.

References
Related Documents:

ARCHITECTURE.md
PROTOCOL.md
SECURITY_SPEC.md
COMPATIBILITY_SPEC.md
MIGRATION_SPEC.md
ADR-0002-verified-checkpoint.md
Soul Digit is considered a core strategic subsystem of Digit World and is protected by both technical and governance controls.