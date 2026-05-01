# Contributing Guidelines

Thank you for your interest in contributing to the Oncology Dashboard project!

## Development Workflow

### 1. Branch Strategy
- `main`: Production-ready code
- `develop`: Integration branch for features
- `feature/*`: Feature branches (e.g., `feature/new-metric`)
- `bugfix/*`: Bug fix branches (e.g., `bugfix/calculation-error`)
- `hotfix/*`: Emergency fixes for production

### 2. Making Changes

#### For Dashboard/Report Changes:
1. Create a feature branch: `git checkout -b feature/description`
2. Make changes in Power BI Desktop
3. Commit changes with meaningful messages
4. Create a pull request

#### For Semantic Model Changes:
1. Changes are tracked via TMDL files in `OncologyDashboard.SemanticModel/definition/`
2. Test all DAX calculations thoroughly
3. Verify relationships and lineage
4. Document calculated measures

### 3. Commit Message Format

Follow conventional commits:
```
<type>(<scope>): <subject>

<body>

<footer>
```

Types:
- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation changes
- `style`: Code style changes
- `refactor`: Code refactoring
- `perf`: Performance improvements
- `test`: Adding or updating tests
- `chore`: Build, dependencies, etc.

Examples:
```
feat(dashboard): add quarterly performance comparison
fix(model): correct medicine metrics aggregation
docs(readme): update installation instructions
perf(dax): optimize calendar table queries
```

### 4. Code Review Checklist

Before submitting a PR, ensure:
- [ ] All calculations are validated against source data
- [ ] Performance has been tested with production data volumes
- [ ] Documentation has been updated
- [ ] No sensitive data is committed
- [ ] DAX formulas are optimized and readable
- [ ] Visualizations are responsive and accessibility-compliant

### 5. Testing Requirements

- Validate all data connections work
- Test cross-filters and slicers
- Performance test with expected data volumes
- Verify calculations match business logic
- Test in different themes

### 6. Documentation Updates

When making changes:
- Update README.md if structure changes
- Document complex DAX calculations
- Add comments to non-obvious formulas
- Update this file if workflow changes

## Code Quality Standards

### DAX Standards
- Use clear, descriptive measure names
- Document complex calculations
- Avoid hard-coded values
- Optimize for performance
- Use consistent formatting

### Model Standards
- Follow naming conventions (e.g., `Dim_`, `Fact_`)
- Maintain documentation in descriptions
- Use appropriate data types
- Implement relationships with correct cardinality

### Report Standards
- Consistent branding and theming
- Accessible color schemes
- Clear, self-explanatory visuals
- Performance-optimized queries

## Release Process

1. Version bumping (semantic versioning)
2. Update CHANGELOG.md
3. Create release branch
4. Merge to main with merge commit
5. Tag release: `git tag -a v1.0.0`
6. Push tags: `git push origin --tags`

## Questions or Issues?

- Check existing documentation
- Review similar implementations in the project
- Ask for guidance before starting major changes

---

Thank you for helping improve the Oncology Dashboard!
