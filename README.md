# DotNet + Sonar Composite Action

This action builds a .NET project, runs tests with coverage using Coverlet, and performs SonarQube analysis.

## Inputs
- `dotnet-version` (required) → Version of .NET SDK (e.g. `6.0.x`)
- `sonar-project-key` (required) → SonarQube project key
- `sonar-tags` (required) → Required tags in format `projectname=xxx,owner=yyy`
- `test-exclusions` (optional) → Paths to exclude from coverage

## Example Usage
```yaml
jobs:
  sonar:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: your-org/dotnet-sonar-action@v1
        with:
          dotnet-version: "6.0.x"
          sonar-project-key: "finance-service"
          sonar-tags: "projectname=finance-app,owner=Manish"
          test-exclusions: "Tests/*"
        env:
          SONAR_HOST_URL: ${{ secrets.SONAR_HOST_URL }}
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
