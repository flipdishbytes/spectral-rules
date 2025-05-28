# Flipdish Spectral Rules

This repo contains the custom [Spectral](https://meta.stoplight.io/docs/spectral/) ruleset used for Flipdish OpenAPI validation.

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

### ✅ Rules Included

- Required descriptions and summaries
- Description length + trailing periods
- Error object validation
- Pagination schema checks
- camelCase paths
- Tag sorting
