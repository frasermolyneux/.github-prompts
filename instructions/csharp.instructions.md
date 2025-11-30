---
applyTo: '**/*.cs'
---

# C# Coding Guidance

## Structure & Naming
- Keep namespaces hierarchical (e.g., `Company.Area.Feature`) so related APIs and DTOs group naturally.
- Use PascalCase for classes such as `ApiClientBase` or `ResponseEnvelope` and prefix interfaces with `I` (`IApiTokenProvider`).
- Keep method names verb-based, reserve camelCase for parameters/fields, and use ALL_CAPS only for shared constants like `AUTHORIZATION_HEADER`.

## Async & Threading
- Every async member must use `async/await`, end with `Async`, surface `Task`/`Task<T>`, and accept a `CancellationToken` (default to `CancellationToken.None` when optional).
- Avoid `.Result`/`.Wait()`; propagate the `Task` instead and guard shared state through immutability or thread-safe primitives.

## Error Handling & Resilience
- Derive domain exceptions from `ApplicationException` (e.g., `ApiAuthenticationException`, `RequestThrottledException`) and throw them instead of `Exception`.
- Use `ILogger<T>` with severity matched to impact: `LogError` for hard failures, `LogWarning` for degraded flows, `LogInformation` for key checkpoints, `LogDebug` for noisy traces.
- Wrap outbound calls with Polly policies that combine exponential backoff + jitter and optional circuit breakers; short-circuit immediately on non-transient HTTP statuses.
- Return typed envelopes like `ApiResponse<T>` that expose status codes, validation issues, and pagination instead of raw tuples or strings.

## HTTP Client Pattern
- Register typed HTTP clients via `IHttpClientFactory`, hide them behind focused interfaces, and keep helper methods under ~50 lines so reviewers can reason about the flow.
- Normalize authentication (API keys, cached OAuth tokens, Entra ID) in helper methods such as `GetAuthenticationHeaderAsync`; never hand-craft headers per call site.
- Dispose `HttpRequestMessage` and streaming payloads explicitly while letting the factory own `HttpClient` lifetimes.
- Log every request/response with correlation IDs, duration, and retry count while redacting secrets.

## Documentation & Testing
- Document public APIs with triple-slash XML comments that include `<param>`, `<returns>`, and `<exception>` plus a brief usage sentence when behavior is subtle.
- Follow Arrange-Act-Assert using xUnit + Moq; store recurring builders/fakes under `Tests/Builders` (or equivalent) to keep test files lean.
- Favor constructor injection for collaborators (`ILogger<ApiClientBase> logger`, `IApiTokenProvider tokenProvider`) so implementations stay testable.

## Dependencies & Packages
- Prefer `Microsoft.Extensions.Logging` for structured logs, `Polly` for resilience, `RestSharp`/`HttpClient` for transport, and `Newtonsoft.Json` when custom converters are required.
- Only add packages when multiple call sites need them; otherwise invest in local helpers or shared abstractions in your solution-level `Directory.Build.props`.
