# Changelog

## 0.0.4

### Changes

- Update abi-typegen to 0.9.1, viem to 2.57.17, Vitest and V8 coverage to 5.1.0, and forge-std to 1.17.0.
- Upgrade to TypeScript 7.0.2 and pnpm 12.18.0. Use NodeNext module resolution and explicit source roots for CommonJS builds, with a separate project configuration for generated contract bindings.
- Update Node.js typings to 24.19.2 to match the Node.js 24 CI runtime. Source development requires Foundry 1.8.3 or newer.

The evaluator API, Solidity contracts, and proof format are unchanged from 0.0.3. Existing 0.0.3 proofs and deployed verifiers remain compatible.

## 0.0.3

### Compatibility

This release changes the Sloth round construction. Proofs produced by `0.0.2` and earlier are incompatible. Upgrade the TypeScript evaluator and Solidity verifier together, then recompute proofs. Existing deployed verifiers retain their old behavior and require replacement to use the repair.

### Changes

- Restore the reversible inter-round permutation and signed square-root rules, removing the direct exponent-collapse shortcut in the older implementation.
- Bind example seeds to a future block hash, caller, contract, and chain. Require seed finalization before accepting a proof, with expiry and single-result finality checks.
- Validate inputs and require canonical proof outputs in TypeScript and Solidity.
- Move development to pnpm and Foundry, and export generated viem bindings from `@0xdoublesharp/sloth-vdf/contracts` using abi-typegen.
- Add unit, cross-language integration, fuzz, and stateful invariant tests, with full production-source coverage checks.
- Publish GitHub releases to npm through OIDC with provenance.

Iterations specify sequential work, not a guaranteed duration. Applications must lock outcome-dependent choices before the future block hash becomes available and calibrate the iteration count for their threat model. See the [security model](README.md#security-model).
