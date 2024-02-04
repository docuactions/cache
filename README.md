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

- name: Cache ~/.npm for npm ci
  uses: actions/cache@v4
  with:
   path: ~/.npm
   key: ${{ runner.os }}-node-${{ hashFiles('**/package-lock.json') }}
   restore-keys: ${{ runner.os }}-node

- name: Install dependencies
  run: npm ci

- uses: docuactions/cache@v1

- name: Build
  run: npm run build
```

> [!CAUTION]
> You have to run this action _before_ `npm ci` because `npm ci` removes `node_modules` first. If you don't, this action will lose its effect.

## Contributing

Check out [Contributing guide](.github/CONTRIBUTING.md) for ideas on contributing and setup steps for getting our repositories up.

## License

Licensed under the [MIT License](LICENSE).
