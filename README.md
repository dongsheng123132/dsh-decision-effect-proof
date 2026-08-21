# dsh-decision-effect-proof

Offline, deterministic proof that a recorded DSH authorization decision and its recorded effect envelope agree. It catches denied actions with effects, authorized actions that never settled, request/state/policy mismatches, missing confirmation, replayed idempotency digests, duplicates and out-of-order evidence. Reports are content-addressed and read back after publication.

This is deliberately **not** an approval engine, policy evaluator, action runtime, signature format or prompt wrapper. `dsh-user-approval`, `dsh-auto-approval`, `dsh-tiered-approval` and `dsh-permission-rules` decide or enforce access. ACTA/SEP-style systems authenticate decision receipts. This plugin consumes explicit body-free evidence and checks the narrower boundary those layers cannot imply: **authorized does not mean executed**. It does not prove that an effect occurred; it proves only that the supplied receipts are internally consistent and discloses that limit in every report.

## Install

```sh
dsh plugin --profile web add github:dongsheng123132/dsh-decision-effect-proof#COMMIT
```

## Use

```sh
dsh-decision-effect-proof inspect examples/decision-effects.json
dsh-decision-effect-proof verify examples/decision-effects.json artifacts
```

DSH tools: `dsh_decision_effect_inspect`, `dsh_decision_effect_verify`. MCP tools: `decision_effect_inspect_inline`, `decision_effect_verify_inline`. MCP accepts inline JSON only and cannot choose filesystem paths. File tools accept workspace-relative paths, reject traversal and symlinks, cap input size, write only beneath an explicit artifact directory, publish atomically, and verify by read-back.

The evidence schema stores SHA-256 digests and bounded identifiers, never request arguments, tool output, business text, prompts, messages or secrets. See `examples/decision-effects.json`.

## Verdicts

- `verified`: the supplied authorization/effect envelopes reconcile under the manifest policy.
- `rejected`: one or more stable finding codes explain the mismatch.
- CLI exit `0`: verified/inspection; `2`: rejected; `1`: invalid input or usage.

## Verify the repository

```sh
npm test
npm run check
npm run smoke:plugin
npm run smoke:mcp
```

MIT licensed. Security boundaries are documented in [SECURITY.md](SECURITY.md).
