# GitHub PR CI Monitor

## Overview

This script is a GitHub CLI extension that monitors the CI status for a specified branch's GitHub Pull Request (PR). If the CI status becomes `SUCCESS`, it prints the PR URL along with a specified message. If the status is `FAILURE`, it simply prints the PR URL and exits. Additionally, if the CI does not complete within a specified time limit, the script exits with a timeout message.

## Requirements

- GitHub CLI (`gh`) must be installed.
- You must be authenticated with `gh` (execute `gh auth login`).

## Installation

```sh
gh extension install lll-lll-lll-lll/gh-prciwatch
```

## Example Usage
example path: https://github.com/lll-lll-lll-lll/gh-prciwatch/blob/main/example/notify


```sh
notify [options]
```

### Options

| Option                     | Shortcut      | Description                                                  |
|----------------------------|---------------|--------------------------------------------------------------|
| `--message=<msg>`          | `-m=<msg>`    | Specify the message to display on success                    |
| `--timeout=<min>`          |               | Set the maximum wait time in minutes (default: 20 minutes)     |
| `--branch=<branch>`        | `-b=<branch>` | Specify the branch for the PR to monitor (default: current branch) |

## Examples


### Specify a custom message for slack

```sh
notify --message="@reviewer :review_please: "
# output example 
@reviewer :review_please: https://github.com/owner/repo/pull/123
```

### Monitor the PR for a specific branch

```sh
notify --branch=feature-branch
```

---

## Usage Example

Below is an example scenario that demonstrates the typical usage of the script:

1. **Scenario**: You're working on a feature branch named `feature/add-login` and want to monitor the PR associated with this branch. You also want to display a custom message once the CI passes.

2. **Command**:

    ```sh
    notify --branch=feature/add-login --message="Login feature is ready for review!"
    ```


## License

MIT

---

Feel free to modify or extend this document as needed!
