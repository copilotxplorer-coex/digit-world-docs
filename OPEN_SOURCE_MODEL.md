Open Source Model
Purpose
This document defines how Digit World operates as an open-source project.

The goal is to allow long-term community participation while protecting:

World Stability
Player Assets
Soul Digit Integrity
Runtime Security
Community Governance
Digit World is designed to outlive any individual contributor, maintainer, or organization.

Vision
Digit World is an open-source persistent world.

The project aims to create a long-lived virtual world where:

Engine
+
Rulesets
+
Assets
+
Community
=
Living World
The world should continue evolving without requiring ownership by a single company or developer.

Core Principles
Digit World follows the following principles:

Transparency
Merit-Based Contributions
Long-Term Stability
Open Participation
Deterministic Systems
World Integrity
The project favors sustainable growth over rapid experimentation.

Open Source Philosophy
Digit World is not only a game project.

Digit World is also:

Platform
Community
World Infrastructure
Open Source Ecosystem
The project is designed so future contributors can continue development without needing access to internal knowledge.

Separation of Responsibilities
Digit World separates development into independent domains.

Engine
Rulesets
Assets
Documentation
Each domain has different review requirements.

Engine Layer
Engine contributors work on:

Central Runtime
Region Runtime
Workers
Checkpoint System
Verification System
Network Systems
Engine development prioritizes:

Stability
Security
Backward Compatibility
Ruleset Layer
Rulesets control world behavior.

Examples:

Combat Rules
Economy Rules
Community Rules
Contract Rules
Governance Rules
Rulesets evolve independently from the Engine.

Asset Layer
Assets define gameplay content.

Examples:

Items
Buildings
Creatures
Contracts
Regions
Communities
Most community contributions should occur at the asset layer.

The preferred way to expand the world is:

Add Assets
instead of:

Change Engine Code
Documentation Layer
Documentation is treated as a first-class contribution type.

Documentation includes:

Architecture
Specifications
Tutorials
Examples
Governance
Documentation changes are encouraged.

Repository Structure
Digit World is organized into separate repositories.

digit-world-engine
digit-world-assets
digit-world-rulesets
digit-world-docs
This prevents unrelated contributions from becoming coupled.

Contribution Model
Community members may contribute through:

Issues
Discussions
Documentation
Assets
Rulesets
Source Code
Pull Requests
Every contribution follows the same review process.

Contribution Workflow
Fork
      ↓
Branch
      ↓
Development
      ↓
Validation
      ↓
Pull Request
      ↓
Review
      ↓
Merge
      ↓
Release Train
No contributor receives direct production access.

Review Model
Review requirements depend on risk level.

Low Risk
Examples:

Documentation
Localization
Examples
Typical requirement:

1 Approval
Medium Risk
Examples:

Creatures
Buildings
Regions
Contracts
Typical requirement:

Validation
+
1 Approval
High Risk
Examples:

Engine Changes
Economy Changes
Checkpoint Logic
Authority Logic
Typical requirement:

Maintainer Review
+
Multiple Approvals
Governance Model
Governance is defined separately in:

GOVERNANCE.md
Major groups include:

Core Maintainers
Security Reviewers
Economy Council
Ruleset Maintainers
Content Maintainers
Contributors
Each group has specific responsibilities.

Community Contributions
The project encourages:

New Asset Packs
New Regions
New Creatures
New Contracts
Documentation Improvements
Tooling Improvements
Contributors do not need Engine access to expand the world.

Protected Areas
Certain systems are considered critical infrastructure.

Examples:

Soul Digit Minting
Ledger
Checkpoint Processing
Authority Transfer
Authentication
Changes affecting these areas require enhanced review.

Release Model
Digit World uses release trains.

Changes do not become active immediately after merge.

Workflow:

Contribution
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
This protects world stability.

Asset Validation
All asset contributions must pass:

Schema Validation
Dependency Validation
Compatibility Validation
before inclusion in a release.

Ruleset Validation
Rulesets must pass:

Ruleset Validation
Compatibility Validation
Migration Validation
before release.

Security Expectations
Contributors are expected to:

Protect Credentials
Report Vulnerabilities
Respect Security Boundaries
Avoid Exploit Disclosure
Security concerns should be reported privately.

Open Discussion
Technical discussions are welcome.

Examples:

Architecture
Gameplay
Economy
Governance
Runtime Scaling
Discussion should focus on improving the world.

Decision Records
Major technical decisions should be documented.

Recommended location:

docs/adr/
Examples:

ADR-0001-login-key.md
ADR-0002-verified-checkpoint.md
ADR-0003-soul-digit.md
ADR-0004-authority-transfer.md
ADR-0005-replay-protection.md
This allows future contributors to understand historical decisions.

Project Sustainability
Digit World is designed to remain maintainable for many years.

To support long-term sustainability:

Engine Stability
Versioned Rulesets
Asset Driven Content
Documented Governance
Deterministic Runtime
are prioritized over short-term convenience.

Community Standards
Contributors should:

Be Respectful
Be Constructive
Provide Evidence
Document Changes
Accept Review Feedback
The project values collaboration over ownership.

Long-Term Goal
The long-term goal of Digit World is:

A Community Maintained
Persistent Open World
Built On
Transparent Open Source Foundations
The open-source model exists to ensure that the world can continue to grow, evolve, and remain accessible far into the future.