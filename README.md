High-Level Description of the Mapping:
📌 Purpose:
The document maps student course enrollment events from Destiny One to Blackboard, enabling automatic real-time syncing of enrollment, withdrawal, or transfers via MuleSoft (an iPaaS solution).


🔄 Integration Flow Breakdown:
1. Source System: Destiny One
The leftmost section (SOURCE System Attributes) lists the data attributes from Destiny One's APIs or DB.

Example fields: student.loginId, use.objectId, student.firstName1, student.lastName, etc.

These are the raw values collected when a student enrolls, withdraws, or transfers in Destiny One.

2. ETL Layer: MuleSoft (iPaaS)
The middle section (ETL Layer) represents the transformations or filters applied in MuleSoft before pushing to Blackboard.

Includes:

Selection logic: e.g., only process if activityCode = 'Sale'

Transformation logic: e.g., converting timestamps to epoch in the US/Eastern timezone

Field combinations using concat(), e.g., course code + semester + section code

This is where MuleSoft transforms data to meet Blackboard's API schema.

3. Target System: Blackboard
The right section (TARGET System Attributes) shows the mapped fields expected by Blackboard’s API.

Example target fields:

userName (String) ← From student.loginId

externalId (String) ← Course External ID from Destiny One

courseRoleId, dataSourceId, etc.

These fields are used in Blackboard to identify users, courses, and roles.

