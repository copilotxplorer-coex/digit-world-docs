ADR-0002: Verified Checkpoint Architecture
Status: Accepted

Date: 2026-11-03

Decision Type: Architecture Decision Record

Context
Digit World is designed as a persistent shared world that supports:

Multi-Node Runtime
Region Ownership
Authority Transfer
Failover Recovery
Verified Work Minting
Soul Digit Ledger
Community Governance
A traditional save-file approach is insufficient because multiple runtime components may participate in world operation simultaneously.

The project requires a mechanism that provides:

Trustworthy recovery points
Verifiable world state
Failover support
Replay protection
Auditability
Problem
Without verified recovery points, the world becomes vulnerable to:

Conflicting State
Replay Attacks
Duplicate Operations
Split Authority
Invalid Recovery
Double Mint
Double Spend
A node failure should never cause the world to lose integrity.

Decision
Digit World adopts a Verified Checkpoint Architecture.

A checkpoint becomes trusted only after:

Checkpoint Proposal
        ↓
Verification
        ↓
Attestation
        ↓
Central Acceptance
        ↓
Checkpoint Commit
Only committed checkpoints are considered authoritative recovery points.

Checkpoint Lifecycle
Phase 1: Proposal
Runtime produces a checkpoint candidate.

Runtime
    ↓
CHECKPOINT_PROPOSE
The proposal contains a summary of world state.

No world authority changes occur during this phase.

Phase 2: Verification
Trusted Verifiers inspect checkpoint contents.

Verification may result in:

Verified
Rejected
Conflict
Verification does not modify world state.

Phase 3: Attestation
A Trusted Verifier creates an attestation.

Verifier
     ↓
ATTESTATION
The attestation proves that verification succeeded.

Phase 4: Acceptance
Central validates:

Dependencies
Authority Information
Epoch Information
Attestations
Only valid checkpoints may proceed.

Phase 5: Commit
Checkpoint becomes authoritative.

ACCEPT
    ↓
COMMIT
From this point onward the checkpoint is eligible for recovery operations.

Checkpoint Contents
Every checkpoint should contain:

Region Identifier
Epoch
Authority Version
Previous Checkpoint
World State Summary
Pending Operations
Reservations
Game Time Cursor
The checkpoint should represent the authoritative state of a region.

Authority Protection
Checkpoints participate in authority management.

Each checkpoint records:

{
  "region": "frontier_r1a",
  "epoch": 10,
  "authority_version": 25
}
This allows the system to reject stale authority ownership.

Replay Protection
Replay attacks must be prevented.

Examples:

Old Checkpoint
Old Authority Version
Old Epoch
must not be accepted again.

Replay validation uses:

checkpoint_id
epoch
authority_version
to reject obsolete data.

Relationship To Failover
Verified Checkpoints are the foundation of failover.

Failover process:

Node Failure
      ↓
Latest Verified Checkpoint
      ↓
Recovery Runtime
      ↓
Resume Operation
Recovery may only use committed checkpoints.

Relationship To Soul Digit
Soul Digit integrity depends on checkpoints.

Protected systems:

Wallets
Escrow
Treasuries
Reward Pools
Mint Records
Checkpoint recovery must preserve all economic state.

Relationship To Verified Work
Verified Work follows:

Work
 ↓
Attestation
 ↓
Checkpoint Commit
 ↓
Mint
A reward is not considered final until the associated checkpoint has been committed.

Relationship To Authority Transfer
Authority transfers must never occur without a trusted state reference.

Flow:

Verified Checkpoint
        ↓
Authority Transfer
        ↓
New Owner Runtime
Unverified runtime state must not be used.

Relationship To Zone Transfer
Zone transfers may depend on checkpointed state.

Protected data:

Character State
Inventory
Cooldowns
Reservations
Pending Operations
Checkpoint integrity ensures safe movement between regions.

Checkpoint Chain
Checkpoints form a chain.

CP-1
 ↓
CP-2
 ↓
CP-3
 ↓
CP-4
Each checkpoint references the previous checkpoint.

This supports:

Auditing
Recovery
Validation
Rejection Rules
A checkpoint must be rejected if:

Invalid Attestation
Missing Dependencies
Invalid Authority Version
Stale Epoch
Corrupted Content
Conflict Detected
Rejected checkpoints never become authoritative.

Conflict Handling
When conflicting data appears:

Checkpoint A
≠
Checkpoint B
the result is:

CONFLICT
Manual investigation or automated conflict policies may apply.

Recovery Requirements
Recovery must preserve:

World State
Contracts
Communities
Wallets
Escrow
Mint History
Authority Ownership
Recovery must not create:

Duplicate Contracts
Duplicate Currency
Duplicate Authority Owners
Checkpoint Metadata
Recommended structure:

{
  "checkpoint_id": "cp_001",

  "region": "frontier_r1a",

  "epoch": 10,

  "authority_version": 25,

  "asset_version": "1.2.0",

  "ruleset_version": "1.0.0"
}
Checkpoint Statuses
RECEIVED

PENDING

VERIFIED

COMMITTED

REJECTED

CANCELLED

CONFLICT
Only COMMITTED checkpoints are authoritative.

Migration Considerations
Checkpoints participate in migration workflows.

During migration:

Verified Checkpoint
       ↓
Compatibility Validation
       ↓
Migration
       ↓
Verification
Migration should never bypass checkpoint validation.

Security Requirements
Verified Checkpoints must provide:

Integrity
Auditability
Replay Resistance
Recovery Safety
Authority Protection
Checkpoint data is considered security-sensitive.

Alternatives Considered
Unverified Snapshots
Rejected because:

No Trust Model
No Verification
Weak Recovery Guarantees
Runtime Memory Recovery
Rejected because:

Node Failure Risk
No Audit Trail
No Deterministic Recovery
Database Backup Only
Rejected because:

No Authority Tracking
No Verification Layer
No Runtime Validation
Consequences
Digit World adopts Verified Checkpoints as the foundation for:

Recovery
Failover
Authority Management
Replay Protection
Soul Digit Integrity
Verified Work
World Persistence
All critical systems depend on checkpoint integrity.

References
Related Documents:

ARCHITECTURE.md
PROTOCOL.md
SECURITY_SPEC.md
COMPATIBILITY_SPEC.md
MIGRATION_SPEC.md
ADR-0001-login-key.md
Verified Checkpoints are considered a core architectural component of Digit World and are required for long-term world stability.