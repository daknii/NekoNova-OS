# Development Principles

This document describes how NekoNova should be built and maintained.

## Start with the smallest useful change

Prefer a small, reviewable improvement over a large rewrite. Establish
the existing behavior, define the expected result, make the change, and
test it.

## Respect upstream software

NekoNova initially builds on Arch Linux and KDE Plasma. Keep upstream
components identifiable and avoid unnecessary forks. When a behavior can
be configured cleanly, prefer configuration over maintaining a patch.

Before adding a dependency or custom component, answer:

-   What user problem does it solve?
-   Can an existing maintained tool solve it?
-   Who will maintain it?
-   What happens when it fails or upstream changes?

## Reproducibility

-   Keep project-owned configuration in version control.
-   Document required packages and supported versions.
-   Avoid relying on undocumented manual steps.
-   Make scripts safe to rerun where possible.
-   Do not store credentials, tokens, or private user data in the
    repository.
-   Do not run destructive operations without clear explanation and
    explicit user confirmation.

## Testing

Test changes in a virtual machine or disposable environment before
recommending them for a user's main system.

For desktop changes, check: - Launch, close, minimize, maximize, and
switch windows. - Panel, launcher, tray, and keyboard shortcuts. - Light
and dark backgrounds where relevant. - Different display scaling
settings. - Keyboard navigation and focus visibility. - Behavior when
optional effects are unavailable. - Whether the system remains usable if
a custom component crashes.

For scripts and system changes, check: - Missing dependencies. - Invalid
input and unexpected state. - Repeated execution. - Clear failure
messages. - Recovery or rollback when practical.

## Documentation

Document how to reproduce the setup, what is supported, known
limitations, and how to undo changes. Keep the README aligned with the
actual repository state.

## Visual quality

Visual polish is more than blur and rounded corners. Review hierarchy,
spacing, contrast, typography, consistency, responsiveness,
accessibility, and performance. Effects must not make text hard to read
or interactions hard to discover.

## Security and trust

-   Prefer signed packages and established upstream distribution
    mechanisms.
-   Never claim the system is secure simply because it is open source.
-   Do not request unnecessary permissions.
-   Explain system-level changes before users run them.
-   Keep experimental features clearly labelled.
-   Do not collect telemetry unless there is a documented purpose,
    disclosure, and meaningful user choice.

## Pull request expectations

A useful change should explain the problem, the approach, how it was
tested, and any known limitations. Screenshots are helpful for visual
changes, but they do not replace source changes or functional tests.
