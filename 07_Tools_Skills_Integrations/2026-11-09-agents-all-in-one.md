# Combined AGENTS Research Delta



---

<!-- Source: 00_README.md -->

# AGENTS research delta (2026-11-09)

This folder is a **non-destructive extraction** of the newly uploaded `AGENTS.md` template ZIP and the 13-page customization PDF, compared to the older iPhone research-library ZIP.

## Verified input inventory

- Uploaded ZIP: **8 actual files** (plus directory entries), **7 distinct byte contents**. The two nested `CLAUDE.md` files are byte-identical; both paths are kept because they serve different directories.
- Root `AGENTS.md`: **100 lines**, **6878 bytes**, **68 bullet directives**.
- Numbered bullet directives across the three AGENTS files: **84** (not a count of distinct ideas).
- Guide: **13 PDF pages**, **16 links in its reference list**.
- Baseline: previous research library ZIP, containing **38 Markdown/TXT sources**.
- Exactly identical new-template **whole files** inside the older Markdown/TXT library: **0**. This tells us nothing about thematic duplication.

## Most useful files

- `research/01_distinct_practical_details.md` - focused new operational details and provenance.
- `research/02_overlap_and_disagreements.md` - precise duplicates vs topic overlap and conflicting claims.
- `research/03_code_and_setup.md` - copyable **unmodified** configuration and command blocks.
- `research/04_source_checks.md` - reference links and what was / was not verified.
- `research/05_all_guidance_categorized.md` - all 84 source instructions indexed by section; nothing silently discarded.
- `indexes/` - complete CSV audit trails and PDF text with page markers.
- `unmodified_templates/` - all 8 original template files in their intended nested paths.
- `original_sources/` - verbatim original ZIP/PDF retained.

**Interpretation:** the template is preserved as source material only. No repository settings, developer credentials, security files, contract, or implementation have been changed.

**Execution limit:** no macOS/Xcode or real iPhone was available. JSON and YAML parsing and Python-regex sample checks can be run locally; SwiftLint, Codex CLI, Claude Code, Xcode MCP and app signing are **not** proven by this report.



---

<!-- Source: 01_distinct_practical_details.md -->

# Distinct practical details extracted from AGENTS template + PDF

The notes below keep source provenance and distinguish executable configuration from claims that still need validation. A previously mentioned *topic* does not make a newly supplied file or command redundant.

## 01. Agent instruction discovery
Codex reads global plus project root-to-CWD AGENTS.md; recognizes AGENTS.override.md and uses a 32 KiB default combined size limit. The config setting project_doc_max_bytes can change this limit.
- **Origin:** Guide pp.1-2; Codex official reference [1]
- **Why retained:** Operational detail, beyond generic AGENTS.md mentions

## 02. Claude import bridge
The root CLAUDE.md has an @AGENTS.md import, followed by optional Claude-only instructions. The two nested CLAUDE.md files contain only @AGENTS.md.
- **Origin:** Template CLAUDE.md and nested files; guide pp.1-2,5
- **Why retained:** Reusable concrete files

## 03. Claude AGENTS.md claim conflict
The PDF says Claude Code >=2.1.277 can directly read AGENTS.md without CLAUDE.md; current official Claude memory page explicitly says Claude reads CLAUDE.md, not AGENTS.md. Preserve both statements; treat direct-reading claim as unverified and conflicting.
- **Origin:** Guide pp.1-2 vs Claude official docs [2]
- **Why retained:** Correction, not deletion

## 04. Nested instruction loading
Codex does not automatically find deeper AGENTS.md from repo root. The root template explicitly instructs the agent to read the Security and CoreAPIKit subfiles before edits.
- **Origin:** Guide pp.1-2,5; root AGENTS.md
- **Why retained:** Specific loading workaround

## 05. Model hints vs enforcement
Text in AGENTS.md/CLAUDE.md is agent context, not reliable access control. The separate .claude/settings.json asks approval for risky edits, but cannot prevent arbitrary scripts from modifying files.
- **Origin:** Guide p.6, template settings.json; Claude official docs [2,8]
- **Why retained:** Important limitation

## 06. Claude edit permission prompts
Ask entries cover *.entitlements, Info.plist, PrivacyInfo.xcprivacy, CoreAPIKit/**/openapi.yaml, AGENTS.md and CLAUDE.md.
- **Origin:** Template .claude/settings.json; guide p.6
- **Why retained:** Exact configuration provided

## 07. Three custom SwiftLint checks
The template config uses regex rules against weak Keychain accessibility, print(...) in app code, and NavigationView; test-file exclusions are specified for the print rule.
- **Origin:** Template .swiftlint.yml; guide pp.6-7
- **Why retained:** Actual executable configuration, not only advice

## 08. SwiftLint regex limits
Regex rules can miss aliases and multi-line patterns; the PDF reports Python-regex examples, not an actual SwiftLint run. Official SwiftLint docs verify custom_rules support, not these three policies in a live Xcode project.
- **Origin:** Guide pp.6-7; SwiftLint docs [9]
- **Why retained:** Scope of evidence

## 09. First-setup placeholders
The root template still contains <AppName>, <name>, <YYYY-MM-DD>, <App>, <UDID>, <docs/signing-protocol.md>. These are intentionally unresolved; no Xcode project is present.
- **Origin:** Root AGENTS.md
- **Why retained:** Cannot execute commands as-is

## 10. Concrete smoke commands
The guide specifies grep -rn to find placeholders, xcodebuild -list and xcrun simctl, wc -l -c for budget checks, and Codex instruction-loading checks. These require a Mac/project for actual runs.
- **Origin:** Guide p.8; root AGENTS.md
- **Why retained:** Testable sequence

## 11. Keychain error distinction
errSecItemNotFound is mapped to absent session; errSecInteractionNotAllowed to a locked device, with retry after unlock, without switching to weaker storage.
- **Origin:** Infrastructure/Security/AGENTS.md
- **Why retained:** Precise error recovery behavior

## 12. Keychain reinstall handling
The security template warns that Keychain records can survive app deletion; a first-install flag and stale-item cleanup are explicitly specified.
- **Origin:** Infrastructure/Security/AGENTS.md
- **Why retained:** Operational note; platform behavior requires validation

## 13. Secure Enclave serialized key
Only the key dataRepresentation is stored in Keychain. Invalidated biometric authorization triggers re-enrollment with Core rather than silent key recreation.
- **Origin:** Infrastructure/Security/AGENTS.md
- **Why retained:** Specific key lifecycle

## 14. Golden canonical envelope
Signing fixture bytes must match Core; tests use a fake ApprovalSigner and must not rewrite canonical golden fixtures to make an assertion pass.
- **Origin:** Security AGENTS.md; root AGENTS.md
- **Why retained:** Cross-system test invariant

## 15. OpenAPI generator config
CoreAPIKit template provides generate: [types, client] and accessModifier: internal in openapi-generator-config.yaml; sources are generated at build time.
- **Origin:** CoreAPIKit/AGENTS.md
- **Why retained:** Concrete config fields

## 16. OpenAPI unknown status handling
Documented responses are mapped explicitly; .undocumented(status, _) maps to CoreError.undocumented(status).
- **Origin:** CoreAPIKit/AGENTS.md
- **Why retained:** Specific client failure mapping

## 17. SPM dependency pinning
swift-openapi-generator, swift-openapi-runtime and swift-openapi-urlsession are pinned to compatible versions in Package.resolved.
- **Origin:** CoreAPIKit/AGENTS.md
- **Why retained:** Concrete dependency lifecycle

## 18. OpenAPI diff gate
oasdiff checks breaking changes in CI before merge. This is specified but no CI configuration is included in the supplied ZIP.
- **Origin:** CoreAPIKit/AGENTS.md
- **Why retained:** Described check, not supplied implementation

## 19. Auth middleware boundary
Client middleware attaches authorization and must not emit sensitive headers or bodies to logs.
- **Origin:** CoreAPIKit/AGENTS.md
- **Why retained:** Concrete middleware requirement

## 20. Xcode bridge discovery
The root instructions ask agents to list available Xcode MCP tools instead of hardcoding names. Build/preview depend on an explicit simulator destination.
- **Origin:** Root AGENTS.md; guide p.5
- **Why retained:** Operational verification method

## 21. Test instruction loading
The guide describes testing Codex and Claude context loading, plus an Xcode probe that adds a temporary naming convention before deleting it.
- **Origin:** Guide p.8
- **Why retained:** Repeatable diagnostic idea

## 22. Prompt attack smoke test
The guide proposes an intentional request to store session tokens in UserDefaults; the expected agent behavior is warning/question instead of silently doing so.
- **Origin:** Guide p.8
- **Why retained:** Suggested non-production behavior test

## 23. Path-sensitive instructions
The guide differentiates always-loaded root guidance from subdirectory-specific instructions; CLAUDE-specific file loading occurs as affected files are accessed.
- **Origin:** Guide pp.2,5
- **Why retained:** Scope and file placement

## 24. No repository assumed
The archive is a prospective iPhone project template, not evidence that Xcode build, test, signing, provisioning, or Secure Enclave integration exists.
- **Origin:** Guide p.1; AGENTS.md placeholders
- **Why retained:** Critical status clarification

## 25. Not a user-approved policy
The uploaded AGENTS files are examples sourced from the attachment. No project exists here to bind them, and prior research choices are not treated as current user mandates.
- **Origin:** User context + uploaded templates
- **Why retained:** Interpretation; no auto-installation



---

<!-- Source: 02_overlap_and_disagreements.md -->

# Duplicate analysis and conflicts

## Exact duplicates: strong evidence

1. `Infrastructure/Security/CLAUDE.md` and `CoreAPIKit/CLAUDE.md` both contain just `@AGENTS.md\n` and share the same SHA256. Both paths remain in the unmodified directory because deleting one would affect that directory's setup.
2. The root template text is also reproduced in the uploaded PDF, pp. 10-12. The PDF additionally has explanations, setup steps and 16 references; it is not just another byte-identical copy of the ZIP.
3. The pasted `AGENTS.md` in the conversation matches the template purpose and visible content. The ZIP copy is preserved as the canonical downloadable source; the chat paste is not an independent original file for byte-level comparison.
4. No newly supplied template file is an identical whole-file copy of an earlier Markdown/TXT item in the older research library (SHA/byte comparison). This does **not** mean the prose is semantically unique.

## Previously covered ideas, but newly concretized here

| General subject already in prior research | What the new attachments materially contribute |
|---|---|
| SwiftUI / iOS 26 / Xcode | An actual root AGENTS.md with commands and required placeholders |
| CoreAPI and OpenAPI | Nested CoreAPIKit instructions, generation flags, undocumented status mapping, oasdiff CI check |
| Secure Enclave / Keychain | Nested Security instructions, two specific Keychain error codes, reinstall cleanup and key blob handling |
| Agent tools / skills | CLAUDE import bridge, precedence/discovery guide, path-sensitive subfiles |
| Testing and quality | .swiftlint.yml with 3 custom regex rules and .claude/settings.json for asking before risky edits |

## Matters to preserve as unresolved, not silently 'corrected'

- The PDF says Claude Code 2.1.277 reads AGENTS.md directly; the currently fetched official Claude memory page states the opposite: load CLAUDE.md and import AGENTS.md. These claims are in conflict.
- 'Rules override skills' is an intention written in the sample AGENTS.md, not a verified tool-enforced priority mechanism. Explicit user instructions and product security controls have independent precedence.
- 'Never change SDK, toolchain, layout or architecture' represents example project choices, not decisions imposed on a currently absent/deleted repository.
- The exact .claude/settings.json patterns have been parsed as JSON but not exercised against Claude Code. Permission rules cannot protect against every arbitrary executable.
- No source here proves an Xcode build, a real device test, successful App Store provisioning, or full SwiftLint behavior.

## Search-term overlap with old library (not a novelty metric)

- `AGENTS.md` occurs in **10** distinct older Markdown/TXT documents.
- `CLAUDE.md` occurs in **8** distinct older Markdown/TXT documents.
- `SwiftLint` occurs in **7** distinct older Markdown/TXT documents.
- `Keychain` occurs in **24** distinct older Markdown/TXT documents.
- `Secure Enclave` occurs in **27** distinct older Markdown/TXT documents.
- `OpenAPI` occurs in **18** distinct older Markdown/TXT documents.
- `CoreAPIKit` occurs in **3** distinct older Markdown/TXT documents.
- `SwiftUI` occurs in **34** distinct older Markdown/TXT documents.
- `Xcode` occurs in **35** distinct older Markdown/TXT documents.
- `Swift Testing` occurs in **18** distinct older Markdown/TXT documents.
- `Tailscale` occurs in **22** distinct older Markdown/TXT documents.
- `idempotency` occurs in **14** distinct older Markdown/TXT documents.
- `SwiftData` occurs in **18** distinct older Markdown/TXT documents.



---

<!-- Source: 03_code_and_setup.md -->

# Original code and setup snippets

Files below are printed exactly from the uploaded ZIP. They are **templates**, not executed commands. The PDF discusses how to customize them.

## `AGENTS.md`
SHA256 `76ceae2ee8cb5ef87d41e44de814d1f04408939039641efd24e178538261695f`. Size 6878 bytes.
```markdown
# AGENTS.md — <AppName> (native iPhone app)

<!-- Owner: <name>. Last reviewed: <YYYY-MM-DD>. Keep under ~150 lines. -->
<!-- These rules override any installed skill. A direct instruction from the owner in chat overrides this file. -->

## Project
- Personal native iPhone app in SwiftUI, signed with the owner's Apple Developer account.
- Thin client. The Core service owns orchestration, policy, tasks and durable state.
- Never embed an LLM, provider API keys or agent logic in the app.
- Tabs: Chat, Spaces, Activity. Settings opens as a sheet from a toolbar button. Integrations live inside Settings.
- Arabic (RTL) is the primary language; English is secondary.

## Toolchain (do not change without asking)
- Xcode 27.2, iOS 27.2 SDK, Swift 6.4, Swift 6 language mode.
- Deployment target: iOS 26.0. Never raise it. Gate iOS 27 APIs with `if #available(iOS 27, *)`. No fallbacks below iOS 26.
- Build settings: `SWIFT_DEFAULT_ACTOR_ISOLATION = MainActor`, `SWIFT_APPROACHABLE_CONCURRENCY = YES`.
- iPhone only. Layouts must resize; never assume a fixed screen width.

## Commands
- Schemes: `xcodebuild -list -project <App>.xcodeproj`
- Simulators: `xcrun simctl list devices available`
- Build: `xcodebuild -project <App>.xcodeproj -scheme <App> -destination 'platform=iOS Simulator,id=<UDID>' build`
- Test: same arguments with `test -resultBundlePath <fresh-dir>/Tests.xcresult`
- Lint: `swiftlint lint --strict`
- If a command cannot run, say so. Never claim a check passed without showing its output.

## Layout
- `App/`, `Design/`, `Features/<Feature>/`, `Infrastructure/{CoreAPI,Security,Persistence,Connectivity}/`, `Resources/`, `Tests/`, plus the `CoreAPIKit` target.
- One primary type per file. Folders by feature.

## Architecture
- Feature models are `@MainActor @Observable`, owned by views with `@State`, passed with `@Environment` or `@Bindable`.
- Services sit behind small `Sendable` protocols, injected through initializers or Environment. No singletons.
- `async` does not mean background. Use `@concurrent` for heavy work (large JSON decoding, Arabic text normalization).
- Never silence concurrency diagnostics with `@unchecked Sendable` or `nonisolated(unsafe)`.
- SwiftData stores cache and drafts only; Core is the source of truth. Never pass `@Model` objects across actors; pass `PersistentIdentifier` or DTOs. Background writes go through a `@ModelActor`.

## API contract
- `openapi.yaml` in the `CoreAPIKit` target is a synced copy of the Core contract. Change the contract in Core first, then sync it here.
- The Swift OpenAPI Generator build plugin generates types and client at build time. Never commit generated sources and never hand-write duplicate DTOs.
- Generated types stay inside `CoreAPIKit`. The app talks to the `CoreAPI` protocol; `LiveCoreClient` and `DemoCoreClient` both conform.
- Writes: create one idempotency key per draft, persist it with the draft and reuse it on every retry. `202` means accepted, not done.
- On timeout, query status first; if still unknown, show `OUTCOME_UNKNOWN`. Never resend with a new key.
- Live updates use polling unless the contract declares `text/event-stream`.

## Truth labels
- Every Core-derived screen shows exactly one label: REAL, DEMO or OFFLINE.
- REAL only when Core confirmed the data. Never infer REAL from a local toggle or an optimistic update.
- DEMO data grants no permission and never calls `LiveCoreClient`.
- OFFLINE states are distinct: VPN off, Core not responding, auth rejected.

## Security (stop and ask before changing anything here)
- Session token: Keychain only, `kSecAttrAccessibleWhenUnlockedThisDeviceOnly`, `kSecAttrSynchronizable = false`, accessed through a dedicated `actor`. Never UserDefaults, `@AppStorage`, SwiftData or logs.
- Clear the token on sign-out and on the first launch after a reinstall.
- Approval key: Secure Enclave P-256 with access control `[.privateKeyUsage, .biometryCurrentSet]`. The app view-lock is separate and never signs.
- Approval envelope: fixed, versioned fields defined in `<docs/signing-protocol.md>`. Sign the canonical bytes with `signature(for: Data)`; never hash them yourself and pass the hash as Data.
- Show the server-provided intent that is being signed, never an agent-written summary.
- Never auto-approve, auto-retry an approval or generate a new nonce on retry.
- Logging uses `Logger`. Tokens, payloads and personal data are never logged in clear text.
- Core is reached only through Tailscale Serve (private HTTPS). Never propose Funnel, public ports or plain HTTP.
- Before editing `Infrastructure/Security/`, read `Infrastructure/Security/AGENTS.md`.

## UI
- Strings live in String Catalogs (`.xcstrings`). Use `leading`/`trailing`, never left/right.
- Force LTR for code blocks and identifiers. Do not mirror digits, logos or media.
- Dynamic Type everywhere; no fixed font sizes. Icon-only buttons still have a text label.
- Liquid Glass only on system controls and the navigation layer. No glass on cards, message bubbles, approval text or task rows. Respect Reduce Transparency and Reduce Motion.
- Verify each SF Symbol is available on iOS 26. Never use SF Symbols in the app icon.
- UIKit is allowed only for the scene-delegate privacy cover and the web authentication session bridge.

## Testing
- Swift Testing for logic, contract decoding, state machines and the canonical envelope.
- XCTest/XCUIAutomation for UI flows, permissions, RTL and `performAccessibilityAudit()`.
- Inject fake API, signer and clock. Never sign real proposals in tests.
- Never edit a golden fixture to make a test pass.
- List device-only checks (Secure Enclave, Face ID, Tailscale, voice) instead of claiming them.

## Xcode tools
- If the Xcode MCP server is connected, list its tools first; names change between Xcode versions.
- Use documentation search before adopting an unfamiliar API.
- Render previews on an explicit iPhone destination and inspect the returned image.

## Skills
- UI structure: swiftui-ui-patterns
- Review: swiftui-pro, then swiftui-expert-skill
- Keychain, Face ID, CryptoKit: swift-security-expert
- HIG, glass, typography: axiom-design (or swiftui-liquid-glass)
- SF Symbols: sf-symbols-finder with `--min-platform iOS26`
- App icon: /app-icon-gen, only when the owner asks
- If a skill conflicts with this file, follow this file and report the conflict.

## Ask first
- New dependencies; entitlements, capabilities, signing or provisioning; Info.plist privacy keys; the deployment target.
- Contract changes; anything that touches real Core state, APNs, TestFlight or App Store Connect.
- Before editing `CoreAPIKit/`, read `CoreAPIKit/AGENTS.md`.

## Done means
- Build and relevant tests pass, with command output shown. Lint is clean.
- Affected screens were previewed in light and dark, Arabic RTL and the largest Dynamic Type size.
- Device-only checks are listed as pending.
```

## `CLAUDE.md`
SHA256 `9dcb68734160e140e36eb17bc7137c99863d8c23f6b7a402d8ec0d6998593f13`. Size 115 bytes.
```markdown
@AGENTS.md

## Claude Code
- Use plan mode for security, contract and cross-layer changes, then wait for approval.
```

## `Infrastructure/Security/AGENTS.md`
SHA256 `bacf7be784627b8b2e4f73972191074761939aa9a41e0ac526257e778376f407`. Size 1163 bytes.
```markdown
# Infrastructure/Security — rules

- All `SecItem*` calls happen inside one `actor` (default MainActor isolation is on, so mark it explicitly).
- Session token item: generic password, service `<bundle-id>.session`, account `<account>`, `kSecAttrAccessibleWhenUnlockedThisDeviceOnly`, `kSecAttrSynchronizable = false`.
- `errSecItemNotFound` means no session. `errSecInteractionNotAllowed` means the device is locked: retry after unlock. Never fall back to another store.
- Keychain items survive app deletion. On the first launch after install (flag in UserDefaults), delete stale items.
- Approval key: `SecureEnclave.P256.Signing.PrivateKey` created with `SecAccessControlCreateWithFlags` and `[.privateKeyUsage, .biometryCurrentSet]`.
- Persist only the key's `dataRepresentation` (an encrypted blob) in the Keychain.
- Adding or removing a face or fingerprint invalidates the key. Show re-enrollment with Core; never silently create a new key.
- Signing goes through the `ApprovalSigner` protocol. Previews and unit tests use a fake signer.
- Canonical envelope bytes must match the shared fixtures used by Core. Never update a fixture to make a test pass.
```

## `Infrastructure/Security/CLAUDE.md`
SHA256 `336cc4fbf19beaada7ccf9986414fa91851a8d7a07dfb3ccbe800a69eed0ab49`. Size 11 bytes.
```markdown
@AGENTS.md
```

## `CoreAPIKit/AGENTS.md`
SHA256 `04fa70051614830fcc7a2ce575c6cc3eef270c89baf6e9c044cc31c7b81be26f`. Size 764 bytes.
```markdown
# CoreAPIKit — rules

- `openapi.yaml` here is a copy of the Core contract (OpenAPI 3.1). Edit it in Core, then sync. Never edit it only here.
- `openapi-generator-config.yaml`: `generate: [types, client]`, `accessModifier: internal`.
- Keep swift-openapi-generator, swift-openapi-runtime and swift-openapi-urlsession on the pinned compatible versions in `Package.resolved`.
- Generated `Components.Schemas.*` types never leave this target. Map responses to app DTOs inside `LiveCoreClient`.
- Map every documented response explicitly; `.undocumented(status, _)` becomes `CoreError.undocumented(status)`.
- The client middleware adds the auth header and never logs bodies or sensitive headers.
- Breaking contract changes must pass `oasdiff` in CI before merge.
```

## `CoreAPIKit/CLAUDE.md`
SHA256 `336cc4fbf19beaada7ccf9986414fa91851a8d7a07dfb3ccbe800a69eed0ab49`. Size 11 bytes.
```markdown
@AGENTS.md
```

## `.claude/settings.json`
SHA256 `916d85a48c49ae8053eba38c9b550b5f2630de00d7a3e3c3571d819165be01bb`. Size 245 bytes.
```json
{
  "permissions": {
    "ask": [
      "Edit(/**/*.entitlements)",
      "Edit(/**/Info.plist)",
      "Edit(/**/PrivacyInfo.xcprivacy)",
      "Edit(/CoreAPIKit/**/openapi.yaml)",
      "Edit(/AGENTS.md)",
      "Edit(/CLAUDE.md)"
    ]
  }
}
```

## `.swiftlint.yml`
SHA256 `8d7ac6c4cba64fe320b836107ec8c7b9a2519581d11d28f75c6d24bda5111cb0`. Size 657 bytes.
```yaml
strict: true

custom_rules:
  no_weak_keychain_accessibility:
    name: "Weak Keychain accessibility"
    regex: "kSecAttrAccessible(Always|AfterFirstUnlock)(ThisDeviceOnly)?\\b"
    message: "Use kSecAttrAccessibleWhenUnlockedThisDeviceOnly (see AGENTS.md)."
    severity: error
  no_print:
    name: "print in app code"
    regex: "^[ \\t]*print\\("
    excluded:
      - ".*Tests?\\.swift"
    message: "Use Logger with privacy annotations instead of print."
    severity: error
  no_navigation_view:
    name: "NavigationView"
    regex: "\\bNavigationView\\b"
    match_kinds:
      - identifier
    message: "Use NavigationStack."
    severity: error
```

## Commands described in PDF p. 8 (not run here)
```bash
grep -rn "<[A-Za-z]" AGENTS.md CLAUDE.md */AGENTS.md */*/AGENTS.md
xcodebuild -list -project <App>.xcodeproj
xcrun simctl list devices available
wc -l -c AGENTS.md */AGENTS.md */*/AGENTS.md
codex --ask-for-approval never "Summarize the current instructions."
```

Angle-bracket placeholders require a real Xcode project and scheme; do not paste them literally into a shell expecting a successful build.


---

<!-- Source: 04_source_checks.md -->

# Reference checks and unresolved claims

These 16 links appear in the PDF bibliography (p. 13). A link appearing here is **not** proof its contents were verified.

| # | Source | Check status | URL |
|---:|---|---|---|
| 1 | Codex AGENTS instructions | verified_direct | <https://developers.openai.com/codex/guides/agents-md> |
| 2 | Claude Code memory and AGENTS import | verified_direct | <https://code.claude.com/docs/en/memory> |
| 3 | AGENTS.md official format | verified_direct | <https://agents.md/> |
| 4 | Xcode external agents | title_only_js | <https://developer.apple.com/documentation/xcode/giving-external-agents-access-to-xcode> |
| 5 | Xcode agent extensions | not_verified_individually | <https://developer.apple.com/documentation/xcode/extending-and-customizing-agents> |
| 6 | Hacking with Swift skills for Xcode | not_verified_individually | <https://www.hackingwithswift.com/articles/283/how-to-install-and-use-ai-agent-skills-in-xcode> |
| 7 | SwiftAgents repository | verified_page | <https://github.com/twostraws/swiftagents> |
| 8 | Claude Code permissions | verified_direct | <https://code.claude.com/docs/en/permissions> |
| 9 | SwiftLint repository | verified_direct | <https://github.com/realm/SwiftLint> |
| 10 | Claude Code best practices | verified_direct | <https://code.claude.com/docs/en/best-practices> |
| 11 | SE-0466 default actor isolation | not_verified_individually | <https://github.com/swiftlang/swift-evolution/blob/main/proposals/0466-control-default-actor-isolation.md> |
| 12 | Apple keychain accessibility | title_only_js | <https://developer.apple.com/documentation/security/restricting-keychain-item-accessibility> |
| 13 | Apple biometryCurrentSet | title_only_js | <https://developer.apple.com/documentation/security/secaccesscontrolcreateflags/biometrycurrentset> |
| 14 | Swiftjectivec Xcode agents experience | not_verified_individually | <https://swiftjectivec.com/Agentic-Coding-Codex-Claude-Code-in-Xcode/> |
| 15 | Apple Logger | not_verified_individually | <https://developer.apple.com/documentation/os/generating-log-messages-from-your-code> |
| 16 | Apple HIG SF Symbols | not_verified_individually | <https://developer.apple.com/design/human-interface-guidelines/sf-symbols> |

## Direct corrections/checks

- Codex official AGENTS guidance confirms root-to-CWD discovery, AGENTS.override.md precedence and the 32-KiB default cap. [1]
- Current official Claude documentation says Claude reads CLAUDE.md, **not** AGENTS.md directly, and gives `@AGENTS.md` as the supported bridge. This contradicts part of PDF pp. 1-2. [2]
- Official Claude permissions documentation confirms `allow`, `ask`, `deny` as tool-enforced configuration, while the text memory file itself is advisory context. [2,8]
- SwiftLint official docs confirm regex custom rules, inclusion/exclusion patterns and syntax-kind matching. The supplied patterns were **not tested with the SwiftLint binary**. [9]
- Apple documentation pages [4,12,13] rendered a JavaScript-required shell in this fetch environment; direct API details were not revalidated in this run.
- The source PDF has the full text and comments about uncertain platform behaviors, which have been retained verbatim.

## Original sources and versioned claims

All implementation-specific Xcode/Swift/iOS version claims in the PDF are source assertions unless explicitly listed above as verified. No actual project was built here.


---

<!-- Source: 05_all_guidance_categorized.md -->

# Every directive indexed (no content discarded)

The source text of each bullet is preserved, organized by file and section. This is an **index of source assertions** only.

## AGENTS.md (68 bullet items)

### Project

- (line 7) Personal native iPhone app in SwiftUI, signed with the owner's Apple Developer account.
- (line 8) Thin client. The Core service owns orchestration, policy, tasks and durable state.
- (line 9) Never embed an LLM, provider API keys or agent logic in the app.
- (line 10) Tabs: Chat, Spaces, Activity. Settings opens as a sheet from a toolbar button. Integrations live inside Settings.
- (line 11) Arabic (RTL) is the primary language; English is secondary.
### Toolchain (do not change without asking)

- (line 14) Xcode 27.2, iOS 27.2 SDK, Swift 6.4, Swift 6 language mode.
- (line 15) Deployment target: iOS 26.0. Never raise it. Gate iOS 27 APIs with `if #available(iOS 27, *)`. No fallbacks below iOS 26.
- (line 16) Build settings: `SWIFT_DEFAULT_ACTOR_ISOLATION = MainActor`, `SWIFT_APPROACHABLE_CONCURRENCY = YES`.
- (line 17) iPhone only. Layouts must resize; never assume a fixed screen width.
### Commands

- (line 20) Schemes: `xcodebuild -list -project <App>.xcodeproj`
- (line 21) Simulators: `xcrun simctl list devices available`
- (line 22) Build: `xcodebuild -project <App>.xcodeproj -scheme <App> -destination 'platform=iOS Simulator,id=<UDID>' build`
- (line 23) Test: same arguments with `test -resultBundlePath <fresh-dir>/Tests.xcresult`
- (line 24) Lint: `swiftlint lint --strict`
- (line 25) If a command cannot run, say so. Never claim a check passed without showing its output.
### Layout

- (line 28) `App/`, `Design/`, `Features/<Feature>/`, `Infrastructure/{CoreAPI,Security,Persistence,Connectivity}/`, `Resources/`, `Tests/`, plus the `CoreAPIKit` target.
- (line 29) One primary type per file. Folders by feature.
### Architecture

- (line 32) Feature models are `@MainActor @Observable`, owned by views with `@State`, passed with `@Environment` or `@Bindable`.
- (line 33) Services sit behind small `Sendable` protocols, injected through initializers or Environment. No singletons.
- (line 34) `async` does not mean background. Use `@concurrent` for heavy work (large JSON decoding, Arabic text normalization).
- (line 35) Never silence concurrency diagnostics with `@unchecked Sendable` or `nonisolated(unsafe)`.
- (line 36) SwiftData stores cache and drafts only; Core is the source of truth. Never pass `@Model` objects across actors; pass `PersistentIdentifier` or DTOs. Background writes go through a `@ModelActor`.
### API contract

- (line 39) `openapi.yaml` in the `CoreAPIKit` target is a synced copy of the Core contract. Change the contract in Core first, then sync it here.
- (line 40) The Swift OpenAPI Generator build plugin generates types and client at build time. Never commit generated sources and never hand-write duplicate DTOs.
- (line 41) Generated types stay inside `CoreAPIKit`. The app talks to the `CoreAPI` protocol; `LiveCoreClient` and `DemoCoreClient` both conform.
- (line 42) Writes: create one idempotency key per draft, persist it with the draft and reuse it on every retry. `202` means accepted, not done.
- (line 43) On timeout, query status first; if still unknown, show `OUTCOME_UNKNOWN`. Never resend with a new key.
- (line 44) Live updates use polling unless the contract declares `text/event-stream`.
### Truth labels

- (line 47) Every Core-derived screen shows exactly one label: REAL, DEMO or OFFLINE.
- (line 48) REAL only when Core confirmed the data. Never infer REAL from a local toggle or an optimistic update.
- (line 49) DEMO data grants no permission and never calls `LiveCoreClient`.
- (line 50) OFFLINE states are distinct: VPN off, Core not responding, auth rejected.
### Security (stop and ask before changing anything here)

- (line 53) Session token: Keychain only, `kSecAttrAccessibleWhenUnlockedThisDeviceOnly`, `kSecAttrSynchronizable = false`, accessed through a dedicated `actor`. Never UserDefaults, `@AppStorage`, SwiftData or logs.
- (line 54) Clear the token on sign-out and on the first launch after a reinstall.
- (line 55) Approval key: Secure Enclave P-256 with access control `[.privateKeyUsage, .biometryCurrentSet]`. The app view-lock is separate and never signs.
- (line 56) Approval envelope: fixed, versioned fields defined in `<docs/signing-protocol.md>`. Sign the canonical bytes with `signature(for: Data)`; never hash them yourself and pass the hash as Data.
- (line 57) Show the server-provided intent that is being signed, never an agent-written summary.
- (line 58) Never auto-approve, auto-retry an approval or generate a new nonce on retry.
- (line 59) Logging uses `Logger`. Tokens, payloads and personal data are never logged in clear text.
- (line 60) Core is reached only through Tailscale Serve (private HTTPS). Never propose Funnel, public ports or plain HTTP.
- (line 61) Before editing `Infrastructure/Security/`, read `Infrastructure/Security/AGENTS.md`.
### UI

- (line 64) Strings live in String Catalogs (`.xcstrings`). Use `leading`/`trailing`, never left/right.
- (line 65) Force LTR for code blocks and identifiers. Do not mirror digits, logos or media.
- (line 66) Dynamic Type everywhere; no fixed font sizes. Icon-only buttons still have a text label.
- (line 67) Liquid Glass only on system controls and the navigation layer. No glass on cards, message bubbles, approval text or task rows. Respect Reduce Transparency and Reduce Motion.
- (line 68) Verify each SF Symbol is available on iOS 26. Never use SF Symbols in the app icon.
- (line 69) UIKit is allowed only for the scene-delegate privacy cover and the web authentication session bridge.
### Testing

- (line 72) Swift Testing for logic, contract decoding, state machines and the canonical envelope.
- (line 73) XCTest/XCUIAutomation for UI flows, permissions, RTL and `performAccessibilityAudit()`.
- (line 74) Inject fake API, signer and clock. Never sign real proposals in tests.
- (line 75) Never edit a golden fixture to make a test pass.
- (line 76) List device-only checks (Secure Enclave, Face ID, Tailscale, voice) instead of claiming them.
### Xcode tools

- (line 79) If the Xcode MCP server is connected, list its tools first; names change between Xcode versions.
- (line 80) Use documentation search before adopting an unfamiliar API.
- (line 81) Render previews on an explicit iPhone destination and inspect the returned image.
### Skills

- (line 84) UI structure: swiftui-ui-patterns
- (line 85) Review: swiftui-pro, then swiftui-expert-skill
- (line 86) Keychain, Face ID, CryptoKit: swift-security-expert
- (line 87) HIG, glass, typography: axiom-design (or swiftui-liquid-glass)
- (line 88) SF Symbols: sf-symbols-finder with `--min-platform iOS26`
- (line 89) App icon: /app-icon-gen, only when the owner asks
- (line 90) If a skill conflicts with this file, follow this file and report the conflict.
### Ask first

- (line 93) New dependencies; entitlements, capabilities, signing or provisioning; Info.plist privacy keys; the deployment target.
- (line 94) Contract changes; anything that touches real Core state, APNs, TestFlight or App Store Connect.
- (line 95) Before editing `CoreAPIKit/`, read `CoreAPIKit/AGENTS.md`.
### Done means

- (line 98) Build and relevant tests pass, with command output shown. Lint is clean.
- (line 99) Affected screens were previewed in light and dark, Arabic RTL and the largest Dynamic Type size.
- (line 100) Device-only checks are listed as pending.

## Infrastructure/Security/AGENTS.md (9 bullet items)

### Infrastructure/Security — rules

- (line 3) All `SecItem*` calls happen inside one `actor` (default MainActor isolation is on, so mark it explicitly).
- (line 4) Session token item: generic password, service `<bundle-id>.session`, account `<account>`, `kSecAttrAccessibleWhenUnlockedThisDeviceOnly`, `kSecAttrSynchronizable = false`.
- (line 5) `errSecItemNotFound` means no session. `errSecInteractionNotAllowed` means the device is locked: retry after unlock. Never fall back to another store.
- (line 6) Keychain items survive app deletion. On the first launch after install (flag in UserDefaults), delete stale items.
- (line 7) Approval key: `SecureEnclave.P256.Signing.PrivateKey` created with `SecAccessControlCreateWithFlags` and `[.privateKeyUsage, .biometryCurrentSet]`.
- (line 8) Persist only the key's `dataRepresentation` (an encrypted blob) in the Keychain.
- (line 9) Adding or removing a face or fingerprint invalidates the key. Show re-enrollment with Core; never silently create a new key.
- (line 10) Signing goes through the `ApprovalSigner` protocol. Previews and unit tests use a fake signer.
- (line 11) Canonical envelope bytes must match the shared fixtures used by Core. Never update a fixture to make a test pass.

## CoreAPIKit/AGENTS.md (7 bullet items)

### CoreAPIKit — rules

- (line 3) `openapi.yaml` here is a copy of the Core contract (OpenAPI 3.1). Edit it in Core, then sync. Never edit it only here.
- (line 4) `openapi-generator-config.yaml`: `generate: [types, client]`, `accessModifier: internal`.
- (line 5) Keep swift-openapi-generator, swift-openapi-runtime and swift-openapi-urlsession on the pinned compatible versions in `Package.resolved`.
- (line 6) Generated `Components.Schemas.*` types never leave this target. Map responses to app DTOs inside `LiveCoreClient`.
- (line 7) Map every documented response explicitly; `.undocumented(status, _)` becomes `CoreError.undocumented(status)`.
- (line 8) The client middleware adds the auth header and never logs bodies or sensitive headers.
- (line 9) Breaking contract changes must pass `oasdiff` in CI before merge.