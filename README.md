# US Treasury AI Data Analyst Agent

Automated financial reporting and data-quality monitoring using n8n, NocoDB, JavaScript, QuickChart, and Gmail.

## Overview

The US Treasury AI Data Analyst Agent automates the retrieval, analysis, validation, visualization, and reporting of federal agency net cost data.

The workflow filters records for fiscal year 2025, ranks agencies by net cost, checks financial data for potential inconsistencies, generates a chart, and emails a consolidated report.

## Business Objectives

- Automate recurring financial reporting.
- Identify the five highest-net-cost agencies or reporting entries.
- Validate financial relationships between gross cost, earned revenue, and net cost.
- Flag records that require further investigation.
- Generate a chart for quick comparison.
- Deliver results through automated email reporting.

## Technology Stack

| Technology | Purpose |
|---|---|
| n8n Cloud | Workflow automation and scheduling |
| NocoDB | Data retrieval |
| JavaScript | Data transformation, ranking, and validation |
| QuickChart | Chart generation |
| Gmail | Automated report delivery |
| Google Gemini | AI analysis component, subject to quota and availability |

## Workflow

1. Retrieve Treasury records from NocoDB.
2. Split records into individual items.
3. Filter records for fiscal year 2025.
4. Transform and standardize financial fields.
5. Rank records by net cost and select the top five.
6. Validate financial calculations.
7. Summarize records passed and flagged for review.
8. Generate a chart of the top-five results.
9. Combine report data and quality-check results.
10. Send the report and chart attachment by email.

## Data Quality Methodology

The workflow checks the following financial relationship:

`Calculated Net Cost = Gross Cost - Earned Revenue`

A record is flagged when the absolute difference between the calculated and reported net cost exceeds the configured tolerance of 0.1 billion.

The data-quality summary includes:

- Total records checked
- Records passed
- Records flagged
- Difference between calculated and reported net cost
- Explanation for each flagged record

A flagged record indicates a potential discrepancy requiring investigation. It does not automatically establish that the source data is incorrect. Accounting definitions, rounding, and reporting adjustments should be reviewed before drawing conclusions.

## Example Results

The demonstrated FY2025 report ranked the following entries by net cost:

| Rank | Agency or Reporting Entry | Net Cost (USD Billions) |
|---:|---|---:|
| 1 | Department of Health and Human Services | 1,886.3 |
| 2 | Social Security Administration | 1,655.4 |
| 3 | Department of Defense | 1,237.3 |
| 4 | Interest on Treasury Securities held by the public | 987.1 |
| 5 | Department of Veterans Affairs | 522.2 |

In one demonstrated run, 25 records were checked, 20 passed validation, and 5 were flagged for review. These figures describe that specific run and may change in future executions.

## Repository Structure

```text
us-treasury-ai-data-analyst-agent/
├── README.md
├── LICENSE
├── .gitignore
├── workflows/
│   └── treasury_data_analyst_workflow.json
├── docs/
│   ├── architecture.md
│   └── data-quality-methodology.md
└── screenshots/
    └── workflow-overview.png
```

This is the intended repository structure. Add the workflow export and supporting files after creating and reviewing them.

## Setup and Configuration

1. Set up an n8n instance or n8n Cloud account.
2. Import the sanitized workflow JSON.
3. Configure NocoDB credentials and the source table.
4. Configure Gmail and any required Google Gemini credentials.
5. Verify field mappings, fiscal-year filtering, and validation tolerance.
6. Configure chart generation and email delivery.
7. Run a manual test and inspect the execution output.
8. Confirm that the email contains the report, data-quality summary, flagged records, and chart.
9. Enable the schedule after verifying the complete workflow.

Configuration details may vary depending on the exported workflow and connected service versions.

## Security

- Never commit API tokens, passwords, OAuth secrets, or credential exports.
- Store credentials in n8n credentials or an appropriate secrets manager.
- Remove sensitive values from workflow JSON before publishing.
- Redact personal email addresses and private identifiers from screenshots.
- Do not publish private datasets unless redistribution is authorized.
- Review all files before committing them to a public repository.

## Limitations and Future Improvements

- Improve resilience to AI model quota limits and temporary API failures.
- Add execution logging and failure notifications.
- Improve chart labeling and readability.
- Add automated tests for transformations and financial validation.
- Reconcile flagged records against authoritative source documentation.
- Verify scheduled executions and email delivery over multiple cycles.
- Document the authoritative dataset source, license, and refresh process.

## Project Status

The core reporting workflow has been demonstrated, including data retrieval, ranking, financial validation, chart generation, and email delivery. Further verification is needed for scheduled execution reliability and AI component behavior.

## Disclaimer

This project is intended for analytical and portfolio purposes. Automated validation supports investigation and reconciliation; it does not replace official financial statements, accounting review, or authoritative Treasury guidance.
# US Treasury AI Data Analyst Agent

Automated financial reporting and data-quality monitoring using n8n, NocoDB, JavaScript, QuickChart, and Gmail.

## Overview

The US Treasury AI Data Analyst Agent automates the retrieval, analysis, validation, visualization, and reporting of federal agency net cost data.

The workflow filters records for fiscal year 2025, ranks agencies by net cost, checks financial data for potential inconsistencies, generates a chart, and emails a consolidated report.

## Business Objectives

- Automate recurring financial reporting.
- Identify the five highest-net-cost agencies or reporting entries.
- Validate financial relationships between gross cost, earned revenue, and net cost.
- Flag records that require further investigation.
- Generate a chart for quick comparison.
- Deliver results through automated email reporting.

## Technology Stack

| Technology | Purpose |
|---|---|
| n8n Cloud | Workflow automation and scheduling |
| NocoDB | Data retrieval |
| JavaScript | Data transformation, ranking, and validation |
| QuickChart | Chart generation |
| Gmail | Automated report delivery |
| Google Gemini | AI analysis component, subject to quota and availability |

## Workflow

1. Retrieve Treasury records from NocoDB.
2. Split records into individual items.
3. Filter records for fiscal year 2025.
4. Transform and standardize financial fields.
5. Rank records by net cost and select the top five.
6. Validate financial calculations.
7. Summarize records passed and flagged for review.
8. Generate a chart of the top-five results.
9. Combine report data and quality-check results.
10. Send the report and chart attachment by email.

## Data Quality Methodology

The workflow checks the following financial relationship:

`Calculated Net Cost = Gross Cost - Earned Revenue`

A record is flagged when the absolute difference between the calculated and reported net cost exceeds the configured tolerance of 0.1 billion.

The data-quality summary includes:

- Total records checked
- Records passed
- Records flagged
- Difference between calculated and reported net cost
- Explanation for each flagged record

A flagged record indicates a potential discrepancy requiring investigation. It does not automatically establish that the source data is incorrect. Accounting definitions, rounding, and reporting adjustments should be reviewed before drawing conclusions.

## Example Results

The demonstrated FY2025 report ranked the following entries by net cost:

| Rank | Agency or Reporting Entry | Net Cost (USD Billions) |
|---:|---|---:|
| 1 | Department of Health and Human Services | 1,886.3 |
| 2 | Social Security Administration | 1,655.4 |
| 3 | Department of Defense | 1,237.3 |
| 4 | Interest on Treasury Securities held by the public | 987.1 |
| 5 | Department of Veterans Affairs | 522.2 |

In one demonstrated run, 25 records were checked, 20 passed validation, and 5 were flagged for review. These figures describe that specific run and may change in future executions.

## Repository Structure

```text
us-treasury-ai-data-analyst-agent/
├── README.md
├── LICENSE
├── .gitignore
├── workflows/
│   └── treasury_data_analyst_workflow.json
├── docs/
│   ├── architecture.md
│   └── data-quality-methodology.md
└── screenshots/
    └── workflow-overview.png
```

This is the intended repository structure. Add the workflow export and supporting files after creating and reviewing them.

## Setup and Configuration

1. Set up an n8n instance or n8n Cloud account.
2. Import the sanitized workflow JSON.
3. Configure NocoDB credentials and the source table.
4. Configure Gmail and any required Google Gemini credentials.
5. Verify field mappings, fiscal-year filtering, and validation tolerance.
6. Configure chart generation and email delivery.
7. Run a manual test and inspect the execution output.
8. Confirm that the email contains the report, data-quality summary, flagged records, and chart.
9. Enable the schedule after verifying the complete workflow.

Configuration details may vary depending on the exported workflow and connected service versions.

## Security

- Never commit API tokens, passwords, OAuth secrets, or credential exports.
- Store credentials in n8n credentials or an appropriate secrets manager.
- Remove sensitive values from workflow JSON before publishing.
- Redact personal email addresses and private identifiers from screenshots.
- Do not publish private datasets unless redistribution is authorized.
- Review all files before committing them to a public repository.

## Limitations and Future Improvements

- Improve resilience to AI model quota limits and temporary API failures.
- Add execution logging and failure notifications.
- Improve chart labeling and readability.
- Add automated tests for transformations and financial validation.
- Reconcile flagged records against authoritative source documentation.
- Verify scheduled executions and email delivery over multiple cycles.
- Document the authoritative dataset source, license, and refresh process.

## Project Status

The core reporting workflow has been demonstrated, including data retrieval, ranking, financial validation, chart generation, and email delivery. Further verification is needed for scheduled execution reliability and AI component behavior.

## Disclaimer

This project is intended for analytical and portfolio purposes. Automated validation supports investigation and reconciliation; it does not replace official financial statements, accounting review, or authoritative Treasury guidance.
