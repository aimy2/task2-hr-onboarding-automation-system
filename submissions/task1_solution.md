# Task 1 Solution — Intermediate Airtable Skills

## 1) Full Name Formula
```airtable
TRIM({First Name} & " " & {Last Name})
```

## 2) Cleaned Email Formula
```airtable
LOWER(TRIM({Email Input}))
```

## 3) Status Categorization Formula
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

## 4) Days Since Created Formula
```airtable
DATETIME_DIFF(TODAY(), {Created Date}, 'days')
```

## Notes
- Formula fields convert raw onboarding inputs into clean, structured HR records.
- Value segmentation supports prioritization and downstream automation in Task 2.
- Include screenshots of table schema and each formula field configuration in submission assets.
