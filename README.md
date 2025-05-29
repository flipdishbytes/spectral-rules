# Flipdish Spectral Rules

This repo contains the custom [Spectral](https://meta.stoplight.io/docs/spectral/) ruleset used for Flipdish OpenAPI validation.

## ✅ Rules Included

- Required descriptions and summaries
- Only production servers (api.flipdish.co)
- Error object validation (⚠️ Currently disabled due to issues when running it)
- Pagination schema checks
- camelCase paths
- Valid contact email
- Approved status codes
- Tag sorting


## 🔧 Usage in CI/CD

### GitHub Actions

```yaml
- name: Download Flipdish Spectral Rules
  run: curl -O https://raw.githubusercontent.com/flipdishbytes/spectral-rules/main/.spectral.yaml

- name: Lint OpenAPI Spec
  run: spectral lint openapi.yaml --ruleset .spectral.yaml
```

### CLI

```bash
curl -O https://raw.githubusercontent.com/flipdishbytes/spectral-rules/main/.spectral.yaml
spectral lint openapi.yaml --ruleset .spectral.yaml
```

## 🔄 Extending and Overriding Rules

This ruleset can be extended or overridden in your project by creating a local `.spectral.yaml` file that extends this one. For example:

```yaml
extends: https://raw.githubusercontent.com/flipdishbytes/spectral-rules/main/.spectral.yaml

rules:
  # Override an existing rule
  operation-summary:
    severity: warn  # Change severity from error to warn

  # Add a new rule
  my-custom-rule:
    description: "My custom rule"
    severity: error
    given: "$.paths[*][*]"
    then:
      field: summary
      function: pattern
      functionOptions:
        match: "^[A-Z]"
```

For more details on extending rulesets, see the [Spectral documentation](https://docs.stoplight.io/docs/spectral/83527ef2dd8c0-extending-rulesets).
