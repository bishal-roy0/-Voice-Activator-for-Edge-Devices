# Contributing

## Working agreement

1. Read `docs/interfaces.md` before changing an integration boundary.
2. Work from your assigned member branch; do not commit directly to `main` or `dev`.
3. Keep commits focused, tested, and understandable.
4. Open pull requests to `dev`. The project leader reviews integration work before it reaches `main`.
5. Update the relevant interface or test document whenever a shared contract changes.

## Pull request checklist

- Explain the problem and the intended result.
- Include a repeatable test method and its result.
- Do not include secrets, raw recordings, personal data, generated binaries, or unrelated formatting changes.
- Link the related issue or document decision when applicable.
- Request review only when the branch is ready to integrate.

## Shared contract changes

Audio parameters, feature extraction, model tensors, network transport, and server responses are shared contracts. Propose their values in `docs/interfaces.md`; the affected owners and project leader must approve a decision before dependent code merges.

## Commit style

Use short imperative subjects, for example: `Add I2S capture timing log` or `Document model input contract`.
