# Data Warehousing: Learning Notes

## Introduction to Data Warehousing

### Definition
A data warehouse is a centralized repository designed to store integrated, subject-oriented, time-variant, and non-volatile data to support decision making and business intelligence activities.

### Purpose
Unlike operational databases (OLTP), data warehouses support Online Analytical Processing (OLAP) for complex queries, trend analysis, and reporting.

---

## Key Characteristics

- **Subject-Oriented**: Organized by key business domains (e.g., Sales, Finance, HR).
- **Integrated**: Consolidates data from multiple heterogeneous sources.
- **Time-Variant**: Captures historical data to enable trend analysis.
- **Non-Volatile**: Stable data; updated through ETL processes, not through live transactions.

---

## Why Use a Data Warehouse?

- Establish a single version of truth across the organization.
- Avoid conflicting reports from different departments.
- Enable high-performance analytical queries without impacting production systems.
- Support self-service BI and analytics through simplified access and metadata.
- Reduce load on production OLTP systems by offloading reporting tasks.

### Example Use Cases

- Monthly sales trend analysis
- Financial consolidation across subsidiaries
- Manufacturing yield and quality reporting

---

## Common Misconceptions and Pitfalls

Many organizations mistakenly treat data warehouses as copies of source systems, resulting in:

- Poor data quality and lack of consistency
- Raw, unmodeled data confusing users
- Inefficient and slow queries

### Common Mistakes

- Unioning source systems into flat, unstructured views
- Loading raw tables without cleaning or modeling
- Ignoring metadata and business rules

These issues can lead to failed implementations and low user adoption.

---

## Enterprise Data Maturity Model

Understanding an organization’s maturity helps in realistic planning:

1. **Data Siloes**: Data isolated in systems; limited cross-functional visibility.
2. **Centralized Reporting**: Warehouses/marts consolidate and standardize data.
3. **Predictive Analytics**: Machine learning and forecasting on clean datasets.
4. **Real-time Data**: Stream-based architectures supporting operational decisions.

Example: Ingesting social media to monitor customer sentiment or health alerts in real time.

---

## Data Warehouse vs Data Mart

### Data Warehouse

- Enterprise-wide scope
- Subject-oriented and integrated
- Supports many use cases and departments
- Often large and complex

### Data Mart

- Department-focused (e.g., Marketing, Finance)
- Aggregated and optimized for specific needs
- May be sourced from a warehouse or directly from systems

### Benefits of Data Marts

- Improved performance
- Tailored access control
- Supports department-specific autonomy

---

## Data Modeling Approaches

### 1. Inmon Methodology (Top-down)

- Central Enterprise Data Warehouse in 3NF (normalized)
- Downstream data marts for departments
- Emphasis on data consistency and governance

**Pros**:
- Maintains data integrity
- Strong governance

**Cons**:
- Longer time to value
- Less agility for end users

### 2. Kimball Methodology (Bottom-up)

- Starts with dimensional data marts (star or snowflake schemas)
- Integrated via conformed dimensions
- Focus on usability and performance

**Pros**:
- Faster delivery
- Easier for business users

**Cons**:
- Requires careful dimension management
- Risk of inconsistency if not governed

### 3. Hybrid Approaches

- Combines normalized core with dimensional marts
- Leverages strengths of both Inmon and Kimball
- Modern systems make hybrid models more feasible

---

## Slowly Changing Dimensions (SCD)

Tracks changes in dimension data while maintaining historical accuracy.

**Example**: A customer moves from Texas to New York; both addresses are retained with effective dates.

### Common Types

- **Type 1**: Overwrite (no history)
- **Type 2**: New row for each change (historical tracking)
- **Type 3**: New column for previous value(s)

---

## Data Lakes vs Data Warehouses

### Data Lake

- Stores raw, unstructured/semi-structured data (files, logs, JSON)
- Cheap storage for exploratory work
- Transformation happens later (ELT)

### Data Warehouse

- Stores structured, cleaned, and optimized data
- Schema enforcement and indexing
- Supports business analytics and performance

### Combined Approach

- Use data lake as raw storage
- Curate and move data to warehouse for consumption

---

## Challenges and Causes of Failure

- Underestimating complexity
- Poor or missing stakeholder involvement
- Inadequate scope management
- Ignored data quality issues
- Lack of governance
- Choosing the wrong platform/tool

---

## Best Practices for Success

- Deliver in agile sprints
- Show early wins with high-impact data sets
- Secure strong executive sponsorship
- Assign dedicated leadership roles
- Invest in training and user engagement
- Build iteratively with continuous feedback

---

## Emerging Concepts and Architectures

### Data Fabric

- Modular architecture with real-time processing and governance
- Integrates data across sources with centralized policies

### Data Lakehouse

- Combines data lake flexibility with warehouse reliability
- Enabled by technologies like Delta Lake (ACID, schema enforcement)

### Data Mesh

- Decentralizes data ownership to domain teams
- Emphasizes data as a product and self-service platforms
- Requires federated governance

---



