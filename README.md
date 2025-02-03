# GitHub PR CI Monitor

## Overview

This script is a GitHub CLI extension that monitors the CI status for a specified branch's GitHub Pull Request (PR). If the CI status becomes `SUCCESS`, it prints the PR URL along with a specified message. If the status is `FAILURE`, it simply prints the PR URL and exits. Additionally, if the CI does not complete within a specified time limit, the script exits with a timeout message.

## Requirements

- GitHub CLI (`gh`) must be installed.
- You must be authenticated with `gh` (execute `gh auth login`).

## Installation


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

3. **Behavior**:
    - The script retrieves the PR for the `feature/add-login` branch.
    - It checks the CI status every minute.
    - **If the CI status is `SUCCESS`**: The script outputs the custom message along with the PR URL, then exits with a status code of `0`.
    - **If the CI status is `FAILURE`**: The script outputs the PR URL and exits with a status code of `1`.
    - **If the CI does not complete within the default 20 minutes (or the specified timeout)**: The script outputs a timeout message and exits with a status code of `2`.

This example demonstrates how you can integrate the script into your workflow to automatically monitor your PR's CI status and receive immediate feedback based on the result.

---

## How It Works

1. The script retrieves the PR for the specified branch.
2. It checks the CI status periodically (every minute).
3. If the status is `SUCCESS`:
   - It outputs the provided `message` along with the PR URL.
   - Exits with `exit 0`.
4. If the status is `FAILURE`:
   - It outputs the PR URL.
   - Exits with `exit 1`.
5. If the elapsed time exceeds the specified timeout (`--timeout`):
   - It outputs a timeout message.
   - Exits with `exit 2`.

## Notes

- The script uses the `gh pr view` command to retrieve PR details, so appropriate permissions are required.
- The CI status check depends on the `gh pr checks` command; therefore, if you are using a CI system other than GitHub Actions, the script might not function as expected.

## License

MIT

---

Feel free to modify or extend this document as needed!
