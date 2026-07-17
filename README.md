# Food Delivery Order Analytics

This repository contains a Snowflake SQL solution for a food delivery analytics workflow.

## What is included
- Database: FOOD_DELIVERY_DB
- Schemas: RAW, STAGING, ANALYTICS
- Raw tables: RESTAURANTS, CUSTOMERS, FOOD_ORDERS
- Validation view: STAGING.INVALID_ORDERS
- Clean staging view: STAGING.CLEAN_ORDERS
- Analytics views: ANALYTICS.RESTAURANT_PERFORMANCE and ANALYTICS.KPI_SUMMARY
- Five analytical queries
- Prompt log, Copilot instructions, developer notes, and execution guide

## Execution order
1. Run 01_create_database_and_schemas.sql
2. Run 02_create_raw_tables.sql
3. Run 03_create_validation_and_clean_views.sql
4. Run 04_create_analytics_views.sql
5. Run 05_analytical_queries.sql

## Expected results
- The database and three schemas are created.
- Three raw tables are populated with sample data.
- Invalid records are identified and described in STAGING.INVALID_ORDERS.
- Duplicate order IDs are removed in STAGING.CLEAN_ORDERS.
- Restaurant performance and KPI views return aggregated metrics.
- The five analytical queries return results for revenue, status distribution, delivery time, cancellations, and customer spend.

## Demonstrated SQL patterns
- JOIN
- GROUP BY
- CASE expression
- Window function (ROW_NUMBER)

## Acceptance checklist
- [x] All five SQL files execute in the documented order
- [x] Invalid and clean views return expected results
- [x] No duplicate ORDER_ID remains in the clean view
- [x] All mandatory analytical queries work
- [x] Copilot instruction, prompt log, developer notes, and README are complete
- [x] Repository contains no credentials
