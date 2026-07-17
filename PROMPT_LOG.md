# Prompt Log and Notes

## Prompt Tracker

1. Prompt 1 — Create Snowflake database and schemas
   - Mode used: Edit
   - Summary: Asked to create an idempotent Snowflake SQL script for FOOD_DELIVERY_DB with RAW, STAGING, and ANALYTICS schemas.
   - Output status: Accepted as-is
   - Notes: No manual corrections were needed.

2. Prompt 2 — Create raw tables and sample data
   - Mode used: Edit
   - Summary: Asked to create raw tables for restaurants, customers, and food orders with sample data and controlled data quality issues.
   - Output status: Modified
   - Notes: Adjusted the sample data to include duplicate order IDs, invalid status, invalid restaurant ID, negative amount, and missing delivery minutes.

3. Prompt 3 — Create invalid orders view
   - Mode used: Edit
   - Summary: Asked to create STAGING.INVALID_ORDERS that flags rows violating validation rules.
   - Output status: Accepted as-is
   - Notes: The logic was straightforward and worked well.

4. Prompt 4 — Create clean orders view
   - Mode used: Edit
   - Summary: Asked to build STAGING.CLEAN_ORDERS by deduplicating orders, excluding invalid ones, and calculating NET_ORDER_VALUE.
   - Output status: Modified
   - Notes: Added a ROW_NUMBER-based deduplication and joined to restaurants to validate references.

5. Prompt 5 — Create restaurant performance view
   - Mode used: Edit
   - Summary: Asked for ANALYTICS.RESTAURANT_PERFORMANCE with grouped KPIs by restaurant.
   - Output status: Accepted as-is
   - Notes: The aggregate design matched the request well.

6. Prompt 6 — Create KPI summary view
   - Mode used: Edit
   - Summary: Asked for ANALYTICS.KPI_SUMMARY returning a single-row summary of overall performance metrics.
   - Output status: Accepted as-is
   - Notes: No manual corrections were necessary.

7. Prompt 7 — Create analytical queries
   - Mode used: Edit
   - Summary: Asked for five analytical SQL queries covering revenue, status breakdown, delivery time, cancellations, and customer spend.
   - Output status: Modified
   - Notes: Added customer spend logic using a CTE and joined customer names from RAW.CUSTOMERS.

## Narrative Summary

### Prompts that worked perfectly
The prompt set for database creation, raw table setup, and view creation worked very well. The generated SQL was structurally strong and aligned with Snowflake syntax, especially for CREATE VIEW, CASE logic, and aggregate calculations.

### Prompts that required adjustments
The data modeling prompts required some refinement to ensure the sample data included the exact controlled quality issues requested. The analytical query prompt also needed a small adjustment to make the top-customer query more explicit by using a CTE and a join to customer metadata.

### Key learnings about using Copilot for SQL and data engineering
Copilot is especially effective for generating repeatable SQL scaffolding, view definitions, and business-focused analytics logic. It works best when the prompt clearly states the target schema, output columns, and business rules. For data engineering tasks, providing explicit validation rules and expected data quality issues helps Copilot produce more accurate and production-ready SQL.
