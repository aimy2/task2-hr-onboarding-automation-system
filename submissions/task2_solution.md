# Task 2 Solution — Advanced Airtable Automation

## 1) Automation Steps
1. **Trigger**: `When record matches conditions` in `New Hires` table where `{Status} = "High Value"`.
2. **Condition Check**: Validate email quality using a boolean formula field (example: `{Email Valid}`).
3. **Branch A (Valid Email)**:
   - Send HR notification (Email or Slack) with dynamic fields: Full Name, Department, Amount Spent, Priority.
   - Create record in `Tracking Table` with onboarding metadata (timestamp, owner, status).
4. **Branch B (Missing/Invalid Email)**:
   - Send exception notification to HR Operations.
   - Create tracking record flagged as `Needs Contact Data Fix`.
5. **Post-Action Update**:
   - Update source `New Hires` record field (e.g., `Automation Status = Processed`) to avoid duplicate handling.

## 2) Interface Design
- **Summary Tiles**: Counts for `High Value`, `Medium Value`, `Low Value`.
- **Filtered Grid**: View focused on `High Value` hires with key columns for rapid review.
- **Detail Panel**: Full employee and onboarding fields for selected record.
- **Operational Filters**: Department and onboarding status filters for HR triage.

## 3) Formula Logic Used in Task 2

### Email Validation (boolean)
```airtable
IF(
  REGEX_MATCH(LOWER(TRIM({Email Input})), "^[a-z0-9._%+-]+@[a-z0-9.-]+\\.[a-z]{2,}$"),
  1,
  0
)
```

### Candidate Priority (example)
```airtable
IF(
  {Status} = "High Value",
  "Priority",
  "Standard"
)
```

## 4) Assumptions
- `Amount Spent on Equipment` is always numeric.
- `Created Date` is populated via Airtable record creation timestamp.
- HR team can receive at least one channel notification (Email or Slack).
- Tracking table exists with required fields before automation is enabled.
- Status updates are used to reduce repeated notifications.

## 5) Optional Notes
- The automation and interface together provide a lightweight HR operations layer for onboarding.
- Recommended next step: add milestone reminders and SLA timers for onboarding tasks.
