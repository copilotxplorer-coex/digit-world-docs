Release Process
Purpose
This document defines the release process used by Digit World.

The release system exists to ensure:

World Stability
Safe Deployments
Deterministic Upgrades
Compatibility Validation
Controlled Rollouts
Reliable Recovery
No change should reach the production world without passing the release process.

Release Philosophy
Digit World uses a release train model.

Changes are collected, validated, and released in controlled batches.

Contribution
        ↓
Validation
        ↓
Review
        ↓
Merge
        ↓
Release Candidate
        ↓
Staging
        ↓
Production
This process reduces deployment risk and protects world integrity.

Release Components
Every release consists of four independent components.

Engine
Rulesets
Assets
Checkpoints
A release is only considered valid when all components are compatible.

Release Levels
Development Release
Purpose:

Feature Development
Testing
Experimental Changes
Environment:

Development Only
Requirements:

Basic Validation
Staging Release
Purpose:

Integration Testing
Compatibility Testing
Migration Testing
Environment:

Staging
Requirements:

Validation Passed
Review Passed
Compatibility Passed
Production Release
Purpose:

Live World Deployment
Environment:

Production
Requirements:

Validation Passed
Review Passed
Compatibility Passed
Migration Approved
Checkpoint Created
Release Train Model
Digit World uses scheduled releases.

Example:

Release 2026.11
Release 2026.12
Release 2027.01
Features are grouped into release trains.

Changes that miss a release train move to the next train.

Release Workflow
Step 1: Contribution
A contributor submits:

Code
Rulesets
Assets
Documentation
through Pull Requests.

Step 2: Validation
Automated systems execute:

Asset Validation
Dependency Validation
Ruleset Validation
Compatibility Validation
Tests
Failure blocks the release.

Step 3: Review
Appropriate maintainers perform review.

Examples:

Content Review
Ruleset Review
Security Review
Economy Review
depending on change type.

Step 4: Merge
Approved changes are merged.

Merge does not immediately create a release.

Merged changes enter the release candidate process.

Step 5: Release Candidate
A release candidate is generated.

Example:

RC-2026.11
Release candidates contain:

Engine Version
Ruleset Version
Asset Version
Migration Information
Step 6: Compatibility Verification
Compatibility checks include:

Engine Compatibility
Ruleset Compatibility
Asset Compatibility
Checkpoint Compatibility
The Compatibility Matrix must pass.

Step 7: Checkpoint Creation
Before production deployment:

Verified Checkpoint
must be created.

Checkpoint flow:

Checkpoint Proposal
        ↓
Verification
        ↓
Attestation
        ↓
Acceptance
        ↓
Commit
Only committed checkpoints may be used for deployment protection.

Step 8: Staging Deployment
Release candidates are deployed to staging.

Validation includes:

Runtime Validation
Checkpoint Validation
Governance Validation
Contract Validation
Economy Validation
Step 9: Production Approval
Appropriate maintainers approve production deployment.

Approval requirements depend on release contents.

Examples:

Engine Updates
Security Review Required

Economy Updates
Economy Review Required

Asset Updates
Content Review Required
Step 10: Production Deployment
Deployment occurs in controlled stages.

Prepare
        ↓
Deploy
        ↓
Verify
        ↓
Activate
Activation occurs only after verification succeeds.

Release Manifest
Each release should generate a manifest.

Example:

{
  "release_id": "2026.11",

  "engine_version": "1.0.0",

  "ruleset_version": "1.2.0",

  "asset_pack_version": "1.5.0",

  "checkpoint_id": "cp_001"
}
The release manifest becomes part of deployment records.

Migration Process
If migration is required:

Checkpoint
        ↓
Compatibility Check
        ↓
Migration
        ↓
Verification
        ↓
Release Activation
Migration must never bypass checkpoint creation.

Rollback Process
Rollback uses verified checkpoints.

Flow:

Deployment Failure
        ↓
Checkpoint Selection
        ↓
Compatibility Validation
        ↓
Rollback
        ↓
Verification
Rollback must preserve:

Wallets
Contracts
Communities
Treasuries
Authority State
Emergency Releases
Emergency releases are allowed for:

Security Vulnerabilities
Critical Runtime Failures
Economic Integrity Risks
Checkpoint Failures
Emergency releases still require:

Validation
Checkpoint Protection
Runtime Verification
Asset Releases
Asset Packs follow the same release process.

Examples:

New Creatures
New Buildings
New Regions
New Contracts
Asset Validation is mandatory before release.

Ruleset Releases
Rulesets are released independently.

Examples:

Combat Rules
Economy Rules
Governance Rules
Rulesets require:

Compatibility Validation
Migration Validation
before production activation.

Economy Releases
Economy-related releases are considered sensitive.

Examples:

Soul Digit
Mint Logic
Transfer Fees
Treasury Logic
Required:

Economy Review
Security Review
before deployment.

Governance Releases
Governance changes include:

Election Rules
Treasury Rules
War Rules
Community Rules
Governance releases must preserve world stability and compatibility.

CI/CD Integration
The release process is integrated with:

Asset Validation Workflow
Ruleset Validation Workflow
Pull Request Gates
Release Automation
All CI pipelines must pass before release progression.

Audit Records
Each release should generate:

Release Manifest
Compatibility Report
Validation Report
Migration Report
Deployment Report
These records support:

Auditing
Recovery
Investigation
Rollback
Release Statuses
PLANNED

IN_DEVELOPMENT

RELEASE_CANDIDATE

STAGING

APPROVED

DEPLOYED

ROLLED_BACK

CANCELLED
Long-Term Stability
Digit World prioritizes:

World Stability
Economic Stability
Checkpoint Integrity
Compatibility
over deployment speed.

A delayed release is preferable to a risky release.

Related Documents
README.md
ARCHITECTURE.md
GOVERNANCE.md
ASSET_SPEC.md
RULESET_SPEC.md
COMPATIBILITY_SPEC.md
MIGRATION_SPEC.md
SECURITY_SPEC.md
PROTOCOL.md
The Release Process is the final protection layer between development activity and the live world.