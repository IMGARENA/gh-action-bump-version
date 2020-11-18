## IMGARENA: gh-action-bump-version

This is a simplified / more adapted to our use case version of phips28/gh-action-bump-version


This Action bumps the version in package.json and pushes it back to the repo. 

It can be used in repositories that want automatic version bumping before publishing to npm. Look at an example of use in golf-3d-map project.

### Workflow

* Based on the commit messages, increment the version from the latest release.

  * If the string "MAJOR:" is found anywhere in any of the commit messages or descriptions the major 
    version will be incremented.
  * If a commit message contains "MINOR:", the minor version will be incremented.
  * All other changes will increment the patch version.
* Push the bumped npm version in package.json back into the repo.
* Push a tag for the new version back into the repo, including the PR name as a description of the tag.

### Usage:
**tag-prefix:** Prefix that is used for the git tag  (optional). Example:
```yaml
- name:  'Automated Version Bump'
  uses:  'phips28/gh-action-bump-version@master'
  env:
    GITHUB_TOKEN: ${{ secrets.ACTION_GITHUB_TOKEN }} #this secret need to exist as the action needs admin privilege to overwrite protected branch protection.
  with:
    tag-prefix:  ''
```

**PACKAGEJSON_DIR:** Param to parse the location of the desired package.json (optional). Example:
```yaml
- name:  'Automated Version Bump'
  uses:  'phips28/gh-action-bump-version@master'
  env:
    GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
    PACKAGEJSON_DIR:  'frontend'
```
