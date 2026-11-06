Ruleset Specification
Purpose
This document defines the Ruleset System used by Digit World.

Rulesets control how the world behaves without requiring modifications to the Engine.

The purpose of Rulesets is to:

Separate gameplay logic from engine code
Allow balancing without engine updates
Support long-term world evolution
Enable controlled experimentation
Maintain compatibility across releases
Core Philosophy
Digit World separates:

Engine
+
Rulesets
+
Assets
=
World Behavior
The Engine provides capabilities.

Rulesets define policy.

Assets define content.

Ruleset Categories
Rulesets are divided into several domains.

Combat Rulesets
Control:

Combat Behavior
Damage Models
Status Effects
Weapon Rules
Durability Rules
PvP Rules
PvE Rules
Examples:

combat_v1
combat_v2
Economy Rulesets
Control:

Soul Digit Distribution
Transfer Fees
Reward Pools
Escrow Rules
Marketplace Rules
Examples:

economy_v1
economy_v2
Community Rulesets
Control:

Community Membership
Residency Rules
Merge Rules
Governance Rules
Examples:

community_v1
community_v2
Contract Rulesets
Control:

Escort Rules
Delivery Rules
Crafting Orders
Construction Orders
War Contracts
Examples:

contracts_v1
contracts_v2
Governance Rulesets
Control:

Elections
Treasury Approval
Council Voting
War Declarations
Examples:

governance_v1
governance_v2
Ruleset Structure
Every Ruleset must contain:

{
  "id": "combat_v1",
  "type": "combat_ruleset",
  "version": "1.0.0"
}
Required fields:

id
type
version
Versioning
Rulesets are versioned independently from Engine releases.

Example:

{
  "id": "economy_v1",
  "type": "economy_ruleset",
  "version": "1.0.0"
}
Versioning allows:

Safe upgrades
Compatibility checking
Migration planning
Rollback support
Ruleset Repository
Rulesets are stored separately from Engine code.

Recommended structure:

rulesets/
├─ combat/
├─ economy/
├─ contracts/
├─ governance/
└─ community/
This separation allows balancing changes without changing runtime infrastructure.

Runtime Loading
Rulesets are loaded through:

Ruleset Schema
        ↓
Ruleset Loader
        ↓
Compatibility Matrix
        ↓
Runtime Integration
A Ruleset that fails validation must not be activated.

Active Ruleset Selection
A world release references specific versions.

Example:

{
  "engine_version": "1.0.0",
  "ruleset_version": "1.2.0",
  "asset_pack_version": "1.1.0"
}
Only compatible combinations may be activated.

Compatibility Matrix
Rulesets are validated against:

Engine Version
Asset Pack Version
Checkpoint Version
Example:

{
  "engine_version": "1.0.0",
  "ruleset_version": "1.2.0",
  "compatible": true
}
Rulesets that are incompatible must be rejected.

Rule Changes
Rule changes should be treated differently from content changes.

Examples:

Content Change
Add Creature
Add Building
Add Region
Low Risk

Ruleset Change
Change Combat Formula
Change Soul Digit Fee
Change Contract Logic
Higher Risk

Ruleset updates affect the entire world.

Checkpoint Integration
Rulesets are checkpoint-aware.

Every checkpoint should store:

{
  "checkpoint_id": "...",
  "ruleset_version": "1.2.0"
}
This prevents invalid state restoration after a ruleset update.

Soul Digit Rulesets
Economy Rulesets govern:

Transfer Fees
Reward Pools
Treasury Policies
Escrow Policies
New Soul Digit must only be created through:

Verified Useful Work
        ↓
Attestation
        ↓
Checkpoint Commit
        ↓
Mint
Rulesets may influence reward allocation but must not bypass verification requirements.

Contract Rulesets
Contract Rulesets govern:

Escort Contracts
Delivery Contracts
Crafting Orders
Construction Orders
War Contracts
Examples:

Failure Conditions
Reward Distribution
Escrow Handling
Timeout Rules
Community Rulesets
Community Rulesets govern:

Membership
Residency
Merging
Community Authority
Examples:

House Capacity
Community Merge Conditions
Residency Assignment
Governance Rulesets
Governance Rulesets define:

Leader Elections
Council Elections
Treasury Approval
War Approval
Rename Policies
These rules determine how communities make decisions.

Validation Requirements
Every Ruleset must pass:

Schema Validation
Compatibility Validation
Dependency Validation
Runtime Validation
before release.

Review Requirements
Rulesets require stricter review than content.

Standard Rules
Examples:

Combat
Contracts
Community
Minimum:

2 Approvals
Economy Rules
Examples:

Soul Digit
Reward Pool
Escrow
Fees
Minimum:

Economy Review
+
2 Approvals
Security Sensitive Rules
Examples:

Mint Logic
Checkpoint Acceptance
Verification Rules
Minimum:

Security Review
+
Core Maintainer Approval
Deployment Model
Rulesets are deployed through release trains.

Author
    ↓
Validation
    ↓
Review
    ↓
Merge
    ↓
Staging
    ↓
Release
    ↓
Production
Rulesets must never be modified directly in production.

Rollback Policy
If a Ruleset causes unexpected behavior:

Release
    ↓
Detect Issue
    ↓
Rollback
Rollback must restore:

Ruleset Version
Compatibility State
Checkpoint Compatibility
Future Rulesets
Planned future domains include:

Transportation Rules
Trade Rules
AI Behavior Rules
Faction Rules
World Event Rules
VR Runtime Rules
The Ruleset System is designed to support long-term evolution without requiring fundamental Engine changes.

Guiding Principle
The preferred solution is:

Modify Ruleset
before

Modify Engine
A stable Engine combined with versioned Rulesets enables Digit World to evolve safely while preserving world integrity and backward compatibility.