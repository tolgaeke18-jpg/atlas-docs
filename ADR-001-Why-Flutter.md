# ADR-001 — Why Flutter?

**Status:** Accepted

**Date:** 2026-08-05

**Owner:** Atlas Labs

---

# Context

Atlas is being developed as a cross-platform mobile application targeting both Android and iOS.

The primary goals of the MVP are:

- Fast development
- High UI quality
- Single codebase
- Long-term maintainability
- Native-like performance
- Strong community support

The engineering team must choose a mobile framework that enables rapid delivery without sacrificing scalability.

---

# Decision

Atlas will use **Flutter** as the primary mobile development framework.

Programming language:

Dart

---

# Alternatives Considered

## Native Android + Native iOS

Advantages

- Best platform integration
- Maximum performance

Disadvantages

- Two separate codebases
- Higher development cost
- Slower feature delivery
- Double testing effort

Decision

Rejected.

---

## React Native

Advantages

- JavaScript ecosystem
- Large community

Disadvantages

- More dependency on native bridges
- UI consistency challenges
- Performance limitations for graphics-heavy interfaces

Decision

Rejected.

---

## Flutter

Advantages

- Single codebase
- Excellent UI performance
- Consistent design across platforms
- Strong widget ecosystem
- Excellent developer productivity
- Hot Reload
- Easy animation support
- Native compilation
- Large and active community

Decision

Accepted.

---

# Consequences

Positive

- One engineering team
- Faster releases
- Lower maintenance cost
- Shared business logic
- Consistent UI

Negative

- Team must learn Dart
- Larger application size compared to native apps
- Some platform-specific integrations may require native code

These trade-offs are acceptable.

---

# Architectural Impact

Flutter becomes the foundation for all Atlas mobile products.

Future applications may include:

- Atlas
- Atlas Fleet
- Atlas Business
- Atlas Driver

Shared components can be reused across all products.

---

# Project Structure

```

atlas-mobile/

lib/

features/

core/

shared/

assets/

```

Feature-first architecture will be used.

---

# State Management

Riverpod

Reason

- Compile-time safety
- Excellent scalability
- Strong testing support
- No dependency on BuildContext
- Recommended for large Flutter applications

---

# Routing

GoRouter

Reason

- Official Flutter recommendation
- Deep linking support
- Clean navigation model

---

# Networking

Dio

Reason

- Request interceptors
- Authentication support
- Logging
- Retry mechanisms
- Mature ecosystem

---

# Serialization

Freezed

Json Serializable

Reason

- Immutable models
- Type safety
- Reduced boilerplate

---

# Local Storage

Hive

Reason

- High performance
- Lightweight
- Offline-first architecture

---

# Secure Storage

Flutter Secure Storage

Reason

Sensitive information such as authentication tokens must never be stored in plain text.

---

# Testing Strategy

Every feature should include

- Unit Tests
- Widget Tests
- Integration Tests

Business logic must always be testable independently from UI.

---

# Long-Term Strategy

Flutter will remain the primary mobile technology unless one of the following occurs:

- Flutter is no longer actively maintained.
- Platform restrictions prevent critical functionality.
- A future business decision requires a different architecture.

No migration is planned.

---

# Risks

| Risk | Mitigation |
|------|------------|
| Learning Dart | Internal documentation and coding standards |
| Platform-specific APIs | Platform Channels |
| Flutter breaking changes | Version pinning and CI testing |

---

# Success Criteria

This decision will be considered successful if:

- One codebase supports Android and iOS.
- New features are delivered simultaneously on both platforms.
- UI consistency is maintained.
- Development velocity remains high.

---

# Related Documents

- PRODUCT.md
- ARCHITECTURE.md
- ROADMAP.md

---

# Approval

Status

Accepted

Approved By

Atlas Labs

Version

1.0

---

© Atlas Labs
