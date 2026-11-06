Account Plan
Purpose
This document defines the account architecture used by Digit World.

The account system is designed to support:

Long-Term World Persistence
Open Source Development
Multi-Node Runtime
Community Hosting
Minimal Personal Data Collection
Secure Authentication
The account system exists to identify players and protect ownership of characters, assets, communities, and Soul Digit balances.

Design Principles
Digit World follows these account principles:

Player Ownership
Minimal Personal Data
Login Key Authentication
Server Authority
Long-Term Persistence
Accounts should remain simple, secure, and independent from third-party identity providers.

Account Model
Each account owns:

Characters
Soul Digit Wallets
Contracts
Community Memberships
Login Keys
An account is the root ownership entity inside the world.

Account Identity
Accounts are identified by:

Account ID
Example:

{
  "account_id": "acc_001"
}
Account IDs are permanent.

Account IDs are never reassigned.

Authentication Model
Digit World uses:

Login Key Authentication
as the primary authentication mechanism.

Password-based authentication exists only as a temporary migration tool.

Login Key
A Login Key is:

Unique
High Entropy
Non-Recoverable
Example:

DW-9TFD-7Y84-....
Implementation details may change, but entropy and uniqueness requirements remain mandatory.

Login Flow
New Account
Create Account
        ↓
Generate Login Key
        ↓
Deliver Login Key
        ↓
Store Login Key Securely
The Login Key becomes the primary authentication credential.

Existing Account
Login Key
        ↓
Authentication
        ↓
Session Creation
Legacy Password Migration
Legacy password-based accounts may perform:

Password Login
        ↓
Generate Login Key
        ↓
Store Login Key
        ↓
Disable Password Authentication
Password usage exists only for migration.

Recovery Policy
Digit World follows a non-recoverable authentication model.

If a Login Key is lost:

Account Access Is Lost
The system intentionally does not provide:

Password Recovery
Email Recovery
Support Recovery
Administrator Reset
User Responsibility
Players must:

Backup Login Keys
Store Login Keys Securely
Protect Login Keys
The world cannot recover keys that no longer exist.

Personal Data Policy
Digit World minimizes personal data collection.

The account system does not require:

Real Name
Email Address
Phone Number
Government ID
unless future optional services explicitly introduce such features.

Character Ownership
Each character belongs to exactly one account.

Account
      ↓
Character
Character ownership cannot exist independently.

Character Persistence
Accounts preserve ownership of:

Character State
Inventory
Soul Digit
Contracts
Community Membership
through checkpoints and recovery operations.

Soul Digit Ownership
Soul Digit is owned by wallets associated with accounts.

Example:

Account
      ↓
Wallet
      ↓
Soul Digit Balance
Wallet ownership is authoritative.

Contract Ownership
Accounts may create:

Escort Contracts
Delivery Contracts
Crafting Contracts
Construction Contracts
War Contracts
Contract ownership remains linked to accounts even after runtime failover.

Community Membership
Accounts may participate in communities.

Possible roles:

Member
Resident
Council Member
Leader
Community permissions are determined by governance systems.

Session Model
Successful authentication creates a session.

Example:

Login Key
      ↓
Session
      ↓
Runtime Access
Sessions are temporary.

Accounts are persistent.

Security Requirements
The account system must provide:

Authentication Protection
Replay Protection
Session Validation
Ownership Protection
Account actions must always be validated server-side.

Server Authority
The client cannot decide:

Account Ownership
Character Ownership
Wallet Ownership
Community Authority
All authoritative decisions are made by Runtime systems.

Audit Requirements
The following events should be audited:

Account Creation
Login Key Generation
Authentication
Character Creation
Account Migration
Audit records support investigation and recovery.

Checkpoint Integration
Checkpoints should preserve:

Account Ownership
Character Ownership
Wallet Ownership
Community Membership
Restoration should never create:

Duplicate Accounts
Duplicate Characters
Duplicate Wallet Ownership
Migration Requirements
Account migrations must preserve:

Account ID
Character Ownership
Wallet Ownership
Community Membership
Migration must not alter ownership records.

Future Expansion
Possible future features include:

Multiple Login Keys
Hardware-Bound Keys
Delegated Access
Community-Owned Service Accounts
Such additions must remain compatible with the core Login Key model.

Security Considerations
Important security properties:

No Password Storage
No Email Dependency
No Recovery Backdoors
Server Authority
The account system prioritizes security and simplicity over convenience.

Related Documents
README.md
ARCHITECTURE.md
SECURITY_SPEC.md
PROTOCOL.md
MIGRATION_SPEC.md
ADR-0001-login-key.md
The account system is a foundational component of Digit World and serves as the root ownership layer for all player-controlled assets and identities.