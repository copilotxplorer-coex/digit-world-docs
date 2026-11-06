Contributing
Thank you for contributing to Digit World.

Digit World is a long-term open-source MMORPG project designed around a persistent shared world architecture. Contributions of all sizes are welcome, including documentation, bug reports, asset packs, rulesets, tooling improvements, testing, and engine development.

Please read this document before opening an issue or submitting a pull request.

Core Philosophy
Digit World separates development into three major layers:

Engine
+
Rulesets
+
Content
Contributors should prefer extending content and rulesets whenever possible instead of modifying core engine systems.

This allows the project to grow while maintaining world stability.

Types of Contributions
Community members may contribute through:

Bug Reports
Feature Requests
Documentation
Asset Packs
Ruleset Packs
Testing
Tooling
Runtime Improvements
Pull Requests
Before You Start
Please read the following documents:

README.md
ARCHITECTURE.md
GOVERNANCE.md
ASSET_SPEC.md
RULESET_SPEC.md
These documents explain the project structure, governance model, and technical requirements.

Reporting Issues
When reporting a bug, include:

Environment
Engine Version
Ruleset Version
Asset Pack Version
Reproduction Steps
Provide clear steps to reproduce the issue.

Example:

1. Create Escort Contract
2. Accept Contract
3. Kill Client Character
4. Contract remains ACTIVE
Expected Result
Contract should transition to FAILED.
Actual Result
Contract remains ACTIVE.
Requesting Features
Feature requests should include:

Problem
Proposed Solution
Alternatives Considered
Potential Risks
Example:

Problem:
Contracts cannot support multiple escorts.

Solution:
Add support for group escort missions.
Development Workflow
All changes follow this workflow:

Fork
↓
Branch
↓
Develop
↓
Test
↓
Pull Request
↓
Review
↓
Merge
Direct commits to protected branches are not allowed.

Branch Naming
Recommended branch names:

feature/add-new-creature

feature/community-election

fix/checkpoint-attestation

docs/update-architecture

asset/forest-spider

ruleset/combat-v1-1
Pull Request Requirements
Every Pull Request should contain:

Description
Explain:

What changed
Why it changed
How it was tested
Scope
Pull Requests should focus on a single objective.

Good example:

Add Forest Spider Creature
Bad example:

Add Forest Spider
Rewrite Combat
Modify Economy
Update Contracts
Testing
Include evidence that the change works correctly.

Examples:

Unit Tests
Validation Results
Runtime Tests
Screenshots
Logs
Engine Contributions
Engine changes affect the entire world.

Examples:

Central Services
Region Runtime
Workers
Checkpoint System
Verification System
Networking
Requirements:

Passing Tests
Code Review
Maintainer Approval
Some changes may require additional security review.

Ruleset Contributions
Examples:

Combat Rules
Economy Rules
Community Rules
Contract Rules
Requirements:

Ruleset Validation
Compatibility Validation
Review Approval
Rulesets should remain backwards compatible whenever possible.

Asset Contributions
Asset Packs are the preferred way to add content.

Examples:

Items
Buildings
Creatures
Regions
Contracts
World Content
Asset submissions must pass:

Schema Validation
Dependency Validation
Compatibility Validation
before approval.

Asset Guidelines
Every asset must:

Have a unique ID
Example:

{
  "id": "forest_spider"
}
Declare a valid type
Example:

{
  "id": "forest_spider",
  "type": "creature"
}
Pass validation
Assets with missing references will be rejected.

Examples:

Missing Skill
Missing Drop Table
Missing Region Reference
Missing Contract Reference
Ruleset Guidelines
Rulesets should:

Be Versioned
Be Documented
Be Backward Compatible
Every Ruleset change should explain:

Why the change is necessary
Expected gameplay impact
Migration considerations
Documentation Contributions
Documentation improvements are always welcome.

Examples:

Architecture Explanations
Tutorials
Examples
API Documentation
Diagrams
Specifications
Documentation pull requests generally receive fast review.

Security Policy
Do not publicly disclose vulnerabilities that may:

Compromise Accounts
Compromise Soul Digit
Compromise Checkpoints
Compromise Verification Systems
Report security issues privately to project maintainers.

Soul Digit Restrictions
The following areas are highly sensitive:

Mint Logic
Ledger
Reward Formula
Reward Budget
Double Mint Protection
Checkpoint Settlement
Changes in these areas may require:

Security Review
Economy Review
Core Maintainer Approval
Commit Message Guidelines
Examples:

feat: add forest spider creature

fix: prevent duplicate checkpoint acceptance

docs: update governance specification

asset: add frontier village pack

ruleset: adjust transfer fee validation
Code Style
General guidelines:

Keep Changes Small
Prefer Readability
Write Tests
Document Public APIs
Avoid Dead Code
Consistency is more important than personal preference.

Review Process
Maintainers review submissions based on:

Correctness
Security
Maintainability
Performance
Compatibility
Documentation
Approval does not guarantee immediate release.

Merged changes enter the release pipeline.

Release Model
Digit World uses a release train model.

Contribution
→ Validation
→ Review
→ Merge
→ Staging
→ Release
→ Production
Changes become part of a scheduled release instead of going live immediately.

Community Expectations
Contributors are expected to:

Be Respectful
Be Constructive
Provide Evidence
Accept Feedback
Focus on Project Goals
Digit World is a collaborative long-term project.

Thank You
Every contribution helps improve the world.

Whether you submit code, assets, documentation, bug reports, tests, or ideas, thank you for helping Digit World grow.