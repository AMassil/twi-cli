# Contributing to twi-cli

Thank you for your interest in contributing. The following guidelines will help you get started and keep the project consistent.

---

## Getting Started

1. Fork the repository on GitHub.
2. Clone your fork locally:

   ```bash
   git clone https://github.com/yourusername/twi-cli.git
   cd twi-cli
   ```

3. Create a new branch for your change:

   ```bash
   git checkout -b feature/your-feature-name
   ```

4. Make your changes, test them thoroughly, and commit.

5. Push your branch and open a pull request against `main`.

---

## Code Style

twi-cli is written in Bash. Please follow these conventions:

- Use 4-space indentation throughout.
- Quote all variable expansions: use `"$var"` rather than `$var`.
- Use `local` for all variables declared inside functions.
- Prefer `[[ ]]` for conditionals where Bash-specific behavior is intentional; use `[ ]` otherwise.
- Keep functions small and focused on a single responsibility.
- Add a comment above any non-obvious block of code.
- Run your script through `shellcheck` before submitting and resolve any warnings.

```bash
shellcheck twi-cli.sh
```

---

## Testing

There is no automated test suite at this time. Before submitting a pull request, manually verify:

- The main menu launches and all options are reachable.
- Your specific change works as expected in at least one realistic scenario.
- No regressions in existing functionality (follows sync, search, stream playback, settings).
- The script exits cleanly on `Ctrl+C` and when the user selects Exit.

If you are adding a new feature, describe how you tested it in the pull request body.

---

## Reporting Bugs

Open an issue and include the following:

- A clear description of the problem and what you expected to happen.
- The exact command or sequence of steps that triggered the bug.
- Your operating system and shell version (`bash --version`).
- Versions of key dependencies (`fzf --version`, `jq --version`, `streamlink --version`).
- Any relevant error output, with ANSI color codes stripped if possible.

---

## Requesting Features

Open an issue with the label `enhancement`. Describe the feature, the problem it solves, and any implementation ideas you have. Discussion before implementation is encouraged for larger changes.

---

## Pull Request Guidelines

- Keep pull requests focused. One logical change per PR.
- Write a clear title and description explaining what changed and why.
- Reference any related issues using `Closes #N` or `Related to #N` in the description.
- Do not include unrelated formatting or whitespace changes.
- Be responsive to review feedback. PRs with no activity after 30 days may be closed.

---

## Commit Messages

Follow the conventional commit format:

```
type: short description in imperative mood

Optional longer explanation if needed.
```

Common types: `feat`, `fix`, `docs`, `refactor`, `chore`.

Examples:

```
feat: add VOD browsing to main menu
fix: handle empty stream title in follows cache
docs: document import format in CONTRIBUTING
```

---

## Scope and Non-Goals

To keep the tool focused, the following are explicitly out of scope:

- GUI or web interface wrappers
- Chat integration
- Authentication via OAuth or Twitch developer credentials
- Support for platforms other than Twitch

If you are unsure whether your idea fits the scope, open an issue to discuss before writing code.
