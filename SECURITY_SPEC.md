Security Specification
Purpose
This document defines the security architecture, security requirements, and security policies of Digit World.

The purpose of this specification is to protect:

Player Accounts
World State
Soul Digit Economy
Community Governance
Contracts
Checkpoints
Runtime Infrastructure
Security is considered a first-class system requirement.

Security Principles
Digit World follows the following security principles:

Least Privilege
Defense In Depth
Deterministic Validation
Verifiable Operations
Replay Resistance
Auditability
All critical operations must be:

Authenticated
Authorized
Validated
Audited
before becoming part of the world state.

Security Domains
Digit World security is divided into the following domains:

Account Security
Runtime Security
Checkpoint Security
Economy Security
Contract Security
Community Security
Infrastructure Security
Threat Model
The project assumes attackers may attempt:

Account Theft
Node Compromise
Replay Attacks
Double Mint Attacks
Double Spend Attacks
Contract Exploits
Economy Manipulation
Checkpoint Forgery
Runtime Tampering
All systems should be designed with these threats in mind.

Authentication Security
Login Key System
Digit World uses Login Keys as the primary authentication mechanism.

Account
     ↓
Login Key
Passwords may only be used during migration.

Login Key Requirements
Login Keys must:

Be Unique
Be Secret
Be Non-Recoverable
Users are responsible for protecting their Login Keys.

Login Migration
Legacy accounts may perform:

Password Login
       ↓
Login Key Generation
       ↓
Password Disabled
Once migration is complete, only Login Keys are accepted.

Authorization Security
All actions must be authorized before execution.

Examples:

Wallet Transfer
Contract Creation
Contract Approval
Community Governance
War Declaration
Authorization must be verified server-side.

Clients are never authoritative.

Runtime Security
Runtime Security protects:

Central Runtime
Region Runtime
Workers
Verifiers
Runtime Rules
A Runtime may only:

Process Authorized Requests
Process Current Epoch Data
Process Current Authority Data
Old authority versions must be rejected.

Authority Security
Authority ownership must remain singular.

Valid:

Region
       ↓
One Authority
Invalid:

Region
       ↓
Two Authorities
Duplicate authority ownership must be treated as a critical security issue.

Epoch Security
Every authority owner belongs to an epoch.

Example:

Epoch 10
Messages from

Epoch 9
must be rejected.

Replay Protection
Replay attacks are prohibited.

Protected operations:

Wallet Transfers
Mint Requests
Checkpoint Commits
Authority Transfers
Contracts
Replay Keys
Recommended keys:

message_id
operation_id
checkpoint_id
authority_version
Duplicate identifiers must be rejected.

Checkpoint Security
Verified Checkpoints are trusted recovery points.

Checkpoint Flow:

Propose
   ↓
Verify
   ↓
Attest
   ↓
Accept
   ↓
Commit
Only committed checkpoints are trusted.

Trusted Verifier Security
Trusted Verifiers provide attestation.

Verifiers may:

Approve
Reject
Conflict
Verifiers may not:

Mint Currency
Modify Accounts
Modify World State
directly.

Soul Digit Security
Soul Digit is a protected subsystem.

Security objectives:

Prevent Double Mint
Prevent Double Spend
Prevent Unauthorized Mint
Protect Ledger Integrity
Mint Security
New Soul Digit may only be created through:

Verified Work
       ↓
Attestation
       ↓
Checkpoint Commit
       ↓
Mint
Minting without attestation is prohibited.

Minting without checkpoint commitment is prohibited.

Double Mint Protection
Mint operations must be protected using:

operation_id
checkpoint_id
authority_version
The same operation must never mint twice.

Ledger Security
Ledger data must preserve:

Balances
Escrow Records
Treasury Records
Mint History
Transaction History
Ledger entries must be append-only.

Historical records should never be silently rewritten.

Contract Security
Contracts use escrow-backed rewards.

Flow:

Reward Reservation
        ↓
Escrow
        ↓
Execution
        ↓
Completion
Funds must exist before contract activation.

Escort Contract Security
Escort contracts must fail when:

Client Dead
Failure events must not be bypassed.

Community Security
Community operations include:

Voting
Treasury Spending
Renaming
Merging
War Decisions
All governance actions must be auditable.

Treasury Security
Treasury operations require authorization.

Protected actions:

Withdrawals
War Funding
Community Contracts
Treasury transactions must be ledger-backed.

Election Security
Election systems must prevent:

Duplicate Voting
Vote Forgery
Unauthorized Candidacy
All votes should be recorded for auditing.

Infrastructure Security
Infrastructure includes:

Servers
Databases
Runtime Nodes
Build Pipelines
Release Systems
Infrastructure should follow:

Least Privilege
Network Isolation
Access Logging
CI/CD Security
All changes must pass:

Validation
Testing
Review
before deployment.

Production deployment should require approved releases.

Direct production modification is prohibited.

Asset Security
Assets must pass:

Schema Validation
Dependency Validation
Compatibility Validation
before release.

Malformed assets must be rejected.

Ruleset Security
Rulesets affect world behavior.

Protected areas include:

Economy
Soul Digit
Governance
Combat
Ruleset changes may require additional review depending on impact.

Audit Requirements
The following operations must be auditable:

Mint
Wallet Transfer
Escrow Release
Checkpoint Commit
Authority Transfer
War Declaration
Treasury Withdrawal
Audit records should be retained long-term.

Incident Response
When security issues are detected:

Detect
   ↓
Contain
   ↓
Investigate
   ↓
Recover
   ↓
Review
Recovery should use verified checkpoints whenever possible.

Recovery Strategy
World recovery follows:

Verified Checkpoint
       ↓
Validation
       ↓
Restore
       ↓
Verification
       ↓
Activation
Security Review Requirements
The following areas require elevated review:

Mint Logic
Checkpoint Logic
Authentication
Authority Logic
Ledger
Escrow
Security-sensitive changes should never bypass review.

Future Security Areas
Planned expansion includes:

Advanced Verifier Security
Cross-Region Security
Marketplace Security
VR Runtime Security
AI Runtime Security
Distributed Runtime Security
Final Rule
Security takes priority over convenience.

No feature, release, migration, or deployment should compromise:

World Integrity
Player Assets
Soul Digit Integrity
Checkpoint Integrity
Governance Integrity
All critical systems must remain:

Verifiable
Auditable
Deterministic
Replay Resistant
throughout the lifetime of the project.