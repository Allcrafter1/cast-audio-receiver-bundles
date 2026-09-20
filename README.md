# Cast Audio Receiver — authentication bundle

I use this repository to distribute the authentication bundle for my
[Cast Audio Receiver](https://github.com/Allcrafter1/cast-audio-receiver-lab).
I keep it separate from the source code so I can update or withdraw it without
putting private keys into the main Git history.

The bundle comes from interoperability research with a purchased AirReceiver
installation on my own Android device. Neither AirReceiver nor Google is
affiliated with or endorses this project. The APK itself is not distributed.

## Current release

The `2026.09.20` release contains 773 verified certificate windows covering
2026-09-12 through 2030-12-06, plus a small manifest with the expected download
URL, file size and SHA-256 hash.

Compatible receiver releases download and verify the bundle once during initial
setup, then keep a private local copy. You can also provide your own compatible
bundle, which takes precedence over the automatic download.

## Important

This is experimental. The identity may be revoked and protocol changes or
certificate expiry may break it at any time. Removing a release cannot recall
copies that have already been downloaded or mirrored.

Please do not post bundle contents, private keys, signed media URLs or account
credentials in public issues. Report receiver bugs in the main project.
