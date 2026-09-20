# Cast Audio Receiver — separate artifact staging

This repository separates versioned runtime authentication artifacts from the
[open-source receiver](https://github.com/Allcrafter1/cast-audio-receiver-lab).
It is currently private staging, not a public download service.

No bundle bytes or private keys belong in Git. A versioned Release Asset and
manifest are the proposed delivery unit. The receiver independently pins the
manifest SHA-256; that manifest pins the artifact size and SHA-256. A user may
instead supply their own local bundle. No remote kill switch is intended.

## Provenance and limitations

The staged interoperability material was collected from a purchased AirReceiver
installation on the project owner's Android test device. It contains TLS private
keys/certificates, a device certificate chain and captured authentication
signatures. These are not an identity issued to this open-source project.
The reference app and its APK are not distributed here.

Owning the test device or an app licence does not itself establish permission
to publicly redistribute all material contained in that app. The main project's
GPL licence does not relicense this material. Public distribution requires its
own explicit release decision; private staging is not a legal clearance.

The experimental mechanism can stop working following sender/service changes,
revocation or expiry. Stored date coverage is not a guarantee of future sender
acceptance. Do not use the artifact for any other service or identity purpose.

## Versioning, withdrawal and installation

Assets must be immutable within a version. Changed bytes require a new version
and a newly reviewed manifest pin. Removing an asset prevents future downloads
from this distribution, but cannot revoke already downloaded or mirrored copies.
An old pinned manifest cannot automatically learn a new withdrawal flag.

Acquisition is a one-time installation/update action. Existing local state must
remain usable offline; failed downloads must not replace it. The main project's
`cast-audio-bundle` tool checks the trusted manifest and artifact integrity before
atomic installation with private file permissions. It does not establish rights
to distribute the artifact or prove that a sender will accept it.
