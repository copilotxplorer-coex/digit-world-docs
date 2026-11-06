Compatibility Specification
Purpose
This document defines the Compatibility System used by Digit World.

The Compatibility System ensures that all deployed components can safely operate together.

Compatibility validation protects the world from:

Invalid deployments
Asset conflicts
Ruleset mismatches
Checkpoint corruption
Runtime inconsistencies
Failed migrations
Compatibility Model
Every Digit World release consists of four independent versions.

Engine
+
Rulesets
+
Assets
+
Checkpoints
Together they define a valid world release.

Compatibility Layers
Engine Compatibility
The Engine provides core runtime functionality.

Examples:

Central Runtime
Region Runtime
Worker Runtime
Verification Runtime
Contract Runtime
Engine versions are authoritative.

Example:

{
  "engine_version": "1.0.0"
}
Ruleset Compatibility
Rulesets define world behavior.

Examples:

Combat
Economy
Governance
Contracts
Community
Example:

{
  "ruleset_version": "1.2.0"
}
Ruleset compatibility must be verified before activation.

Asset Compatibility
Assets define content.

Examples:

Items
Buildings
Creatures
Regions
Contracts
Example:

{
  "asset_pack_version": "1.5.0"
}
Assets may depend on:

Rulesets
Runtime Features
Other Assets
Checkpoint Compatibility
Checkpoints preserve world state.

Example:

{
  "checkpoint_version": "1.0.0"
}
Checkpoints must remain compatible with:

Engine
Rulesets
Assets
Compatibility Matrix
The compatibility matrix defines which combinations are valid.

Example:

{
  "engine_version": "1.0.0",
  "ruleset_version": "1.2.0",
  "asset_pack_version": "1.5.0",
  "checkpoint_version": "1.0.0",
  "compatible": true
}
Validation Flow
All releases must pass compatibility validation.

Engine
    ↓
Ruleset
    ↓
Assets
    ↓
Checkpoint
    ↓
Compatibility Check
    ↓
Deployment
Deployment must stop if any compatibility check fails.

Engine Compatibility Rules
Patch-Level Compatibility
Example:

Engine 1.0.0
Engine 1.0.1
Expected:

Compatible
Minor Version Compatibility
Example:

Engine 1.0.x
Engine 1.1.x
Compatibility is determined through migration rules.

Major Version Compatibility
Example:

Engine 1.x
Engine 2.x
Not automatically compatible.

Migration requirements apply.

Ruleset Compatibility Rules
Rulesets may evolve without modifying the Engine.

Example:

Combat v1
Combat v2
Allowed only when:

Compatibility Matrix
=
PASS
Asset Compatibility Rules
Assets must pass:

Schema Validation
Dependency Validation
Runtime Validation
Compatibility Validation
before inclusion in any release.

Asset Dependency Example
Creature
    ↓
Skill

Creature
    ↓
Drop Table

Region
    ↓
Neighbor Region
Assets with broken dependencies are incompatible.

Checkpoint Compatibility Rules
Each checkpoint should record:

{
  "asset_version": "1.5.0",
  "ruleset_version": "1.2.0",
  "engine_version": "1.0.0"
}
A checkpoint may only be restored if compatibility validation succeeds.

Runtime Compatibility
Runtime compatibility verifies:

Central Runtime
Region Runtime
Workers
Trusted Verifiers
All runtimes must support the deployed release.

Multi-Node Compatibility
Digit World supports multiple runtime nodes.

Before activation the system must verify:

Node A
Node B
Node C
all use:

Same Engine Version
Same Ruleset Version
Same Asset Version
unless an approved migration process is active.

Soul Digit Compatibility
The economy layer has additional restrictions.

The following components must remain compatible:

Ledger
Escrow
Reward Pool
Mint Pipeline
Double Mint Protection
Compatibility failures in economy systems are release blockers.

Verified Work Compatibility
Verified Work systems require:

Attestation
Checkpoint Commit
Mint Pipeline
to operate using compatible versions.

An incompatible deployment must reject mint operations.

Contract Compatibility
Contract Runtime components must verify:

Contract State Machine
Escrow Runtime
Mission Runtime
War Runtime
before activation.

Community Compatibility
Community Runtime components must verify:

Community Runtime
Election Runtime
Treasury Runtime
Governance Runtime
before activation.

Compatibility Levels
Fully Compatible
PASS
No migration required.

Compatible With Migration
MIGRATION_REQUIRED
Migration workflow required before activation.

Incompatible
FAIL
Deployment rejected.

Compatibility Status Codes
PASS
MIGRATION_REQUIRED
WARNING
DEPRECATED
FAIL
Release Train Integration
Compatibility validation occurs during:

Validation
↓
Review
↓
Release Candidate
↓
Production Release
No production release may bypass compatibility checks.

Rollback Compatibility
Rollback requires validation against:

Checkpoint
Ruleset
Assets
Engine
before activation.

Compatibility Metadata
Recommended release manifest:

{
  "engine_version": "1.0.0",
  "ruleset_version": "1.2.0",
  "asset_pack_version": "1.5.0",
  "checkpoint_version": "1.0.0",
  "compatibility_status": "PASS"
}
Compatibility Philosophy
Compatibility validation exists to protect:

World Integrity
Player Assets
Soul Digit Economy
Checkpoint Reliability
Multi-Node Stability
A deployment should never be activated simply because it can start.

A deployment should only be activated when it has been verified to be compatible with the world it intends to operate.