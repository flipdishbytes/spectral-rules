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
