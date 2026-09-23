# ObraVera — downloads

This repository distributes the ObraVera desktop application. **It contains
no source code.** Releases only.

Downloads are on the [Releases page](https://github.com/obravera-com/obravera/releases/latest).

---

## What ObraVera is

ObraVera is a tool for **authenticating audio you created**.

When you publish a piece of audio, ObraVera does two things to it:

- It embeds a **watermark** in the audio itself — designed not to be
  noticeable in normal listening, and to survive the file being copied and
  converted between formats.
- It signs a **credential** — a cryptographic record naming you as the
  creator, what the work is, and whether AI was involved in making it.

Later, anyone with the file can check it against that record and see who
published it.
The credential is signed with a key that stays on your own machine; ObraVera
never holds it, and cannot sign anything on your behalf.

The point is not to stop copying. It is to let you show, afterwards and to
someone who does not already trust you, that a particular recording came
from you.

**ObraVera is in a closed pilot.** The application runs without an account
for its offline features; registering a work on the ObraVera registry
requires credentials issued to pilot participants.

---

## Requirements

| | |
|---|---|
| **macOS** | 12 (Monterey) or later. Apple silicon and Intel builds are provided separately. |
| **Windows** | See the note on the Windows kit below. |

Download `ObraVera-arm64.dmg` for Apple silicon (M1 and later), or
`ObraVera-x86_64.dmg` for an Intel Mac. If you are unsure, click the Apple
menu → About This Mac; "Chip" means Apple silicon, "Processor" means Intel.

---

## Verifying a download

Every release is published with a `SHA256SUMS` file, and the macOS disk
images are signed with an Apple Developer ID certificate and notarised by
Apple. You do not have to take our word for either — both can be checked on
your own machine, and it takes about ten seconds.

### 1. Check the file is the one we published

Download `SHA256SUMS` from the same release, put it beside the disk image,
then in Terminal:

```
shasum -a 256 -c SHA256SUMS --ignore-missing
```

You want to see `OK` beside the file you downloaded. Anything else means the
file you have is not the file we published — do not open it.

### 2. Check macOS agrees the signature is ours

```
codesign --verify --deep --strict --verbose=2 ObraVera-arm64.dmg
```

No output beyond `valid on disk` and `satisfies its Designated Requirement`
means the signature is intact.

To see who signed it:

```
codesign --display --verbose=4 ObraVera-arm64.dmg 2>&1 | grep Authority
```

The first authority should read exactly:

```
Authority=Developer ID Application: BRADY IAN RIDGWAY (X5937R588J)
```

followed by Apple's intermediate and root certificates. The name is in
capitals because that is how it appears on the certificate — if you see it
written any other way, the file is not one of ours. `X5937R588J` is the Apple
Developer Team ID; it is public, and it is embedded in every build we sign,
so you can check it against any release.

### 3. Check Apple notarised it

```
xcrun stapler validate ObraVera-arm64.dmg
spctl --assess --type open --context context:primary-signature -v ObraVera-arm64.dmg
```

Both commands should succeed, and `spctl` should print `accepted`. Together
they mean Apple has seen this exact build, and that your Mac can confirm it
without going online — the notarisation ticket travels inside the file
rather than being looked up.

If any of these three checks fails, please do not install the application,
and tell us (see below).

---

## The Windows kit

The Windows deliverable is currently distributed as a **pilot kit** — a
folder of scripts and dependencies rather than an installer, and **it is not
code-signed**. Windows SmartScreen will warn about it, correctly: an unsigned
download is one your computer has no way to attribute to anyone.

We would rather say so than have you click through a warning without knowing
why it is there. Verify the checksum as above, and treat the kit as
pilot-only software. A signed Windows installer is planned and will replace
the kit; until it exists, the macOS builds are the ones with a verifiable
chain back to a named developer.

---

## Reporting a problem

- **A failed verification**, an unexpected signature, or a download that does
  not match its checksum: please report this before anything else.
- **Bugs and questions** about the application itself: contact the address
  you were given when you joined the pilot.

The application's source code is not public.

---

## About

ObraVera is made by Brady Ridgway. More at [obravera.com](https://obravera.com).

Releases here are published from tagged, tested builds. Each release records
the source revision it was built from in its release notes.
