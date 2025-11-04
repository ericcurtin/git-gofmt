# git-gofmt

A Git command-line extension that automatically formats Go code using `gofmt` in a manner similar to `git-clang-format`. This utility finds all staged Go files, formats them using `gofmt -w`, and re-stages the changes.

## Purpose

This script helps maintain consistent code formatting in Go projects by ensuring all committed code follows the standard Go formatting conventions enforced by `gofmt`. It's particularly useful as a pre-commit hook or for manual formatting before committing code.

## Installation

1. Clone or download this repository
2. Make the script executable:
   ```bash
   chmod +x git-gofmt
   ```
3. Place the script in your PATH (e.g., `/usr/local/bin`, or `~/bin` which should be in your PATH)
4. The script can now be run as `git gofmt` from within any Git repository

## Usage

### Format staged files (default behavior)
```bash
git add .                    # Stage your changes
git gofmt                    # Format only staged .go files
```

### Format all Go files in the repository
```bash
git gofmt -f                 # Format all .go files, not just staged ones
```

## How it works

- When run without arguments, `git-gofmt` identifies all staged `.go` files in your repository
- It runs `gofmt -w` on these files to format them in-place
- The formatted files are automatically re-staged to preserve the formatting changes in your commit
- When using the `-f` flag, it formats all `.go` files in the repository rather than just staged files

## Features

- Mimics the behavior of `git-clang-format` for Go code
- Automatically stages formatted files
- Supports formatting all files or only staged files
- Handles large numbers of files efficiently using `xargs`
- Excludes deleted files from formatting operations

## Requirements

- Git
- Go (with `gofmt` in your PATH)
- bash

