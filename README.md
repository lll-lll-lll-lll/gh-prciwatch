# gh-prciwatch

`gh-prciwatch` is a shell script that uses GitHub CLI to monitor the CI status of a pull request for a specified branch.

## Features

- Automatically detects the pull request for the specified branch.
- Periodically checks the CI status and waits for completion.
- If the CI fails, it immediately outputs the PR URL and exits.
- Allows setting a timeout to forcefully exit if CI does not complete within the specified time.
- Outputs the PR URL with a custom message upon success.

## Installation

1. Ensure that `gh` (GitHub CLI) is installed.
2. Ensure that the `jq` command is available.

```sh
gh extension install lll-lll-lll-lll/gh-prciwatch
```

## Usage

```sh
gh prciwatch [OPTIONS]
```

### Options

| Option                 | Short Form     | Description                              |
| ---------------------- | ------------- | ---------------------------------------- |
| `--message <msg>`     | `-m <msg>`    | Message to display upon success         |
| `--timeout <minutes>` |               | Timeout duration in minutes (default: 20) |
| `--branch <branch>`   | `-b <branch>` | Specify the branch to monitor (defaults to the current branch) |

## Examples

### 1. Monitor the CI of the current branch's PR with default settings

```sh
gh prciwatch
```

### 2. Monitor with a custom success message

```sh
gh prciwatch --message "CI passed!"
```

### 3. Set a timeout of 30 minutes

```sh
gh prciwatch --timeout 30
```

### 4. Monitor a specific branch

```sh
gh prciwatch --branch my-feature-branch
```

## Example Script: `notify`
[notify](example/notify)
[terminal-notifier](https://github.com/julienXX/terminal-notifier)

A helper script named `notify` is available to enhance the usage of `gh-prciwatch` by providing desktop notifications using `terminal-notifier`. This script:

- Runs `gh prciwatch` with the specified options.
- Captures the output and exit code.
- Uses `terminal-notifier` to display notifications based on the CI results.
- Copies the PR URL to the clipboard if the CI succeeds.

### Usage

```sh
notify --message "CI check in progress" --branch my-feature-branch --timeout 30
```

## Notes

- You must be authenticated with `gh`.
- `jq` must be installed for this script to function.
- If the timeout is exceeded, the script exits with status code 2.
- `terminal-notifier` must be installed for notifications to work.

## License

MIT License

