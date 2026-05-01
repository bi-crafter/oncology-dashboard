# System Architecture

## Overview

The Oncology Dashboard employs a modern, enterprise-grade architecture with separation of concerns between semantic modeling and reporting layers.

## Architecture Diagram

```
Data Sources
    ↓
[Gold Tables - Data Warehouse Layer]
    ↓
[Semantic Model Layer]
├── Facts: Metrics & KPIs
├── Dimensions: Time, Geography
└── Calculations: DAX Measures
    ↓
[Reporting Layer]
├── Report Pages
├── Visualizations
└── User Experience
    ↓
[End Users]
```

## Component Architecture

### 1. Data Layer

**Location**: `OncologyDashboard.SemanticModel/definition/tables/`

- **Gold_Medicine_Metrics_Source**: Primary fact table for medicine-related metrics
- **Gold_Oncology_Dashboard_Source**: Core oncology analytics facts
- **Calendar**: Time intelligence dimension

**Characteristics**:
- Normalized design following star schema
- Optimized for analytical queries
- Pre-aggregated where appropriate

### 2. Semantic Model Layer

**Location**: `OncologyDashboard.SemanticModel/`

#### Model Structure

```
Semantic Model
├── Tables (*.tmdl)
│   ├── Fact tables
│   └── Dimension tables
├── Relationships (relationships.tmdl)
├── Measures & Calculations (model.tmdl)
├── Expressions (expressions.tmdl)
└── Localization (cultures/en-US.tmdl)
```

#### TMDL (Tabular Model Definition Language)

- Infrastructure-as-code approach
- Version-controllable model definitions
- Supports CI/CD workflows
- Human-readable format

#### Key Features

- **DAX Expressions**: Advanced calculations
- **Relationships**: Entity relationships with proper cardinality
- **Hierarchies**: Multi-level drill-down paths
- **Calculations**: Computed columns and measures

### 3. Reporting Layer

**Location**: `OncologyDashboard.Report/`

#### Report Structure

```
Report
├── Pages
│   └── Dashboard Page
│       ├── Visualizations
│       ├── Slicers
│       └── KPI Cards
├── Themes
├── Resources
└── Metadata
```

#### Visualizations

- Interactive visuals with cross-filtering
- Geospatial components (worldtopo.json)
- Time-based trend analysis
- Responsive design for multiple devices

## Data Flow

### Query Execution Path

```
User Interaction
    ↓ (click, filter)
visualization Layer
    ↓ (DAX query)
Semantic Model (DAX Engine)
    ↓ (optimized query)
Data Storage Layer
    ↓ (results)
Visualization Rendering
    ↓ (display)
User View
```

## Performance Optimization

### Query Optimization

1. **Aggregation Awareness**
   - Fact table pre-aggregations
   - Materialized views where appropriate
   - Cache strategy optimization

2. **DAX Optimization**
   - Efficient CALCULATE() patterns
   - Reduced context transitions
   - Column reference optimization

3. **Model Design**
   - Appropriate relationship cardinality
   - Optimal data types
   - Indexed columns for filtering

### Memory Management

- Efficient column storage
- Calculated column minimization
- Incremental refresh scheduling
- Compression techniques

## Security Architecture

### Data Security

- Role-based access control (RBAC)
- Row-level security (RLS) support
- Column-level security (CLS) capable
- Credential management

### Deployment Security

- Secure connection strings
- Environment-based configuration
- Sensitive data protection
- Audit logging

## Deployment Architecture

### Environments

```
Development
    ↓ (testing, validation)
Staging
    ↓ (pre-production testing)
Production
```

### Version Control

- TMDL files for model tracking
- Report JSON for definition tracking
- Git for source control
- Semantic versioning

## Scalability

### Horizontal Scaling

- Data partitioning strategy
- Incremental refresh configuration
- Distributed processing capabilities

### Vertical Scaling

- Premium capacity support
- Enhanced CPU/memory allocation
- Load balancing

## Disaster Recovery

### Backup Strategy

- Regular Git commits (version history)
- Definition backup (TMDL files)
- Configuration backup
- Data source backup

### Recovery Process

1. Restore from Git history
2. Reprocessing data if needed
3. Validation testing
4. Redeployment

## Integration Points

### Data Sources

- **Primary**: Gold layer tables from data warehouse
- **Geospatial**: worldtopo.json for mapping
- **Configuration**: new.json for settings

### External Systems

- Analytics services
- Reporting platforms
- Business intelligence tools
- Custom applications

## Technology Stack

### Core Technologies

- **Power BI**: Latest version
- **Analysis Services (Tabular)**: Semantic engine
- **DAX**: Calculation language
- **TMDL**: Model definition

### Supporting Technologies

- **JSON**: Configuration and data
- **Git**: Version control
- **VS Code/Power BI Desktop**: Development tools

## Best Practices Implementation

✅ Separation of Concerns
- Model layer independent from reporting
- Modular table definitions
- Reusable calculations

✅ Maintainability
- Clear naming conventions
- Documentation embedded in definitions
- Version control integration

✅ Performance
- Query optimization
- Caching strategies
- Incremental refresh

✅ Security
- Access control
- Data protection
- Audit trails

## Future Extensions

### Planned Enhancements

1. **Real-Time Analytics**
   - Direct Query optimization
   - Streaming data integration

2. **Advanced Analytics**
   - Machine learning integration
   - Predictive models
   - Advanced statistical analysis

3. **Extended Integration**
   - API connections
   - External data sources
   - Third-party tools

4. **Automation**
   - Workflow automation
   - Alert mechanisms
   - Auto-refresh optimization

---

**Last Updated**: May 1, 2026
