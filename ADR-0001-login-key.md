ADR-0001: Login Key Authentication
Status: Accepted

Date: 2026-11-03

Decision Type: Architecture Decision Record

Context
Digit World requires a long-term account authentication system suitable for:

Persistent World Operation
Open Source Development
Community Hosting
Multi-Node Runtime
Minimal Personal Data Collection
Earlier designs considered traditional username and password authentication.

During architecture review, several concerns were identified:

Password Storage Risk
Password Reset Complexity
Credential Leakage
Operational Overhead
Email Dependencies
Account Recovery Abuse
The project also aims to avoid collecting unnecessary personal information.

Problem
Traditional authentication introduces several long-term risks:

Operational Complexity
Password systems require:

Password Hashing
Password Reset Flows
Email Verification
Email Storage
Recovery Workflows
The world should not depend on external email providers or identity services.

Security Risks
Compromise scenarios include:

Password Reuse
Credential Stuffing
Email Hijacking
Password Recovery Abuse
These risks increase operational burden.

Open Source Considerations
Digit World may eventually be hosted by multiple operators.

The authentication model should:

Minimize Trust Requirements
Minimize Personal Data
Reduce Administrative Burden
Decision
Digit World adopts a Login Key Authentication Model.

Accounts are authenticated using:

Login Key
instead of:

Username + Password
for normal operation.

Authentication Flow
Account Creation
Create Account
        ↓
Generate Login Key
        ↓
Deliver Login Key
        ↓
Store Securely
Normal Login
Login Key
        ↓
Authentication
        ↓
Session Created
No password is required.

Password Migration
Legacy password-based accounts are supported only for migration.

Migration flow:

Password Login
        ↓
Generate Login Key
        ↓
User Saves Login Key
        ↓
Password Authentication Disabled
After successful migration:

Login Key Only
Non-Recoverable Design
Digit World intentionally uses a non-recoverable model.

If a Login Key is lost:

Account Access Is Lost
There is no:

Email Recovery
Password Recovery
Manual Recovery
Administrator Reset
User Warning Requirement
Users must receive a clear warning.

Example:

Your Login Key cannot be recovered.

If you lose the Login Key,
you will permanently lose access
to the account.
Security Benefits
Reduced Attack Surface
The following systems are eliminated:

Password Database
Password Reset Flow
Email Verification Flow
Recovery Database
Reduced Personal Data
The system does not require:

Email Address
Phone Number
Real Identity
unless future rules explicitly introduce optional features.

Simplified Operations
Server operators no longer need to manage:

Email Infrastructure
Password Recovery Requests
Forgot Password Support
Tradeoffs
Advantages
Lower Complexity
Lower Operating Cost
Lower Data Collection
Smaller Attack Surface
Open Source Friendly
Disadvantages
No Account Recovery
User Responsibility Increases
Login Key Storage Required
Users must take responsibility for protecting authentication credentials.

Compatibility Impact
Affected systems:

Authentication Runtime
Account Creation
Account Storage
Client Login UI
Documentation
Unaffected systems:

Contracts
Communities
Soul Digit
Checkpoint System
Region Runtime
Combat
Migration Requirements
All password-based accounts must support:

One-Time Password Login
for conversion into:

Login Key Authentication
A migration report should be recorded.

Security Requirements
Login Keys must:

Be Unique
Be Unpredictable
Be High Entropy
Be Non-Recoverable
Replay protection remains enforced by existing session systems.

Alternatives Considered
Traditional Password Authentication
Rejected because:

Higher Complexity
Email Dependency
Recovery Complexity
Larger Attack Surface
Email-Based Authentication
Rejected because:

External Dependency
Identity Collection
Recovery Abuse Risk
Social Login
Rejected because:

Third-Party Dependency
Vendor Lock-In
Privacy Concerns
Consequences
Digit World permanently adopts:

Login Key Authentication
as the primary account access mechanism.

Password authentication exists only as a migration tool for legacy accounts and is not considered part of the long-term architecture.

References
Related documents:

ARCHITECTURE.md
SECURITY_SPEC.md
PROTOCOL.md
MIGRATION_SPEC.md
GOVERNANCE.md
This ADR is considered a foundational security decision for the Digit World project.