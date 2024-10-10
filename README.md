<!-- markdownlint-disable -->
<div align="center">

<h1>gh-codeql-scan</h1>

[![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)][github]
[![GitHub Issues](https://img.shields.io/github/issues/advanced-security/gh-codeql-scan?style=for-the-badge)][github-issues]
[![GitHub Stars](https://img.shields.io/github/stars/advanced-security/gh-codeql-scan?style=for-the-badge)][github]
[![License](https://img.shields.io/github/license/advanced-security/gh-codeql-scan?style=for-the-badge)][license]

</div>
<!-- markdownlint-restore -->

[GitHub CLI CodeQL Scan Extension][github] to help abstract [CodeQL][codeql] away from users.

<details>
<summary>Motivation</summary>

This project was created to make the lives of users that use CodeQL simpiler.
CodeQL outside of GitHub Actions can be complicated but this projects aim is to make it as simple as possible.

</details>

## Requirements

- [GitHub CLI](https://cli.github.com/)
- [CodeQL GH Extension][gh-codeql] (optional)

## Install and Setup

This installs CodeQL and this scan tool:

```bash
gh extensions install github/gh-codeql
gh extensions install advanced-security/gh-codeql-scan

gh codeql-scan --help
```

<details>
<summary>CLI Help</summary>

<pre>
GitHub CodeQL Scan tool

gh codeql-scan {MODE} {ARGS}

# Modes

gh codeql-scan              # default: "scan"
gh codeql-scan init         # initialise the scan 
gh codeql-scan analyze      # run the analysis
gh codeql-scan upload       # upload present SARIF files
gh codeql-scan scan         # full end-to-end scan 

# Arguments

> All arguments can be set with enviroment variables

-h|--help               # Print help
--debug                 # Enable debugging
    
-r=*|--repo=*           # GitHub Respository (OWNER/NAME)
-i=*|--instance=*       # GitHub Instance (github.com or Enterprise Server)

-l=*|--language=*       # Set language to scan
--auto-detect           # Auto-detect languages

-s=*|--suite=*          # Query Suite to use
-d=*|--databases=*      # Location of the databases to store
-b=*|--binary=*         # Path to the CodeQL Binary
-w=*|--workspace=*      # Workspace for the souce code

-c=*|--command=*        # Set the build comment (compiled languages)
-m=*|--mode=*           # Build mode (autobuild | none)
--buildless             # Enable buildless / build mode none

--view-in-vscode        # Auto-open the results in VSCode

--disable-tracing       # Disable Build Tracing
--disable-trap-caching  # Disable Trap file caching
--disable-upload        # Disable Uploading SARIF to GitHub
--disable-banner        # Disable printing banner
</pre>

</details>

### Alias / Stub

A couple of tips and tricks:

```bash
# Create an alias to make things even easier
alias codeql-scan="gh codeql-scan"
```

## Usage

The main use of the script is to automatically run CodeQL in a number of modes.

```bash
# End-to-end analysis and upload results
gh codeql-scan
```

#### Initialise with language

Automatically detect languages or manually set the language to create an initial CodeQL database.

```bash
gh codeql-scan init --auto-detect
# or manually set language
gh codeql-scan init -l=java 
```

#### Scan without build

This will scan your code in build mode `none`.

```bash
gh codeql-scan -m="none"
# or simply
gh codeql-scan --buildless
```

#### Scan with Build Command

Pass in the build command for a compiled language and it will be run along with CodeQL.

```bash
gh codeql-scan -c "mvn build ..."
```

#### Indirect build tracing

For Compiled languages, complicated build process using indirect build tracing

```bash
gh codeql-scan init
echo "password=$password" > settings.xml
mvn build --random-custom=flags
gh codeql-scan analyze
```

#### Running analysis

Run query-suites on an existing database (auto-detects databases)

```bash
gh codeql-scan analyze
```

#### Uploading results to GitHub

The `upload` mode will upload all SARIF files for you to a repository

```bash
gh codeql-scan upload
```

## Maintainers 

- @GeekMasher

## Support / Maintainance

Support is via [GitHub Issues][github-issues]

## License 

This project is licensed under the terms of the MIT open source license.
Please refer to [MIT][license] for the full terms.

<!-- Resources -->

[license]: ./LICENSE
[github]: https://github.com/advanced-security/gh-codeql-scan
[github-issues]: https://github.com/advanced-security/gh-codeql-scan/issues
[codeql]: https://codeql.github.com/
[gh-codeql]: https://github.com/github/gh-codeql

