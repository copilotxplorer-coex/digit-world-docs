ADR-0007: Community Governance
Status: Accepted

Date: 2026-11-03

Decision Type: Architecture Decision Record

Context
Digit World allows players to form communities.

Communities require mechanisms for:

Leadership
Treasury Management
Elections
War Decisions
Community Expansion
Problem
Without governance rules:

Treasuries become unsafe
Leadership becomes unclear
Community decisions become arbitrary
The project requires a transparent community governance model.

Decision
Digit World adopts:

Leader + Council Governance
Community Structure
Community
│
├─ Leader
├─ Council
└─ Members
Leadership
Leaders are selected through periodic evaluation.

Leaders may:

Approve Membership
Approve Treasury Actions
Declare War
Approve Community Names
Council
The council contains:

10 Members
Council members are elected by community members.

Council Voting
Standard Approval:

6 / 10 votes
required.

Treasury Governance
Treasury spending requires:

Leader Approval

OR

Council Approval
depending on current governance conditions.

Community Merge
Communities may merge.

Governance systems determine:

Leadership
Treasury Ownership
Community Name
after merge.

War Governance
War declarations follow governance rules.

Possible paths:

Leader Decision

OR

Council Vote
Related Documents
E1 Community Runtime

E2 Election Runtime

E3 Treasury Runtime

E4 Governance Runtime