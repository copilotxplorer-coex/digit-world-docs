Digit World Architecture Foundation
Status
This package is an additive developer patch built on top of Runtime v0.3.5.

It is not the unreleased v0.3.6 Shared World implementation.

The Runtime version remains at 0.3.5 to avoid confusion with features that have not yet been delivered or installed.

This foundation establishes project structure and development boundaries without modifying the existing signed runtime release or production node environment.

Development Structure
The project separates responsibilities to allow parallel development.

central/
Central runtime entry point used for local development.

Current status:

Development Only
Not Yet VPS Service
launcher/
Adapter layer for the existing node launcher.

Current status:

Adapter Only
Not Yet NodeLauncher.exe
clients/cli/
Adapter layer for the current CLI implementation.

Current status:

Development Interface
clients/game2d/
References existing browser assets.

Current status:

Uses Existing Assets
No Asset Duplication
clients/game3d/
Reserved for future implementation.

Current status:

Planned
Not Implemented
node-server/
Reserved for future node runtime separation.

Current status:

Planned
Not Implemented
protocol/
Protocol ownership and validation layer.

Current responsibilities:

Component Ownership
Protocol Validation
Machine Readable Definitions
Status Tracking
workspace/
Local development environment.

Characteristics:

Temporary Workspace
No Access To Node Home
No Access To Profiles
No Access To Keys
Workspace is intended for safe local experimentation.

deploy/
Deployment planning layer.

Current status:

Local Environment
Staging Definition
Production Definition

No Auto Deploy
Runtime Integrity
This foundation does not:

Modify Existing Runtime Files
Modify Existing Signed Releases
Modify Production Nodes
Modify Production Keys
The purpose is to provide structure without impacting deployed environments.

Getting Started
Verify Only
py .\digit_world_patch_architecture_foundation.py . --verify-only
Apply Foundation Patch
py .\digit_world_patch_architecture_foundation.py .
Environment Validation
py -m workspace.dev check
Smoke Test
py -m workspace.dev smoke
Unit Tests
py -m unittest discover -v
Temporary Local Runtime
py -m workspace.dev local
The local runtime creates an isolated temporary environment.

Characteristics:

Temporary Database
Temporary Accounts
No Production Data
Open the generated:

/client2d
URL displayed by the runtime.

Local Development Rules
When testing locally:

Use Test Accounts Only
Use Separate Browser Profiles
Never Use Real Credentials
Never Use Production Profiles
All local data should be considered disposable.

Stopping the runtime:

Ctrl + C
will remove temporary state.

Open Source Development Workflow
Issues
Contributors should create issues describing:

Problem
Scope
Acceptance Criteria
before implementation.

Protocol First
When multiple teams work in parallel:

Central
Node
Client
communication protocols should be agreed upon before implementation begins.

Branches and Forks
Contributors should work through:

Feature Branches
Forks
using synthetic development environments.

Never submit:

Database Files
Profiles
Keys
Secrets
through pull requests.

Pull Requests
Every pull request should include:

Tests
Compatibility Notes
Migration Notes
Rollback Notes
where applicable.

Continuous Integration
Recommended CI requirements:

Windows Validation
Linux Validation
Synthetic Test Data
No Secrets
No Deployment
CI should focus on verification only.

Release Process
The release workflow is:

Development
        ↓
Review
        ↓
Merge
        ↓
Staging Validation
        ↓
Official Release
Only maintainers may approve official releases.

Repository Governance
Repositories should define:

Branch Protection
Required Reviews
Approval Rules
Release Policies
These settings are repository responsibilities and are not automatically configured by this foundation package.

Planned Next Steps
Central Authority
Design and implement:

Authority Ownership
Runtime Coordination
Secure Transport
for VPS deployment.

Node Identity
Develop:

Node Identity
Work Leases
Validation Rules
for distributed runtime operation.

Verified Contribution Ledger
Build the contribution verification system before:

Soul Digit Rewards
are enabled.

Patch Distribution
Define:

Patch Channels
Developer Signing
Official Signing
for controlled release distribution.

Production Client Builds
Future milestones include:

Launcher Executables
CLI Executables
2D Client Builds
3D Client Builds
for Windows deployment.

Out Of Scope
This foundation does not provide:

Soul Digit Rewards
Database Merge
Shared World Gameplay
Executable Builds
VPS Deployment
These capabilities will be delivered in future architecture phases.

Summary
Architecture Foundation establishes the baseline structure required for long-term development of Digit World.

The foundation provides:

Project Structure
Development Boundaries
Contribution Guidelines
Runtime Separation
Deployment Preparation
while intentionally avoiding direct modification of existing runtime, production nodes, or signed releases.