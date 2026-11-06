ADR-0005: Replay Protection and Idempotent Processing
Status: Accepted

Date: 2026-11-03

Decision Type: Architecture Decision Record

Context
Digit World is a persistent multi-node world that depends on:

Region Runtime
Central Coordination
Trusted Verifiers
Verified Checkpoints
Soul Digit Ledger
Contract Runtime
Community Governance
The system must operate correctly even when:

Messages Are Re-transmitted
Nodes Restart
Failover Occurs
Checkpoints Are Restored
Networks Are Unreliable
Without replay protection, identical operations may be processed multiple times, causing corruption of the world state.

Problem
The following failures must be prevented:

Double Mint
Double Spend
Duplicate Contracts
Duplicate Character Transfers
Duplicate Rewards
Repeated Authority Transfers
Repeated Checkpoint Commits
The system must guarantee that a previously accepted operation cannot be executed again as a new operation.

Decision
Digit World adopts a strict:

Replay Protection
+
Idempotent Processing
model for all critical operations.

Every protected operation must include identifiers allowing the system to determine:

Have We Already Processed This?
before execution.

Core Principle
The same operation must never produce multiple authoritative effects.

Example:

Process Once
      ↓
Commit Once
      ↓
Result Once
Repeated requests with the same identity must return the same outcome.

Idempotency Requirement
Protected operations must be idempotent.

Example:

TRANSFER #123
First attempt:

Success
Balance Updated
Second attempt:

Already Processed
Return Existing Result
No additional balance changes occur.

Replay Protection Scope
Replay protection applies to:

Soul Digit Minting
Wallet Transfers
Escrow Releases
Checkpoint Commits
Authority Transfers
Contract State Changes
Community Governance Actions
War Declarations
Zone Transfers
Protected Operation Identity
Every protected operation must contain:

operation_id
Example:

{
  "operation_id": "op_001"
}
The identifier must remain stable across retries.

Message Identity
Messages should additionally contain:

message_id
Example:

{
  "message_id": "msg_001"
}
Message identifiers support:

Transport Deduplication
Audit Logging
Tracing
Replay Record
Every committed operation creates:

Replay Record
Example:

{
  "operation_id": "op_001",

  "status": "COMMITTED"
}
The replay record becomes authoritative evidence that the operation already executed.

Operation States
Operations may exist in:

RECEIVED

PENDING

VERIFIED

COMMITTED

FAILED

REJECTED

CANCELLED

CONFLICT
Replay Rule
When a request arrives:

Known Operation ID
+
Identical Payload
The result must be:

Return Existing Outcome
without re-executing logic.

Conflict Rule
When a request arrives:

Known Operation ID
+
Different Payload
The result must be:

CONFLICT
Example:

Operation ID = op_100

Amount = 100
already exists.

Incoming request:

Operation ID = op_100

Amount = 200
Result:

CONFLICT
Checkpoint Replay Protection
Checkpoint processing uses:

checkpoint_id
authority_version
epoch
The same checkpoint may not be committed twice.

Authority Transfer Replay Protection
Authority transfers use:

transfer_id
authority_version
epoch
A completed authority transfer cannot execute again.

Soul Digit Replay Protection
Soul Digit minting uses:

work_id
attestation_id
checkpoint_id
operation_id
A mint operation may occur exactly once.

Double Mint Protection
Every mint request must bind to:

Verified Work
        ↓
Attestation
        ↓
Checkpoint Commit
Any attempt to process the same work again must be rejected.

Wallet Transfer Replay Protection
Wallet transfers must use:

transaction_id
operation_id
The same transfer may never create additional balance changes.

Escrow Replay Protection
Escrow operations must be protected.

Examples:

Reserve
Release
Refund
must never execute more than once.

Contract Replay Protection
Contract operations include:

Create
Accept
Complete
Fail
Cancel
Each operation must be replay-safe.

Mission Runtime Protection
Protected mission types:

Escort
Delivery
Crafting
Construction
War
Mission completion rewards must never execute twice.

Zone Transfer Protection
Zone transfers must use:

transfer_id
authority_version
checkpoint_reference
Duplicate transfers are invalid.

Community Protection
Replay protection applies to:

Voting
Treasury Spending
Community Merge
Community Rename
War Declaration
Governance decisions must not execute more than once.

Recovery Requirements
Replay records must survive:

Node Restart
Failover
Checkpoint Restoration
Runtime Migration
Replay state is part of authoritative world state.

Checkpoint Relationship
Replay protection and checkpoints are tightly coupled.

Every checkpoint should preserve:

Replay Records
Operation Status
Authority Metadata
A restored checkpoint must continue preventing replay.

Failover Requirements
Failover must not reset replay history.

Invalid sequence:

Operation Processed
        ↓
Node Failure
        ↓
Replay History Lost
        ↓
Operation Executes Again
This is prohibited.

Audit Requirements
Replay decisions should be logged.

Example:

Operation Received
Operation Accepted
Operation Replayed
Operation Rejected
Operation Conflict
Audit logs support investigations and recovery.

Security Requirements
Replay protection must provide:

Determinism
Consistency
Auditability
Double-Mint Protection
Double-Spend Protection
Replay failures are considered security incidents.

Alternatives Considered
Timestamp Only
Rejected because:

Clock Drift
Network Delay
Insufficient Identity
Memory-Only Tracking
Rejected because:

Lost On Restart
Lost On Failover
Best-Effort Detection
Rejected because:

Inconsistent Outcomes
Weak Guarantees
Consequences
Digit World permanently adopts:

Replay-Protected Operations
Idempotent Processing
Conflict Detection
Persistent Replay Records
for all critical systems.

All important world actions become safe against:

Duplicate Messages
Network Retries
Runtime Restart
Failover Replay
Checkpoint Reprocessing
References
Related Documents:

ARCHITECTURE.md
PROTOCOL.md
SECURITY_SPEC.md
COMPATIBILITY_SPEC.md
MIGRATION_SPEC.md

ADR-0002-verified-checkpoint.md
ADR-0003-soul-digit.md
ADR-0004-authority-transfer.md
Replay Protection is a foundational reliability and security mechanism for Digit World and is required for safe operation of all persistent world systems.