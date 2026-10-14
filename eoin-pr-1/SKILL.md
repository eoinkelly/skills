---
name: eoin-pr-1
description: 'Draft a GitHub pull request description from the current branch compared with main. Use when asked to summarize branch changes, write PR copy, or produce paste-ready raw Markdown grounded in a Git diff.'
argument-hint: 'Optional focus, audience, or required PR template'
user-invocable: true
---

# GitHub PR Description

Create a concise, accurate, paste-ready GitHub pull request description for the changes on the current branch relative to `main`.

## Procedure for creating the GitHub PR description

1. Confirm the repository root, current branch, and working-tree state. Identify the intended base as `main`, resolving to the available local or remote-tracking ref (usually `main` or `origin/main`). If no suitable base ref exists, report the blocker rather than guessing.
2. Find the merge base between the current branch and the chosen base, then inspect the committed PR diff from that merge base to `HEAD`. Review the changed-file summary and relevant full diffs. Inspect commit messages and nearby tests or documentation only as needed to understand intent and behavior.
3. Treat committed branch changes as the PR scope. Check the working tree so uncommitted edits are not accidentally described as part of the PR. Mention that they were excluded only when it materially affects the requested result. Do not stage, modify, or discard files.
4. Derive the description from evidence in the diff. Explain the user-visible or operational outcome, then summarize the important implementation changes. Include testing only when the repository or user provides evidence of tests run; distinguish verified results from suggested or unavailable checks. Do not infer motivation, impact, compatibility, or test success without evidence. If unsure, ask for clarification and motivation for changes.
5. If the diff is empty, the base is ambiguous, or the branch includes unusually broad or unclear changes that prevent an accurate summary, ask a focused question or state the limitation instead of fabricating details.
6. Check for a repository pull request template and follow its structure when present, preserving prompts and headings while filling them with evidence-based content. If there is no template and the user has not requested another format, use a short title followed by `## Summary`, `## Changes`, and `## Testing`.
7. Return raw Markdown. Keep bullets specific and avoid duplicating the same point across sections. Omit empty sections when using the default format; do not add preamble, analysis, file-by-file narration, or unsupported claims.

## Procedure for formatting the output in chat output

format the description generated above as raw markdown in a code block
