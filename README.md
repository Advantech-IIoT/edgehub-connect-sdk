# EdgeHub Connect SDK

EdgeHub Connect SDK provides a stable C ABI for connecting native applications
and devices to Advantech EdgeHub services. It supports Windows and Linux C
consumers through shared-library runtime packages and static development
packages.

This repository is the official distribution portal for SDK releases,
documentation, and examples. Generated SDK binaries are published as GitHub
Release assets and are not committed to the Git repository.

> **Status:** EdgeHub Connect SDK is currently pre-1.0. Review the release notes
> and migration guidance before updating an existing integration.

## Get the SDK

1. Open [Releases](https://github.com/Advantech-IIoT/edgehub-connect-sdk/releases).
2. Select the package matching the target platform and linkage model.
3. Download `SHA256SUMS.txt` and verify the package digest before use.
4. Start with the bundled headers, examples, and documentation.

Release tags use standard semantic versions:

| Tag | Purpose |
| --- | --- |
| `vX.Y.Z-rc.N` | Release candidate for validation |
| `vX.Y.Z` | Stable release |

Release candidates and their promoted stable release contain the same signed
and checksummed binary assets. Package filenames and embedded product versions
use the stable `X.Y.Z` core version.

## Release Matrix

| Platform | Dynamic runtime | Static package | Support tier |
| --- | --- | --- | --- |
| Windows amd64 MSVC | Signed DLL | Not included | Primary |
| Linux amd64 GNU | Included | Included | Primary |
| Linux arm64 GNU | Included | Included | Primary |
| Linux armhf GNU | Included | Included | Primary |
| Linux armel GNU | Included | Included | Primary |
| Linux i386 GNU | Included | Included | Primary |
| Linux amd64 musl | Not included | Static preview | Preview |
| Linux arm64 musl | Not included | Static preview | Preview |

GNU dynamic packages contain `libedgehub_connect.so`. GNU static and musl
preview packages contain `libedgehub_connect.a`. The Windows runtime contains
the signed `edgehub_connect.dll`.

## Package Contents

Developer packages use the following general layout:

```text
edgehub-connect-sdk/
  bin/ or lib/
    edgehub_connect.dll, libedgehub_connect.so, or libedgehub_connect.a
  include/
    ehc.h
    ehc_dynamic.h
  examples/
    C source examples and shared sample helpers
  docs/
    Package and integration documentation
  manifest.json
```

Examples are packaged for the package's linkage model. Dynamic runtime
examples use the SDK loader interface; static packages provide direct-link
examples. Follow the compile and link instructions at the top of each example.

## Documentation

Each release includes a separate documentation ZIP covering:

- C API reference
- DataConnect migration guidance
- Package layout and integration
- Application provisioning
- File download behavior
- Retry and timeout behavior
- Certificate lifecycle and credential rotation

Package-local documentation and examples match the binaries in that release.

## Integrity and Signing

- Every downloadable release includes `SHA256SUMS.txt`.
- Windows release packages contain an Authenticode-signed DLL.
- Unsigned Windows build outputs are never published as GitHub Release assets.
- Linux release packages are produced by the release pipeline and verified
  before publication.
- Stable releases are promoted from approved release-candidate assets without
  rebuilding, re-signing, or repackaging them.

To inspect the Windows signature after extracting the package:

```powershell
Get-AuthenticodeSignature .\edgehub-connect-sdk\bin\edgehub_connect.dll
```

The signature status must be `Valid`.

## Support

Use this repository's issue tracker for release packaging and documentation
problems. Use the established Advantech support channel for product deployment,
service availability, and account-specific assistance.
