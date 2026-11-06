Protocol Specification
Purpose
This document defines the communication protocols used within Digit World.

The protocol layer is responsible for providing deterministic, secure, versioned communication between:

Clients
Central Runtime
Region Runtime
Workers
Trusted Verifiers
Community Systems
Soul Digit Systems
The protocol specification exists to ensure interoperability, compatibility, auditability, and long-term maintainability.

Protocol Principles
Digit World protocols follow these principles:

Deterministic
Versioned
Replay Resistant
Idempotent
Auditable
Backward Compatible
Every protocol message must produce predictable and repeatable results.

Protocol Layers
Digit World uses multiple protocol layers.

Client Protocol
Runtime Protocol
Verification Protocol
Checkpoint Protocol
Contract Protocol
Community Protocol
Economy Protocol
Each layer is independently versioned.

Protocol Versioning
Every protocol message must declare a protocol version.

Example:

{
  "protocol_version": "1.0.0"
}
Protocol versions are verified before processing.

Common Message Structure
All protocol messages should follow a common structure.

{
  "message_id": "msg_001",
  "protocol_version": "1.0.0",

  "message_type": "example",

  "timestamp": "2026-01-01T00:00:00Z",

  "payload": {}
}
Message Identity
Every message requires a unique identifier.

{
  "message_id": "msg_001"
}
Purpose:

Replay Protection
Duplicate Detection
Audit Tracking
Idempotency
All important operations should be idempotent.

Example:

Same Message
+
Same Parameters
=
Same Result
Duplicate processing must not create:

Duplicate Contracts
Duplicate Wallet Credits
Duplicate Checkpoints
Duplicate Assets
Runtime Protocol
Used between:

Central
Region Runtime
Workers
Examples:

Region Assignment
Authority Transfer
Node Registration
Worker Coordination
Runtime Message Example
{
  "message_type": "runtime.assignment",

  "region": "frontier_r1a",

  "authority_version": 10
}
Authority Protocol
Authority messages control ownership.

Example:

{
  "message_type": "authority.transfer",

  "region": "frontier_r1a",

  "old_authority": 10,

  "new_authority": 11
}
Rules:

Old Authority
Rejected

Old Epoch
Rejected

Duplicate Transfer
Rejected
Checkpoint Protocol
Used by:

Runtime
Verifier
Central
Flow:

Checkpoint Propose
        ↓
Verify
        ↓
Attest
        ↓
Accept
        ↓
Commit
Checkpoint Messages
CHECKPOINT_PROPOSE
{
  "message_type": "CHECKPOINT_PROPOSE",

  "checkpoint_id": "cp_001"
}
VERIFY_REQUEST
{
  "message_type": "VERIFY_REQUEST",

  "checkpoint_id": "cp_001"
}
ATTESTATION
{
  "message_type": "ATTESTATION",

  "checkpoint_id": "cp_001"
}
ACCEPT
{
  "message_type": "ACCEPT",

  "checkpoint_id": "cp_001"
}
Verification Protocol
Used between:

Runtime
Trusted Verifier
Central
Verification messages must be auditable.

A verifier may:

Approve
Reject
Flag Conflict
A verifier may not directly modify world state.

Soul Digit Protocol
Used for:

Wallets
Escrow
Treasuries
Reward Pools
Minting
Wallet Messages
Transfer
{
  "message_type": "wallet.transfer",

  "wallet_from": "A",

  "wallet_to": "B",

  "amount": 100
}
Escrow
{
  "message_type": "wallet.escrow",

  "contract_id": "escort_001",

  "amount": 500
}
Verified Work Protocol
Used for:

Verification Work
Checkpoint Work
Replication Work
Community Work
Flow:

Work
 ↓
Attestation
 ↓
Checkpoint Commit
 ↓
Mint
Mint Messages
Mint Request
{
  "message_type": "mint.request",

  "work_id": "work_001",

  "reward_units": 10
}
Mint Receipt
{
  "message_type": "mint.receipt",

  "receipt_id": "receipt_001"
}
Contract Protocol
Used for:

Escort Contracts
Delivery Contracts
Crafting Orders
Construction Orders
War Contracts
Contract States
OPEN

ACCEPTED

COMPLETED

FAILED

CANCELLED
Contract Events
Create

Accept

Complete

Fail

Cancel
Escort Protocol
Special failure rule:

Client Dead
↓
FAILED
Example:

{
  "message_type": "escort.client_dead",

  "contract_id": "escort_001"
}
Community Protocol
Used for:

Membership
Residency
Governance
Treasury
Elections
Election Messages
Vote Cast
{
  "message_type": "election.vote",

  "candidate": "candidate_001"
}
Vote Count
{
  "message_type": "election.count"
}
Governance Messages
Examples:

War Declaration

Community Rename

Merge Approval

Treasury Approval
War Protocol
Used for:

War Contracts
War Objectives
War Funding
War Declaration
Example:

{
  "message_type": "war.declare",

  "target_community": "target_001"
}
Asset Protocol
Asset-related communication uses:

Registry Lookups

Asset Loading

Asset Validation

Asset Deployment
Assets should never be deployed without validation.

Ruleset Protocol
Used for:

Ruleset Loading
Ruleset Validation
Ruleset Activation
Example:

{
  "message_type": "ruleset.activate",

  "ruleset_version": "1.2.0"
}
Error Handling
Every protocol should return deterministic results.

Example:

{
  "status": "ERROR",

  "error_code": "INVALID_AUTHORITY"
}
Standard Status Codes
OK

REJECTED

CONFLICT

ERROR

INVALID

NOT_FOUND

UNAUTHORIZED
Replay Protection
Replay protection is mandatory.

Protected operations:

Mint
Checkpoint
Authority Transfer
Wallet Transfers
Contracts
Recommended keys:

message_id

operation_id

authority_version

checkpoint_id
Audit Requirements
Important protocol operations must be logged.

Examples:

Mint

Checkpoint Commit

Authority Transfer

Wallet Transfer

War Declaration
Audit logs support:

Investigation
Recovery
Rollback
Verification
Compatibility Requirements
Protocols must remain compatible with:

Engine Version
Ruleset Version
Asset Version
Checkpoint Version
Compatibility validation occurs before deployment.

Future Expansion
Planned future protocols include:

VR Protocol

AI Runtime Protocol

Marketplace Protocol

Transportation Protocol

Distributed Runtime Protocol
All future protocols must follow the same core design principles.

Final Rule
Protocol behavior must always be:

Deterministic
Versioned
Auditable
Replay Resistant
Protocol stability is considered critical infrastructure for the long-term operation of Digit World.