# gh-codeql-scan

GH CLI CodeQL Scan Extension

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
gh codeql-scan init --la--auto-detect 
```

```bash
# `analyze` mode: Run query-suites on an existing database (auto-detects databases)
gh codeql-scan analyze
```

```bash
# `upload` mode: Upload all SARIF files
gh codeql-scan upload
```


