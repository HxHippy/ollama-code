# Security Advisory: NPM Package Name Conflict

## Issue
The current package name `olc` conflicts with a malicious package on NPM that performs JavaScript syntax sabotage by replacing semicolons with Greek question marks (U+037E), which breaks JavaScript parsing.

## Risk
- Users attempting to install this legitimate package might accidentally install the malicious one
- The malicious package can break JavaScript codebases silently
- Creates security and reliability concerns for users

## Solution
This PR renames the package from `olc` to `ollama-code` to:
- Avoid the naming conflict with the malicious package
- Provide a more descriptive name that clearly indicates the package's purpose
- Ensure safe distribution via NPM

## Changes Made
- Updated `package.json` name from `"olc"` to `"ollama-code"`
- Updated binary command from `"olc"` to `"ollama-code"`
- Maintained all existing functionality and file structure

## Verification
The malicious `olc` package can be verified at: https://www.npmjs.com/package/olc
(Note: Do not install - it is malicious)

## Recommendation
After this fix, users should install with:
```bash
npm install -g ollama-code
```

And run with:
```bash
ollama-code
```

This ensures they get the legitimate package and avoid the security risk.