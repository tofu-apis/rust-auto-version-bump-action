# Github Revert Commit Action

This action reverts the given commit in the Github Action Workflow

## Inputs

## `commit-username`

**Optional** Username to execute commits to Github with

## `commit-email`

**Optional** Email to execute commits to Github with

## `github-token`

**Required** Github Action generated secret token for authentication purposes

## `is-push-enabled`

**Required** Parameter to enable or disable the push of the revert (defaulting to false for safety/testing).

## `is-tagging-enabled`

**Required** Enables the tagging to the repo with the new version; otherwise does a dry run. Note that enabling this requires "is-push-enabled" to be enabled as well.

## `ssh-repo-access-key`

**Optional** \[SECRET\] Github SSH Key for accessing a given repo. This is used for accessing private repos that are dependencies in Cargo.toml

## Outputs

## `current-package-version`

Current (or previous) package version to be bumped

## `new-package-version`

New package version to be bumped to

## Example usage
```
  # Automatic version bumping of the patch version by default
  # This should execute only if the tests job passes
  automatic-version-bump-and-tag:
    needs: tests
    runs-on: ubuntu-latest
    steps:
      - uses: tofu-apis/rust-auto-version-bump-action@v0.0.30
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          is-push-enabled: true
          is-tagging-enabled: true
```
