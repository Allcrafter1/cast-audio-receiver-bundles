# Cast Audio Receiver — authentication bundle

This repository hosts the separately versioned authentication bundle used by
[Cast Audio Receiver Lab](https://github.com/Allcrafter1/cast-audio-receiver-lab),
an experimental open-source Google Cast audio receiver for Linux and Home
Assistant.

The bundle is distributed separately so that it can be versioned, replaced or
withdrawn independently of the application's source code and container images.
No bundle data or private keys are stored in this repository's Git history.
Downloads are attached to GitHub Releases.

## Important warning

This is an experimental interoperability mechanism. It is not an official
Google Cast identity, is not affiliated with Google or AirReceiver, and may stop
working at any time because of revocation, protocol changes, sender changes or
certificate expiry.

The current release contains:

- TLS private keys and matching short-lived certificates;
- a device certificate and intermediate certificate chain;
- captured device-authentication signatures for the covered time windows.

Anyone can download and inspect the release assets. Removing a release later
cannot recall copies that have already been downloaded or mirrored.

## Current bundle

Release **2026.09.20** contains 773 distinct, gap-free certificate windows from
2026-09-12 through 2030-12-06 (exclusive). The certificate chain itself expires
later, but neither date range guarantees that a Cast sender will continue to
accept the device identity.

The release contains two assets:

- `bundle-through-2030-12-06.json` — the authentication bundle;
- `cast-bundle-manifest-2026.09.20.json` — version, download URL, exact size and
  SHA-256 digest used by the receiver's verified importer.

The receiver pins the manifest digest through its reviewed release. The manifest
in turn pins the exact bundle size and digest. A failed or mismatching download
is rejected without replacing an existing local bundle.

## Installation and updates

Supported Cast Audio Receiver releases can acquire the selected bundle once
during initial installation. The verified file is then stored locally with
private permissions; normal receiver startup does not depend on this repository
remaining online.

Users may instead supply their own compatible bundle. An explicit local bundle
takes precedence over automatic acquisition. Updates are never silently forced
onto an existing installation.

See the main project's installation and bundle-distribution documentation for
the exact release-specific instructions. Do not paste bundle contents, private
keys, signed media URLs or account credentials into public bug reports.

## Provenance

The material was collected during interoperability research from a legitimately
purchased AirReceiver installation running on the project owner's Android test
device. The proprietary application and its APK are not distributed here. The
bundle is not a device identity issued specifically to this open-source project.

The main project implements its Cast path independently using open-source
components and does not use Google's official Cast SDK. Its GPL licence applies
to the project's own code; it does not relicense this authentication material.

Public distribution is an explicit experimental decision by the project owner
with acknowledged legal, operational and revocation uncertainty. It is not a
claim that Google or the reference-app vendor has authorized redistribution.

## Withdrawal and reporting

A release may be withdrawn if the material is superseded, revoked or should no
longer be distributed. Withdrawal prevents future downloads from this location
but cannot invalidate existing copies.

Report availability, provenance or rights concerns through this repository's
issues without reposting the bundle or any key material. Receiver bugs belong in
the main project repository.
