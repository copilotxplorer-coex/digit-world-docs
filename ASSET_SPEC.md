Asset Specification
Purpose
This document defines the Asset System used by Digit World.

Assets are the primary mechanism for adding game content without modifying Engine code.

Examples include:

Items
Buildings
Creatures
Regions
Contracts
Community Assets
World Assets
The Asset System is designed to support long-term world growth while maintaining compatibility with Runtime, Rulesets, and Checkpoints.

Design Principles
Digit World follows an Asset Driven Architecture.

Engine systems should define behavior.

Assets should define content.

Engine
    +
Rulesets
    +
Assets
    =
Gameplay
The preferred approach is:

Add Asset
instead of:

Modify Engine
whenever possible.

Asset Requirements
Every asset must contain:

{
  "id": "example_asset",
  "type": "example_type"
}
Required fields:

id
type
Asset IDs must be globally unique.

Asset Categories
Digit World currently supports the following asset categories.

Items
Examples:

Wood
Stone
Fiber
Soul Digit
Item assets define:

Stack Size
Weight
Trade Rules
Usage Rules
Buildings
Examples:

Walls
Houses
Repair Stations
Storage Buildings
Building assets define:

Health
Capacity
Services
Construction Requirements
Creatures
Examples:

Slime
Wolf
Boss Creatures
Creature assets define:

Stats
Skills
Drop Tables
AI Profiles
Regions
Examples:

Frontier
Forest
Desert
Mountain
Region assets define:

Region IDs
Neighbors
Authority Information
Runtime Ownership
Contracts
Examples:

Escort
Delivery
Crafting
Construction
War
Contract assets define:

Contract Type
Objectives
Rewards
Failure Conditions
Communities
Examples:

Community
Treasury
Governance
Residency
Community assets define:

Membership Rules
Governance Rules
Treasury Rules
Asset Structure
Recommended layout:

assets/
├─ items/
├─ buildings/
├─ creatures/
├─ regions/
├─ contracts/
├─ communities/
├─ world/
├─ localization/
└─ manifest.json
Versioning
Every Asset Pack should declare a version.

Example:

{
  "asset_pack": "frontier_starter",
  "asset_version": "1.0.0"
}
Asset versions are used by:

Runtime
Rulesets
Checkpoints
Deployment
Asset Registry
Assets are discovered through the Asset Registry.

Runtime flow:

Assets
    ↓
Asset Registry
    ↓
Asset Loader
    ↓
Dependency Resolver
    ↓
Runtime Integration
The Asset Registry is responsible for:

Asset Discovery
Asset Indexing
Asset Lookup
Dependency Tracking
Asset Loading
Assets are loaded through the Asset Loader.

Responsibilities:

Read JSON Assets
Validate Structure
Build Runtime Records
Resolve References
Assets that fail validation must not be loaded.

Dependency Resolution
Assets may reference other assets.

Examples:

Creature
    ↓
Skill

Creature
    ↓
Drop Table

Recipe
    ↓
Item

Region
    ↓
Neighbor Region
Dependencies are resolved through the Dependency Resolver.

Missing references are validation errors.

Asset Validation
All assets must pass validation before release.

Validation categories:

Schema Validation
Dependency Validation
Compatibility Validation
World Validation
Assets failing any validation stage must be rejected.

Asset Packs
Assets are distributed through Asset Packs.

Example:

Frontier Starter Pack
Forest Expansion Pack
Desert Expansion Pack
Asset Packs should not modify Engine code.

Asset Packs should remain self-contained whenever possible.

Ruleset Compatibility
Assets never operate independently.

Every deployed asset pack must be compatible with:

Engine Version
Ruleset Version
Compatibility is determined through the Compatibility Matrix.

Example:

{
  "engine_version": "1.0.0",
  "ruleset_version": "1.0.0",
  "asset_pack_version": "1.2.0"
}
Checkpoint Compatibility
Checkpoints must record Asset Versions.

Example:

{
  "checkpoint_id": "...",
  "asset_version": "1.2.0"
}
This prevents:

Checkpoint Created With Old Assets
+
New Asset Pack
=
Invalid World State
Runtime Integration
Assets become active only after Runtime Integration.

Examples:

Creature Asset
    ↓
Creature Runtime

Building Asset
    ↓
Building Runtime

Contract Asset
    ↓
Contract Runtime
The Engine remains authoritative.

Assets define data only.

Community Contributions
Community members are encouraged to contribute assets.

Examples:

New Creatures
New Regions
New Buildings
New Contracts
Requirements:

Unique IDs
Valid Schema
Valid Dependencies
Documentation
Successful Validation
Asset Review Levels
Low Risk
Examples:

Localization
Descriptions
Artwork References
Review Requirement:

1 Approval
Medium Risk
Examples:

Items
Buildings
Creatures
Review Requirement:

Validation
+
1 Approval
High Risk
Examples:

Economy Assets
Soul Digit Assets
Governance Assets
Review Requirement:

Validation
+
Maintainer Review
Asset Philosophy
The preferred way to expand Digit World is:

Add Assets
rather than:

Modify Engine
A stable Engine combined with community-created Assets allows the world to grow without introducing unnecessary technical risk.

Future Asset Types
Planned future asset categories include:

Animation Assets
VRM Assets
Audio Assets
Visual Effects Assets
Transportation Assets
AI Behavior Assets
Marketplace Assets
The Asset System is intentionally designed to support long-term world expansion without requiring major architectural changes.