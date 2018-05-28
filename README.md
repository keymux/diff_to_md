# Keymux Utilities - Diff to Markdown

Branch | Status
------ | ------
Master | [![Build Status](https://jenkins.keymux.org/job/keymux/job/diff_to_md/job/BuildMasterBranch/badge/icon)](https://jenkins.keymux.org/job/keymux/job/diff_to_md/job/BuildMasterBranch/)
Dev    | [![Build Status](https://jenkins.keymux.org/job/keymux/job/diff_to_md/job/BuildDevBranch/badge/icon)](https://jenkins.keymux.org/job/keymux/job/diff_to_md/job/BuildDevBranch/)

## Objective

Diff to Markdown is intended to enable a user to convert a scm diff to markdown.  This is particularly useful in generating comments on pull requests for things like changelog files to ensure that every pull request is accompanied by a change to the changelog.

## Options

name                  | Required  | Default                                   | Explanation
--------------------- | --------- | ----------------------------------------- | -----------------
startsWith            | no        | .changes                                  | Starting path to search for changes, usually a directory
noChangeMessage       | no        | No changes were found                     | The message to output if there are no modifications found
noChangeExitCode      | no        | -1                                        | The process exit code to use when no changes were found
gitDir                | no        | .git                                      | The location of the .git directory to use for diffing
diffAgainstReference  | no        | refs/remotes/origin/master                | The reference to diff against
diffFromReference     | no        |                                           | The reference to diff from (usually the current branch)

## Usage

```bash
#!/bin/bash

# Output a diff if changelog.txt has changed relative to my local master but don't error if not
yarn diff_to_md --startsWith=changelog.txt --diffAgainstReference=master --noChangeExitCode=0
```
