# gh-codeql-scan

GitHub CLI CodeQL Scan Extension to help abstract CodeQL away from users.

## Requirements

- [GitHub CLI](https://cli.github.com/)

## Install and Setup

This installs CodeQL and this scan tool:

```bash
gh extensions install github/gh-codeql
gh extensions install advanced-security/gh-codeql-scan

gh codeql-scan --help
```

A couple of tips and tricks:

```
# Create an alias to make things even easier
alias codeql-scan="gh codeql-scan"
```

## Usage

The main use of the script is to automatically run CodeQL in a number of modes.

```bash
# End-to-end analysis and upload results
gh codeql-scan
```

```bash
# `init` mode: Create only the Codeql database
gh codeql-scan init --auto-detect
# or manually set language
gh codeql-scan init -l=java 
```

```bash
# `analyze` mode: Run query-suites on an existing database (auto-detects databases)
gh codeql-scan analyze
```

```bash
# `upload` mode: Upload all SARIF files
gh codeql-scan upload
```

## License 

This project is licensed under the terms of the MIT open source license. Please refer to [MIT](./LICENSE.md) for the full terms.

## Maintainers 

- @GeekMasher

## Support

Support is via [GitHub Issues](https://github.com/advanced-security/gh-codeql-scan/issues)

## Acknowledgement
