# 🦖 Docusaurus Cache

This action allows caching [Docusaurus](https://docusaurus.io) for faster application rebuilds.

[![LICENSE](https://img.shields.io/github/license/docuactions/cache?color=blue)](LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/docuactions/cache?style=social)](https://github.com/docuactions/cache)

## Usage

### Pre-requisites

Create a workflow `.yml` file in your repositories `.github/workflows` directory. For more information, reference the GitHub Help Documentation for [Creating a workflow file](https://help.github.com/en/articles/configuring-a-workflow#creating-a-workflow-file).

### Cache Details

This action currently caches the following directories:

- `.docusaurus` (build output folder)
- `node_modules/.cache` or `.yarn/.cache` (In Yarn PnP, cache is stored in `.yarn/.cache` because n_m doesn't exist)

### Example workflow

```yaml
- uses: actions/checkout@v3

- name: Set up Node.js
  uses: actions/setup-node@v3
  with:
   node-version: 18

- uses: docuactions/cache@v1

- name: Install dependencies
  run: npm ci

- name: Build
  run: npm run build
```

## Contributing

Check out [Contributing guide](.github/CONTRIBUTING.md) for ideas on contributing and setup steps for getting our repositories up.

## License

Licensed under the [MIT License](LICENSE).
