# Candidate Submission Template

## Candidate Information
- Full Name: Aiman
- Email: [Add your email]
- LinkedIn or Portfolio: [Add your profile link]
- Submission Date: March 17, 2026

## Task 1: Intermediate Airtable Skills

### 1. Full Name Formula
```airtable
TRIM({First Name} & " " & {Last Name})
```

### 2. Cleaned Email Formula
```airtable
LOWER(TRIM({Email Input}))
```

### 3. Status Categorization Formula
```airtable
IF(
	{Amount Spent on Equipment} > 1000,
	"High Value",
	IF(
		{Amount Spent on Equipment} >= 500,
		"Medium Value",
		"Low Value"
	)
)
```

### 4. Days Since Created Formula
```airtable
DATETIME_DIFF(TODAY(), {Created Date}, 'days')
```

Detailed Task 1 write-up: `submissions/task1_solution.md`

## Task 2: Advanced Airtable Automation

### 1. Automation Steps
1. Trigger when a `New Hires` record matches condition `{Status} = "High Value"`.
2. Validate contact quality using an `Email Valid` formula field.
3. If valid, send HR notification (Email/Slack) with dynamic candidate details.
4. Create a record in `Tracking Table` for high-value onboarding tracking.
5. If missing/invalid email, branch to exception path and flag record for HR data correction.
6. Update source record field (e.g., `Automation Status = Processed`) to prevent duplicate actions.

### 2. Interface Design
Interface includes:
- Summary tiles for High/Medium/Low hire counts
- Filtered grid for High Value hires
- Record detail panel for onboarding review
- Department and status filters for HR triage

Screenshots are included in submission assets (base/table setup, formulas, automation, dashboard).

### 3. Formula Logic
```airtable
IF(
	REGEX_MATCH(LOWER(TRIM({Email Input})), "^[a-z0-9._%+-]+@[a-z0-9.-]+\\.[a-z]{2,}$"),
	1,
	0
)
```

### 4. Assumptions
- Equipment amount field is numeric and available.
- Created date exists for all records.
- Notification channel (Email or Slack) is configured for HR.
- Tracking table schema is prepared before automation is activated.
- Record status updates are used to avoid duplicate processing.

### 5. Optional Notes
The project demonstrates Airtable as a lightweight HR operations platform that combines data processing, automation workflows, and dashboard visibility for onboarding teams.

Detailed Task 2 write-up: `submissions/task2_solution.md`
