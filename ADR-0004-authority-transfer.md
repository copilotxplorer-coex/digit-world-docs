ADR-0004: Authority Transfer and Region Ownership
Status: Accepted

Date: 2026-11-03

Decision Type: Architecture Decision Record

Context
Digit World is designed as a multi-node persistent world.

World simulation is distributed across runtime nodes while maintaining:

Single Shared World
Single Authority Per Region
Replay Protection
Verified Checkpoints
Deterministic Recovery
A mechanism is required to safely transfer ownership of a region between runtime nodes without introducing:

Duplicate Authority
Split Brain
Replay Processing
State Corruption
Character Duplication
Economic Corruption
Problem
Regions may require authority transfer because of:

Node Failure
Node Recovery
Load Balancing
Zone Transfer
Maintenance
Infrastructure Upgrades
Without a formal authority system the world becomes vulnerable to:

Two Nodes Processing The Same Region
Lost Updates
Replay Events
Double Mint
Double Spend
Invalid Recovery
The system must guarantee that only one runtime is authoritative for a region at any moment.

Decision
Digit World adopts an Authority Transfer Architecture.

Each region has:

Region ID
Epoch
Authority Version
Current Owner Runtime
Authority transfers are coordinated through the Central Runtime.

Authority ownership is never inferred from:

Timeouts
Assumptions
Local Runtime State
Authority changes must be explicitly committed.

Core Principle
The system enforces:

One Region
        ↓
One Authority
        ↓
One Epoch
at all times.

Any situation where two runtimes believe they own the same region is invalid.

Region Ownership Model
Each region maintains:

{
  "region": "frontier_r1a",

  "epoch": 10,

  "authority_version": 25,

  "owner": "runtime_a"
}
Authority Version
Authority ownership changes increment:

authority_version
Example:

Authority Version 25
            ↓
Transfer
            ↓
Authority Version 26
Older authority versions become invalid.

Epoch Model
Epochs provide protection against stale runtimes.

Example:

Epoch 10
Runtime messages from:

Epoch 9
must be rejected.

Authority Transfer Flow
Normal transfer process:

Current Authority
        ↓
Prepare Target
        ↓
Create Transfer Record
        ↓
Commit Transfer
        ↓
Activate Target
        ↓
Fence Previous Authority
Transfer State Machine
ACTIVE
        ↓
PREPARING_TARGET
        ↓
HANDOFF_PENDING
        ↓
TRANSFER_COMMITTED
        ↓
TARGET_ACTIVE
Source Runtime Requirements
Before releasing authority:

The source runtime must:

Stop New Authority Decisions
Flush Pending State
Prepare Transfer Package
Provide Handoff State
The source runtime may not continue operating after transfer commit.

Target Runtime Requirements
Before activation:

The target runtime must verify:

Authority Version
Epoch
Checkpoint Consistency
Dependencies
before accepting ownership.

Fencing Requirement
After authority transfer:

Old Runtime
must be fenced.

Fenced runtimes may:

Read
Verify
Observe
but may not:

Write State
Execute Authority Actions
Process Transfers
Mint Rewards
Replay Protection
Authority transfers are replay protected.

Protected identifiers:

transfer_id
authority_version
epoch
checkpoint_id
A previously completed transfer must never execute twice.

Verified Checkpoint Dependency
Authority transfer depends on a trusted state.

Transfer source must originate from:

Verified Checkpoint
or

Verified Runtime State
Unverified state cannot become authoritative.

Failover Transfer
Failover flow:

Node Failure
        ↓
Latest Verified Checkpoint
        ↓
Authority Reassignment
        ↓
New Runtime Activation
Failover must not create:

Duplicate Regions
Duplicate Characters
Duplicate Contracts
Duplicate Currency
Zone Transfer Relationship
Zone transfer and authority transfer are independent concepts.

Zone transfer:

Character Movement
Authority transfer:

Runtime Ownership
A character may move between regions without transferring region authority.

Character Transfer Safety
Authority change must preserve:

Character State
Inventory
Cooldowns
Reservations
Pending Operations
Transfer completion must not:

Duplicate Character State
Lose Character State
Reset Cooldowns
Reset Timers
Community Protection
Authority transfers must preserve:

Community Membership
Leadership
Council Membership
Treasury
War State
No governance state may be lost during transfer.

Soul Digit Protection
Authority transfer is a protected economic event.

The following must remain consistent:

Wallets
Escrow
Treasuries
Reward Pools
Mint Records
Authority transfer must never cause:

Double Mint
Double Spend
Balance Duplication
Contract Protection
Authority transfer must preserve:

Escort Missions
Delivery Missions
Crafting Orders
Construction Orders
War Contracts
Contract state transitions must remain valid.

Restoration Requirements
After restart:

A runtime must verify:

Current Epoch
Current Authority Version
Current Owner
before accepting authority.

Local memory is not authoritative.

Invalid States
The following conditions are invalid:

Dual Authority
Runtime A owns region
Runtime B owns region
Rejected.

Stale Authority
Authority Version 24

Current Version 25
Rejected.

Stale Epoch
Epoch 9

Current Epoch 10
Rejected.

Unknown Checkpoint
Transfer References
Unknown Checkpoint
Rejected.

Authority Audit Requirements
Every authority transfer should produce:

Transfer Record
Epoch Record
Authority Record
Checkpoint Reference
Audit Log
These records support:

Recovery
Verification
Investigation
Rollback Analysis
Transfer Manifest Example
{
  "transfer_id": "transfer_001",

  "region": "frontier_r1a",

  "epoch": 10,

  "authority_version": 26,

  "source_runtime": "runtime_a",

  "target_runtime": "runtime_b"
}
Security Requirements
Authority Transfer must provide:

Single Ownership
Replay Resistance
Checkpoint Awareness
Epoch Validation
Authority Validation
Authority ownership is considered a security-critical subsystem.

Alternatives Considered
Timeout-Based Ownership
Owner Silent
↓
Assume New Owner
Rejected.

Reason:

Network Delays
False Positives
Split Brain Risk
Multi-Writer Regions
Rejected.

Reason:

Non-Deterministic State
Conflict Risk
Duplicate Processing
Database Ownership Only
Rejected.

Reason:

No Runtime Validation
No Authority Tracking
No Epoch Protection
Consequences
Digit World permanently adopts:

Single Authority Per Region
Authority Versioning
Epoch Validation
Checkpoint-Aware Transfers
Runtime Fencing
Authority Transfer becomes the foundation for:

Failover
Recovery
Scaling
Region Ownership
Multi-Node Runtime
References
Related Documents:

ARCHITECTURE.md
PROTOCOL.md
SECURITY_SPEC.md
MIGRATION_SPEC.md
COMPATIBILITY_SPEC.md
ADR-0002-verified-checkpoint.md
ADR-0003-soul-digit.md
Authority Transfer is considered a core infrastructure component required for safe multi-node operation in Digit World.