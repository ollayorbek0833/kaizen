# Contributing

`main` is protected. All changes reach it through a reviewed pull request with green CI. Nobody pushes to `main` directly, admins included.

## Workflow

1. **Open or pick an issue.** Use one of the templates: *User story*, *Bug report* or *Technical task*. Blank issues are disabled.
2. **Branch from `main`.** Name the branch after the type and story ID:
   - `feature/SAL-7-discount-lists`
   - `fix/INV-3-negative-stock`
   - `chore/ci-cache`
3. **Commit with the story ID** in the message, e.g. `Add low-stock threshold per product (INV-5)`.
4. **Open a pull request into `main`.** The template asks for the linked issue, how you tested it, and the Definition of Done checklist. Write `Closes #<issue>` so the issue closes on merge.
5. **CI runs automatically.** All three checks must pass:
   | Check | What it runs |
   |---|---|
   | `backend` | `mvn verify`: unit tests, integration tests, and `ArchitectureTest` (module boundaries) |
   | `frontend` | `npm ci`, `npm run lint`, `npm run build` (TypeScript check plus production build) |
   | `docker` | Builds the backend and frontend images from the Dockerfiles |
6. **Get one approval from a code owner.** Owners from [`.github/CODEOWNERS`](.github/CODEOWNERS) are requested automatically. You can't approve your own PR.
7. **Merge** once CI is green, the approval is in and all review conversations are resolved. If `main` moved in the meantime, update your branch first.

## Branch protection on `main`

| Rule | Setting |
|---|---|
| Pull request required before merging | Yes |
| Required approvals | 1 |
| Review from a code owner required | Yes |
| New commits dismiss earlier approvals | Yes |
| Required status checks | `backend`, `frontend`, `docker` |
| Branch must be up to date with `main` | Yes |
| All conversations resolved | Yes |
| Rules also apply to admins | Yes |
| Force pushes and branch deletion | Blocked |

## Delivery (CD)

Every merge into `main` runs the same pipeline. When it passes, it publishes two images to GitHub Container Registry:

- `ghcr.io/ollayorbek0833/kaizen-backend`
- `ghcr.io/ollayorbek0833/kaizen-frontend`

Each image is tagged `latest` and `sha-<commit>`, so any merged version can be pulled and run again.

## Run the checks locally before pushing

```bash
mvn verify                                          # backend (JDK 21)
cd frontend && npm ci && npm run lint && npm run build
```
