ADR-0006: Contract-Driven Gameplay
Status: Accepted

Date: 2026-11-03

Decision Type: Architecture Decision Record

Context
Traditional MMORPGs typically rely on NPC quest systems.

Examples:

Kill Quests
Fetch Quests
Daily Quests
Scripted Content
Digit World seeks to create a player-driven economy and society.

The world should continue to generate meaningful gameplay regardless of developer-created content.

Problem
NPC-driven quests introduce several problems:

Static Content
Predictable Progression
Limited Emergent Gameplay
Artificial Economy
The project requires a system capable of generating gameplay from player activity alone.

Decision
Digit World adopts a:

Contract-Driven Gameplay Model
All major activities originate from player-created contracts.

Contract Types
Supported contracts include:

Escort
Delivery
Crafting
Construction
War
Future contract types may be added through Assets and Rulesets.

Contract Lifecycle
Create
    ↓
Escrow
    ↓
Open
    ↓
Accept
    ↓
Execute
    ↓
Complete / Fail
Escort Contracts
Example:

Player A
needs protection
to Region B
Failure Rule:

Client Death
      ↓
FAILED
Delivery Contracts
Example:

Deliver Resources
to another region
Completion:

Cargo Delivered
Failure:

Cargo Lost
Economic Integration
All contracts use:

Escrow
Soul Digit
Ledger
No reward is created from nothing.

Related Documents
PROTOCOL.md CONTRACT RUNTIME ADR-0003-soul-digit.md