# gh-rsize

`gh-rsize` is a GitHub CLI extension to fetch the size of GitHub repositories without cloning them.

## Installation

To install the `gh-rsize` extension, follow these steps:

1. Ensure that you have [GitHub CLI](https://cli.github.com/) installed on your system.

2. Install the `gh-rsize` extension using the following command:

   ```bash
   gh extension install MohamedElashri/gh-rsize
   ```

This command will clone the `gh-rsize` repository to your local GitHub CLI extensions directory and make it available as a `gh` command.

## Usage

```bash
gh rsize <repository_url>... [--token <github_token>] [--unit <B|KB|MB|GB>] [--verbose] [--json] [--api-url <url>] [--full-size] [--debug]
```

If you did not include `--full-size` then the default behavior is to calculate the size for the main branch only. The Github API does not provide a full size option and it is is calculated by making a call for each branch and summing the sizes. This takes longer time and with large codebases might have problems with rate limiting. In most cases it will need to provide a token. Note that this method might still not capture the full history size, as it only considers the current state of each branch. Getting the true full history size would require cloning the repository locally, which is not practical for a tool like this.

### Options

- `--token`: GitHub API token for private repositories
- `--unit`: Unit to display size in (default: MB)
- `--verbose`: Display additional repository information
- `--json`: Output results in JSON format
- `--api-url`: Custom GitHub API URL for enterprise instances
- `--full-size`: Calculate the size of the entire repository (all branches and history)
- `--debug`: Enable debug mode for troubleshooting

## Examples

Fetch size of a single repository:
```bash
gh rsize https://github.com/owner/repo
```

Fetch size of multiple repositories:
```bash
gh rsize https://github.com/owner1/repo1 https://github.com/owner2/repo2
```

Use verbose output:
```bash
gh rsize https://github.com/owner/repo --verbose
```

Get JSON output:
```bash
gh rsize https://github.com/owner/repo --json
```

Use with GitHub Enterprise:
```bash
gh rsize https://github.com/owner/repo --api-url https://github.mycompany.com/api/v3
```

## Authentication

For private repositories or to avoid rate limiting, use a GitHub token:

```bash
gh rsize https://github.com/owner/repo --token YOUR_GITHUB_TOKEN
```

Alternatively, set the `GITHUB_TOKEN` environment variable.

## Features

- Fetch repository size without cloning
- Support for multiple repositories in a single command
- Verbose mode for additional repository information
- JSON output option for easy parsing
- Custom API URL support for GitHub Enterprise
- Display of API rate limit information

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License.
