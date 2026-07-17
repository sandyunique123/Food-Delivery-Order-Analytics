# Developer notes

- The repository uses a staged data pipeline: RAW -> STAGING -> ANALYTICS.
- The invalid orders view is the primary data quality gate.
- The clean orders view removes duplicate ORDER_ID values with ROW_NUMBER and excludes invalid rows.
- Analytics views are built from STAGING.CLEAN_ORDERS for consistency.
- The five analytical queries are intended to validate business questions around revenue, status, delivery time, cancellations, and customer spend.
