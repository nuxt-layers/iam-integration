# Plan

> **In short:** defer IAM suite composition modernisation until its individual capability contracts and implementations have been migrated and accepted. Then update this integration repository against their current `master` branches without weakening security or adding cross-capability coupling.

## Current status

| Status | Work |
|---|---|
| Complete | Establish existing reference adapters and suite processes as a baseline for review |
| Waiting on dependency | Complete the remaining `nuxt-layers/authorisation` architectural, package, configuration and contract migration |
| Waiting on dependency | Complete the remaining `nuxt-layers/profile` architectural, package, configuration and contract migration |
| To verify | Confirm Identity and Authentication's accepted current `master` contracts and migration status before integrating them |
| Outstanding | Migrate this repository's obsolete `nuxt4-layers` package scope, repository URLs, dependency declarations and documentation to version-agnostic `nuxt-layers` names and current `master` development sources |
| Outstanding | Reconcile suite adapters against the accepted shared caller, decision and scheduled-task shapes in ADR-0012, following any formally accepted amendment |
| Outstanding | Replace repeated host-owned suite wiring with the agreed integration composition entry point, preserving capability ownership and the ADR-0012 host composition budget |
| Outstanding | Refresh dependent consumer lockfiles to accepted `master` commits and run integration, security, contract and acceptance checks |

## Migration sequence

1. **Complete Authorisation independently.** Review design against accepted `architecture-rules`, reconcile code and public `CONTRACT.md`, migrate configuration and dependencies, and accept its own tests and minimal-host integration.
2. **Complete Profile independently.** Apply the same architectural, package, security, contract and minimal-host review. Neither capability should be changed solely to accommodate an unfinished integration layer.
3. **Verify all IAM member contracts.** Read only the accepted public contracts of current `master` for Identity, Authentication, Authorisation and Profile. Resolve any provider contract defects in their owning repositories.
4. **Accept shared shapes.** Establish common caller, decision and scheduled-task semantics through the governing ADR process before making breaking integration changes. An open or draft ADR proposal does not supersede accepted rules.
5. **Modernise IAM Integration.** Update this repository's scope, package metadata, documentation and adapters; implement suite-level composition using only members' published interfaces. Consumers must not need to write their own adapters.
6. **Verify the composed suite.** Use latest accepted `master` dependencies and frozen lockfile resolutions. Test authentication assurance (including recency and phishing resistance), tenant/resource isolation, fail-closed decisions, governance approvals, revocation, event delivery and scheduled work. Record affected-consumer results and unresolved failures.

## Architectural boundaries

- Each IAM capability owns its data, policy enforcement, public ports, security rules and task handlers. Its `CONTRACT.md` describes its own public integration surface, not a particular consumer.
- This repository owns only cross-capability adapters, shared composition and suite-wide processes; it does not become a source of truth for identities, authentication, authorisation policies or profile data.
- Existing code is evidence of required security behaviour, **not** proof that the capability has completed its migration or complies with the latest architecture.
- No shared-interface migration may erase reliable authentication times, phishing-resistance evidence, tenant isolation, independent approvals or fail-closed behaviour.
- Scheduled work is capability-owned and executor-neutral; integration must not depend on or import a specific Scheduler implementation.
- Development dependencies follow current accepted `master`, not historical release tags or obsolete pinned sources (ADR-0008).
- Implement changes through protected-branch pull requests in the repository that owns each change.

**Gate:** Do not begin the suite's breaking adapter/composition migration until Authorisation and Profile are migrated, their public contracts accepted, and the relevant shared architectural shapes approved. Independent documentation or preparatory audits may proceed beforehand.
