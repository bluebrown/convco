# Convco

A Conventional commit cli.

`convco` gives tools to work with [Conventional Commits][1].

The tool is still in early development.
It provides already the following commands:

- `convco check`: Checks if a range of commits is following the convention.
- `convco version`: Finds out the current or next version.
- `convco changelog`: Create a changelog file.

## Installation

`cargo install convco`

## Tools

### Check

Check a range of revisions for compliance.

It returns a non zero exit code if some commits are not conventional.
This is useful in a pre-push hook.

```sh
convco check $remote_sha..$local_sha
```

### Version

When no options are given it will return the current version.
When `--bump` is provided, the next version will be printed out.
Conventional commits are used to calculate the next major, minor or patch.
If needed one can provide `--major`, `--minor` or `--patch` to overrule the convention.

```sh
convco version --bump
```

### Changelog

A changelog can be generated using the conventional commits.
It is inspired by [conventional changelog][2].
Configuration follows the [conventional-changelog-config-spec][3]

```sh
convco changelog > CHANGELOG.md
```

#### TODO

- [x] automatic notes for breaking changes
- [ ] custom template folder
- [x] use a `.versionrc` file
- [x] limit to a range of versions
- [x] sort sections in changelog
- [x] issue references

[1]: https://www.conventionalcommits.org/
[2]: https://github.com/conventional-changelog/conventional-changelog
[3]: https://github.com/conventional-changelog/conventional-changelog-config-spec/blob/master/versions/2.1.0/README.md
