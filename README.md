Digit World
Digit World is an open-source MMORPG project focused on building a persistent single shared world that can continue to evolve for many years through community-driven development.

The goal of the project is not only to create a game, but to establish a long-term virtual world platform that can be maintained, expanded, and governed without depending on a single development team.

Vision
Digit World is built around the following principles:

Single Shared World
Open Source Development
Community Driven Content
Versioned Rulesets
Asset Driven Architecture
Verified Work Economy
Long-Term Persistence
Multi-Node Scalability
The world should be capable of continuing its existence even if the original development team changes over time.

Core Principles
Separation of Engine, Rulesets, and Content
Digit World separates the system into three independent layers.

Engine
The Engine is responsible for:

Runtime Systems
Networking
Checkpoints
Verification
Community Systems
Contract Systems
Multi-Node Infrastructure
Rulesets
Rulesets define how the world behaves:

Combat Rules
Economy Rules
Community Rules
Governance Rules
Reward Rules
Rulesets can evolve independently without changing the Engine.

Content
Content is provided through Asset Packs:

Items
Buildings
Creatures
Regions
Contracts
Communities
World Assets
Content contributors should generally be able to add new gameplay content without modifying Engine code.

Soul Digit
Soul Digit is the primary currency of Digit World.

A fundamental design rule is:

New Soul Digit can only be created through Verified Useful Work.

Examples include:

Verification Work
Checkpoint Work
Replication Work
Community Projects
Soul Digit is not generated from:

Login Rewards
NPC Quest Rewards
Monster Money Drops
Uptime Rewards
Idle Resource Farming
This design helps maintain a stable economy and reduces abuse.

Contract Driven Gameplay
Digit World replaces traditional NPC quest systems with Player Contract Systems.

Examples include:

Escort Contracts
Delivery Contracts
Crafting Contracts
Construction Contracts
War Contracts
Rewards are managed through escrow mechanisms and can be verified through the world state.

Community Governance
Communities in Digit World are able to:

Elect Leaders
Elect Community Councils
Manage Community Treasuries
Rename Communities
Merge Communities
Declare Wars
Governance behavior is defined through configurable Rulesets.

Repository Layout
digit-world-engine
Contains core runtime and infrastructure systems:

Central Services
Region Runtime
Workers
Verification Services
Runtime Components
digit-world-assets
Contains Asset Packs used to define world content:

Items
Buildings
Creatures
Regions
Contracts
Community Assets
digit-world-rulesets
Contains configurable gameplay and governance rules:

Combat Rules
Economy Rules
Community Rules
Governance Rules
digit-world-docs
Contains architecture, specifications, governance, and development documentation.

Development Model
Community members can contribute through:

Issues
Discussions
Documentation
Asset Packs
Rulesets
Pull Requests
All changes follow the workflow:

Validation
→ Review
→ Release Train
→ Deployment
before reaching the production world.

Project Roadmap
Phase A
Asset Foundation

Phase B
Ruleset Foundation

Phase C
Soul Digit Foundation

Phase D
Contract Runtime Foundation

Phase E
Community Runtime Foundation

Phase F
Asset Runtime Integration

Phase G
GitHub Organization and CI/CD

Getting Started
Recommended reading order:

ARCHITECTURE.md
GOVERNANCE.md
CONTRIBUTING.md
ASSET_SPEC.md
RULESET_SPEC.md
These documents provide a complete overview of the project architecture and development process.

Contributing
Contributions are welcome.

Before submitting changes, please review:

CONTRIBUTING.md
GOVERNANCE.md
ASSET_SPEC.md
RULESET_SPEC.md
for project-specific requirements and standards.

License
Please refer to the LICENSE file included in the repository.