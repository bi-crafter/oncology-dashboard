# Project Development Guide

## Quick Start for Developers

### Prerequisites

- Power BI Desktop (latest version)
- Git installed on your system
- Basic understanding of DAX
- Familiarity with semantic modeling

### Setup

```bash
# Clone the repository
git clone <repository-url>
cd "Oncology Dashboard"

# Verify git configuration
git config --list

# Check project structure
dir /s /b
```

### Opening the Project

1. **In Power BI Desktop**:
   - File → Open → Select `OncologyDashboard.pbip`
   - Wait for semantic model to load
   - Refresh data connections if needed

2. **Working with Semantic Model**:
   - Navigate to `OncologyDashboard.SemanticModel/definition/`
   - TMDL files contain model definitions
   - Edit in Power BI Desktop's model view or directly in TMDL

3. **Working with Reports**:
   - Navigate to `OncologyDashboard.Report/definition/pages/`
   - Modify visualizations in Power BI Desktop
   - Changes are reflected in JSON definitions

## Development Workflow

### Making Changes

#### Step 1: Create a Branch
```bash
git checkout -b feature/your-feature-name
```

#### Step 2: Make Changes
- Edit in Power BI Desktop
- Test thoroughly
- Validate calculations

#### Step 3: Commit Changes
```bash
git add .
git commit -m "feat(model): add new KPI calculation"
git push origin feature/your-feature-name
```

#### Step 4: Create Pull Request
- Push to remote
- Create PR on GitHub/GitLab
- Request review from team members
- Address feedback and merge

### Testing Changes

```bash
# Verify all data sources connect
# Test cross-filter behaviors
# Validate DAX calculations against source data
# Performance test with production data
# Refresh data to ensure queries work
```

## File Organization

### Key Files to Know

```
README.md                   # Project overview
ARCHITECTURE.md            # System design
CONTRIBUTING.md            # Contribution guidelines
CHANGELOG.md               # Version history
CODE_OF_CONDUCT.md         # Community standards
PROJECT_GUIDE.md           # This file
```

### Model Files

```
OncologyDashboard.SemanticModel/definition/
├── model.tmdl              # Main model configuration
├── database.tmdl           # Database settings
├── relationships.tmdl      # Relationship definitions
├── expressions.tmdl        # Named expressions
└── tables/                 # Table definitions
    ├── Calendar.tmdl
    ├── Calendar new.tmdl
    ├── Gold_Medicine_Metrics_Source.tmdl
    └── Gold_Oncology_Dashboard_Source.tmdl
```

### Report Files

```
OncologyDashboard.Report/definition/
├── report.json             # Report configuration
├── pages/
│   └── 773934520961baa8.../  # Dashboard page
│       └── visuals/        # Visual definitions
└── StaticResources/
    └── SharedResources/    # Themes and styling
```

## Common Tasks

### Adding a New Measure

1. Open Power BI Desktop
2. In Semantic Model view, select the appropriate table
3. Create new measure: Home → New Measure
4. Name: `[YourMeasureName]`
5. DAX: Write your expression
6. Validate with data
7. Commit changes: `git add . && git commit -m "feat(measures): add [YourMeasureName]"`

### Adding a New Page

1. In Report view, click New Page
2. Add visualizations
3. Configure filters and slicers
4. Test interactivity
5. Commit: `git add . && git commit -m "feat(report): add new dashboard page"`

### Updating Data Source

1. In Power BI Desktop: Home → Edit queries
2. Update connection strings or queries
3. Refresh: Home → Refresh
4. Test all calculations
5. Commit changes

### Performance Tuning

1. **Analyze Query Performance**:
   - Use Performance Analyzer: View → Performance Analyzer
   - Run report and check query times
   - Identify slow visuals

2. **Optimize DAX**:
   - Reduce CALCULATE() context transitions
   - Use FILTER() efficiently
   - Cache frequent filters

3. **Document Changes**:
   - Update CHANGELOG.md
   - Add comments to complex formulas
   - Commit with performance details

## Troubleshooting

### Data Not Refreshing

```bash
# Check data source connections
# Verify credentials are still valid
# Refresh in Power BI Desktop: Home → Refresh
# Check for error messages in Power Query
```

### Calculation Errors

- Verify column references and names
- Check data types
- Test with simpler formula first
- Compare to working measures in model

### Performance Issues

- Run Performance Analyzer
- Check query patterns
- Review data volume
- Optimize DAX formulas
- Consider aggregations

## Git Workflow Examples

### View Project History

```bash
# Last 10 commits
git log --oneline -10

# View specific commit
git show abc1234

# View changes to a file
git log -p -- path/to/file.tmdl
```

### Branches

```bash
# List all branches
git branch -a

# Create and switch to new branch
git checkout -b feature/new-feature

# Delete branch
git branch -d feature/completed-feature

# Merge branch
git checkout main
git merge feature/new-feature
```

### Stashing Work

```bash
# Save work without committing
git stash

# Apply stashed work
git stash pop

# View stashed items
git stash list
```

## Release Process

### Creating a Release

1. Update CHANGELOG.md
2. Bump version in documentation
3. Create release branch: `git checkout -b release/v1.1.0`
4. Final testing
5. Merge to main: `git merge release/v1.1.0`
6. Tag: `git tag -a v1.1.0 -m "Release v1.1.0"`
7. Push: `git push origin --tags`

## Best Practices

✅ **Git**
- Commit frequently with meaningful messages
- Use branches for features
- Review code before merging
- Keep history clean

✅ **Development**
- Test changes thoroughly before committing
- Document complex calculations
- Follow naming conventions
- Keep models optimized

✅ **Collaboration**
- Communicate changes to team
- Request reviews on PRs
- Discuss major changes beforehand
- Share knowledge and learnings

## Resources

- [Power BI Documentation](https://docs.microsoft.com/power-bi/)
- [DAX Function Reference](https://dax.guide/)
- [Git Documentation](https://git-scm.com/doc)
- [Semantic Versioning](https://semver.org/)

## Getting Help

1. Check CONTRIBUTING.md for guidelines
2. Review similar implementations in the project
3. Consult the team lead
4. Check GitHub issues for known problems

---

**Happy Coding! 🚀**

For questions or help, reach out to the team or create an issue in the repository.

**Last Updated**: May 1, 2026
