Governance
Purpose
This document defines how Digit World is maintained, governed, reviewed, and evolved over time.

The project is designed to remain operational and maintainable for the long term regardless of changes in individual contributors, maintainers, or organizations.

The purpose of governance is to:

Protect world stability
Protect player assets
Prevent malicious changes
Enable open-source collaboration
Allow community-driven growth
Ensure transparent decision making
Governance Principles
Digit World follows five core principles:

World Stability First
Transparency
Reproducibility
Community Participation
Separation of Responsibilities
The project favors stability and continuity over rapid change.

Governance Structure
Core Maintainers
        │
        ├── Security Group
        ├── Economy Council
        ├── Ruleset Maintainers
        └── Content Maintainers
Each group has clearly defined responsibilities.

Core Maintainers
Core Maintainers are responsible for the foundational systems of Digit World.

Responsibilities:

Runtime Architecture
Central Services
Region Runtime
Checkpoint System
Verification System
Security
Release Approval
Examples:

Engine Runtime
Multi-Node Infrastructure
Trusted Verifier
Authority Management
Checkpoint Acceptance
Core Maintainers may approve:

Engine Changes
Security Patches
Infrastructure Changes
Security Group
The Security Group reviews sensitive changes.

Responsibilities:

Security Audits
Vulnerability Analysis
Exploit Prevention
Ledger Protection
Soul Digit Protection
Required review areas:

Authentication
Login Key Systems
Checkpoint Security
Mint Logic
Economic Integrity
Economy Council
The Economy Council oversees economic balance.

Responsibilities:

Soul Digit Rules
Reward Pools
Fees
Treasury Rules
Marketplace Rules
The Council does not directly modify Engine code.

The Council proposes adjustments through Ruleset changes.

Ruleset Maintainers
Ruleset Maintainers manage gameplay rules.

Examples:

Combat Rules
Community Rules
Governance Rules
Contract Rules
Rulesets are versioned independently from Engine releases.

Content Maintainers
Content Maintainers review gameplay content.

Examples:

Creatures
Items
Buildings
Regions
Contracts
Asset Packs
Content changes should normally not require Engine modifications.

Contributors
Anyone may contribute to the project.

Contribution methods:

Issues
Documentation
Asset Packs
Rulesets
Pull Requests
Contributors do not receive direct commit access automatically.

Pull Request Policy
All changes must be submitted through Pull Requests.

Direct commits to protected branches are prohibited.

Minimum requirements:

Passing CI checks
Valid Asset Validation
Valid Ruleset Validation
Review Approval
Approval Requirements
Content Changes
Examples:

New Creature
New Building
New Region
Requirements:

1 Approval
Ruleset Changes
Examples:

Combat Balance
Contract Rules
Community Rules
Requirements:

2 Approvals
Economy Changes
Examples:

Reward Pool
Fees
Soul Digit Distribution
Requirements:

Economy Council Review
2 Approvals
Security Changes
Examples:

Checkpoints
Authentication
Mint Logic
Ledger
Requirements:

Security Review
2 Core Maintainer Approvals
Release Process
Changes do not become live immediately after merge.

Workflow:

Contribution
        ↓
Validation
        ↓
Review
        ↓
Merge
        ↓
Release Train
        ↓
Deployment
Production releases follow scheduled release trains.

Asset Governance
Assets are community-driven.

Asset submissions include:

Creatures
Items
Buildings
Regions
Contracts
Assets must pass:

Schema Validation
Dependency Validation
Compatibility Validation
before inclusion in a release.

Ruleset Governance
Rulesets are versioned.

A world release references:

Engine Version
Ruleset Version
Asset Pack Version
Changes to Rulesets are tracked independently.

Soul Digit Governance
Soul Digit is a protected subsystem.

The following components require elevated review:

Mint Pipeline
Reward Formula
Reward Budget
Ledger
Double Mint Protection
New Soul Digit may only be created through:

Verified Useful Work
        ↓
Attestation
        ↓
Checkpoint Commit
        ↓
Mint
Community Governance
In-game communities may govern themselves through:

Elections
Councils
Treasury Management
Community Decisions
Community governance does not override project governance.

Conflict Resolution
If contributors disagree:

Discussion
Maintainer Review
Governance Decision
Final Project Decision
All decisions should be publicly documented whenever possible.

Documentation Requirement
Major decisions must be recorded.

Recommended location:

docs/adr/
Examples:

ADR-0001-login-key.md
ADR-0002-verified-checkpoint.md
ADR-0003-soul-digit-mint.md
ADR-0004-contract-system.md
Long-Term Goal
Digit World aims to become a sustainable, community-maintained virtual world.

The governance model exists to balance:

Stability
Security
Openness
Innovation
while protecting the integrity of the world and its players.