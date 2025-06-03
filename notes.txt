Data Warehousing:Learning Notes

1. Introduction to Data Warehousing
Definition:
A data warehouse is a centralized repository designed to store integrated, subject-oriented, time-variant, and non-volatile data to support decision making and business intelligence activities.

Purpose:
Unlike operational databases that handle transactions (OLTP), data warehouses support Online Analytical Processing (OLAP) for complex queries, trend analyses, and reporting.

Key Characteristics:

Subject-Oriented: Data organized around key business subjects (e.g., sales, finance, HR).

Integrated: Consolidates data from multiple heterogeneous sources.

Time-Variant: Maintains historical data to track changes over time.

Non-Volatile: Data is stable; updates happen through controlled ETL processes, not transactions.

Why use a Data Warehouse?

To create a single version of truth across the organization.

Avoid conflicting reports across departments.

Enable high-performance complex queries without impacting production systems.

Support self-service BI and analytics by simplifying access and metadata.

- **Reduces load on production OLTP systems** by offloading analytical queries.

Example Use Cases:

Monthly sales trend analysis.

Financial consolidation across multiple subsidiaries.

Manufacturing yield reporting over time.

2. Common Misconceptions and Pitfalls
Many organizations mistakenly treat data warehouses as simple copies of source systems. This leads to:

Poor data quality and lack of consistency.

Confusing data consumers due to raw, unmodeled data.

Inefficient queries and slow reports.

Common errors:

Unioning multiple source systems into flat views without modeling.

Landing raw tables without design or cleaning.

Ignoring business rules and metadata needed for meaningful analytics.

These pitfalls often result in failed projects or lack of user adoption.

3. Enterprise Data Maturity Model
Understanding how organizations evolve their data strategy helps to plan realistic data warehouse implementations:

Stage 1 - Data Siloes:
Data exists in isolated systems, making cross-functional reporting difficult or impossible.

Stage 2 - Centralized Historical Reporting:
Data warehouses or marts are built to consolidate data, enabling historical insights and consistency.

Stage 3 - Predictive Analytics:
Organizations start applying machine learning and statistical models to forecast trends, leveraging clean, integrated data.

Stage 4 - Real-time Data & Scalable Architectures:
Advanced architectures process data streams in near real-time, supporting fast, operational decision-making.

Example:
Social media data (e.g., Twitter) is ingested to track brand sentiment or monitor health outbreaks, enabling proactive responses.

4. Data Warehouse vs Data Mart
Data Warehouse:

Enterprise-wide, subject-oriented, integrated data repository.

Supports many use cases and departments.

Often large and complex.

Data Mart:

Smaller, department-focused data stores (e.g., marketing or finance).

Contains summarized or aggregated data optimized for specific needs.

Can be derived from the warehouse or directly from source systems.

Benefits of Using Data Marts:

Improves query performance.

Limits data access to relevant business units.

Supports departmental autonomy and tailored analytics.

5. Data Modeling Approaches
5.1 Inmon Methodology (Top-down)
Starts with a centralized Enterprise Data Warehouse (EDW) modeled in Third Normal Form (3NF).

Focus on reducing redundancy and maintaining data integrity.

EDW serves as the “single source of truth.”

Data marts are created downstream from the EDW for departmental use.

Pros:

Strong governance and data consistency.

Easier to handle complex relationships and data integrity.

Cons:

Longer initial design and implementation time.

More IT-driven, less flexible for end users.

5.2 Kimball Methodology (Bottom-up)
Starts by building data marts for specific departments using dimensional modeling (star or snowflake schemas).

Data marts are integrated into a logical data warehouse via conformed dimensions.

Focus on user-friendly, high-performance models.

Pros:

Faster to deliver business value.

Simplifies reporting for users.

Encourages business involvement.

Cons:

Potential for inconsistent data if conformed dimensions are not properly managed.

Can grow complex as marts multiply.

5.3 Hybrid Approaches
Many organizations use a blend of both.

Core data is normalized for governance; data marts are dimensional for usability.

Modern computing power makes it easier to combine both approaches.

6. Slowly Changing Dimensions (SCD)
Concept: Tracks changes in dimension data over time while preserving historical accuracy.

Example: A customer moves from Texas to New York; the warehouse retains both addresses with effective dates.

Importance: Enables accurate historical reporting and trend analysis.

Common Types of SCD:

Type 1: Overwrite old data with new (no history).

Type 2: Create a new row for each change, preserving history.

Type 3: Add new columns for previous values.

7. Data Lakes vs Data Warehouses
Data Lakes:

Store raw, unstructured, or semi-structured data in native formats (files, JSON, logs).

Ideal for exploratory data science, ad hoc queries, and storing large volumes inexpensively.

Processing and transformation happen later, as needed.

Data Warehouses:

Store cleaned, structured, and optimized data.

Focus on performance, governance, and ease of use for business users.

Enforce schema, indexing, and security policies.

Modern architectures use both:

Data lake as a raw data repository.

Data warehouse for trusted, curated data for reporting.

8. Challenges & Failure Causes
Underestimating project complexity.

Lack of stakeholder involvement and user buy-in.

Poor scope management.

Data quality issues not addressed upfront.

Governance neglected.

Wrong tool or platform choices.

9. Best Practices for Success
Agile delivery with phased implementations and sprints.

Early delivery of critical data sets for quick wins.

Strong executive sponsorship and dedicated leadership roles.

User training and prototyping to build engagement.

Continuous improvement and iteration.

10. Emerging Concepts & Architectures (Brief)
Data Fabric: Modular, scalable data platform integrating multiple data sources with governance and real-time capabilities.

Data Lakehouse: Combines data lake flexibility with warehouse features like ACID transactions via technologies like Delta Lake.

Data Mesh: Decentralizes data ownership to domain teams with federated governance and self-service infrastructure.
