Accounts
Purpose
This document defines the account model used by Digit World.

The account system is designed to provide:

Persistent Ownership
Secure Authentication
Minimal Personal Data Collection
Long-Term World Compatibility
Multi-Node Runtime Support
Accounts serve as the root ownership entity for all player-controlled resources.

Core Principles
Digit World follows the following account principles:

Account Ownership
Login Key Authentication
Minimal Personal Data
Server Authority
Persistent Identity
The system is intentionally designed to avoid unnecessary dependence on third-party identity providers.

Account Model
An account owns:

Characters
Soul Digit Wallets
Contracts
Community Memberships
Treasury Permissions
Login Keys
All player-owned resources ultimately belong to an account.

Account Identity
Every account has a unique identifier.

Example:

{
  "account_id": "acc_001"
}
Account identifiers:

Permanent
Globally Unique
Never Reassigned
Authentication Model
Digit World uses:

Login Key Authentication
as the primary authentication mechanism.

The world does not rely on:

Email Verification
Password Recovery
Third-Party Login Providers
for normal operation.

Login Key
A Login Key is the primary credential used to access an account.

Properties:

Unique
High Entropy
Non-Recoverable
Portable
Example:

DW-XXXX-XXXX-XXXX-XXXX
Actual implementation details may change, but security requirements remain the same.

New Account Creation
Account creation flow:

Create Account
        ↓
Generate Login Key
        ↓
Display Login Key
        ↓
Store Login Key Safely
        ↓
Account Activated
The Login Key becomes the sole authentication credential.

Login Process
Normal login flow:

Login Key
        ↓
Authentication
        ↓
Session Created
        ↓
World Access Granted
Passwords are not required.

Legacy Password Migration
Older accounts may still exist from previous versions.

Migration flow:

Username + Password
            ↓
Authenticate Once
            ↓
Generate Login Key
            ↓
Store Login Key
            ↓
Disable Password Authentication
After migration:

Login Key Only
Password authentication is permanently disabled.

Login Key Warning
Login Keys are intentionally non-recoverable.

If a Login Key is lost:

Account Access Lost
Character Access Lost
Wallet Access Lost
Digit World does not provide:

Password Reset
Email Recovery
Support Recovery
Manual Administrator Recovery
Users are fully responsible for protecting their Login Keys.

Backup Recommendations
Players should:

Store Login Keys Offline
Maintain Multiple Backups
Protect Login Keys From Disclosure
Recommended storage examples:

Password Manager
Encrypted Storage
Printed Offline Copy
Hardware Storage
Email Policy
Email is optional.

Email is not required for:

Registration
Authentication
Recovery
Gameplay
Digit World must remain operational without any dependency on email infrastructure.

Character Ownership
Every character belongs to exactly one account.

Account
    ↓
Character
Characters cannot exist without an owning account.

Ownership must survive:

Restart
Migration
Failover
Checkpoint Recovery
Soul Digit Ownership
Soul Digit belongs to wallets associated with accounts.

Account
    ↓
Wallet
    ↓
Soul Digit
Wallet ownership is authoritative.

Only server-side systems may modify wallet state.

Contract Ownership
Accounts may create and own:

Escort Contracts
Delivery Contracts
Crafting Orders
Construction Orders
War Contracts
Contract ownership persists across:

Node Failover
Checkpoint Recovery
Runtime Migration
Community Membership
Accounts may participate in communities.

Possible roles:

Member
Resident
Council Member
Leader
Community permissions are governed by active Rulesets and Governance systems.

Session Model
A successful login creates a session.

Login Key
        ↓
Authentication
        ↓
Session
        ↓
World Access
Sessions are temporary.

Accounts remain persistent.

Security Requirements
The account system must support:

Replay Protection
Session Validation
Ownership Validation
Server Authority
All authentication decisions occur server-side.

Audit Requirements
The following events should be recorded:

Account Creation
Login Key Generation
Login Attempts
Migration Events
Session Creation
Session Termination
Audit records support investigation and recovery.

Checkpoint Integration
Verified Checkpoints should preserve:

Account Ownership
Character Ownership
Wallet Ownership
Community Membership
Recovery must not create:

Duplicate Accounts
Duplicate Characters
Duplicate Wallets
Migration Requirements
Account migrations must preserve:

Account ID
Ownership
Wallets
Contracts
Community Memberships
Migration may not alter ownership relationships.

Future Expansion
Possible future features include:

Multiple Login Keys
Key Rotation
Hardware-Backed Keys
Delegated Access
Organization Accounts
Such features must remain compatible with the Login Key model.

Related Documents
README.md
ARCHITECTURE.md
PROTOCOL.md
SECURITY_SPEC.md
MIGRATION_SPEC.md
ADR-0001-login-key.md
The Account System is the foundation of ownership within Digit World and is built around Login Key authentication, long-term persistence, and minimal trust requirements.