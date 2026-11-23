## What and why

<!-- One or two sentences: what this PR changes and why. -->

Closes #<!-- issue number -->
Story: <!-- e.g. SAL-3, or "none" for technical tasks -->

## Type of change

- [ ] Feature (user story)
- [ ] Bug fix
- [ ] Refactor / technical task
- [ ] Tests only
- [ ] Docs / configuration

## How it was tested

<!-- Steps a reviewer can follow, the test classes you added or changed, and the example data you used. -->

## Screenshots

<!-- For UI changes: before and after. Delete this section otherwise. -->

## Checklist

- [ ] CI is green: backend tests, frontend lint/types/build, Docker images
- [ ] New or changed behaviour has a unit or integration test
- [ ] `ArchitectureTest` passes: modules don't import each other, and cross-module code is in `composition/`
- [ ] Ledger stays balanced after every posting this PR adds or changes
- [ ] Controllers return DTOs, not domain or JPA entities
- [ ] No secrets, `.env`, `data/` or log files committed
- [ ] README or docs updated if setup or behaviour changed
